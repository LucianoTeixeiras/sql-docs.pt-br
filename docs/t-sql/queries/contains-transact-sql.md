---
title: "CONTÉM (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTAINS_TSQL
- CONTAINS
dev_langs:
- TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- CONTAINS predicate (Transact-SQL)
- conditions [SQL Server], CONTAINS
- fuzzy (less precise) word or phrase search [full-text search]
- word weighting values [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- LANGUAGE option
- word inflectionally generated from another [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- word near another word search [full-text search]
- full-text search [SQL Server], searching on a property
- proximity searches [full-text search]
- less precise (fuzzy) searches [full-text search]
- property searching [SQL Server], searching on a property
- inflectional forms [full-text search]
- prefix searches [full-text search]
ms.assetid: 996c72fc-b1ab-4c96-bd12-946be9c18f84
caps.latest.revision: 117
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 67d85ab09ac28beca984372e3df2bd6a1ca0bfa3
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="contains-transact-sql"></a>CONTAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Procura correspondências precisas ou difusas (menos precisas) para palavras e frases únicas, palavras em uma certa distância entre si ou correspondências ponderadas no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. CONTAINS é um predicado usado no [cláusula WHERE](../../t-sql/queries/where-transact-sql.md) de um [!INCLUDE[tsql](../../includes/tsql-md.md)] instrução SELECT para executar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pesquisa de texto completo no texto completo indexado colunas que contêm tipos de dados com base em caractere.  
  
 CONTAINS pode pesquisar:  
  
-   Uma palavra ou frase.  
  
-   O prefixo de uma palavra ou frase.  
  
-   Uma palavra próxima a outra.  
  
-   Uma palavra gerada a partir de outra por flexão (por exemplo, a palavra guia é uma raiz flexional de guiar, guiou, guiando e guiado).  
  
-   Uma palavra que é sinônima de outra usando um dicionário de sinônimos (por exemplo, a palavra "metal" pode ter sinônimos, como "alumínio" e "aço").  
  
 Para obter informações sobre os formulários de pesquisas de texto completo que são suportados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consulte [consulta com pesquisa de texto completo](../../relational-databases/search/query-with-full-text-search.md).  
 
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CONTAINS (   
     {   
        column_name | ( column_list )   
      | *   
      | PROPERTY ( { column_name }, 'property_name' )    
     }   
     , '<contains_search_condition>'  
     [ , LANGUAGE language_term ]  
   )   
  
<contains_search_condition> ::=   
  {   
      <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    | <weighted_term>   
    }   
  |   
    { ( <contains_search_condition> )   
        [ { <AND> | <AND NOT> | <OR> } ]   
        <contains_search_condition> [ ...n ]   
  }   
<simple_term> ::=   
     { word | "phrase" }  
  
<prefix term> ::=   
  { "word*" | "phrase*" }  
  
<generation_term> ::=   
  FORMSOF ( { INFLECTIONAL | THESAURUS } , <simple_term> [ ,...n ] )   
  
<generic_proximity_term> ::=   
  { <simple_term> | <prefix_term> } { { { NEAR | ~ }   
     { <simple_term> | <prefix_term> } } [ ...n ] }  
  
<custom_proximity_term> ::=   
  NEAR (   
     {  
        { <simple_term> | <prefix_term> } [ ,…n ]  
     |  
        ( { <simple_term> | <prefix_term> } [ ,…n ] )   
      [, <maximum_distance> [, <match_order> ] ]  
     }  
       )   
  
      <maximum_distance> ::= { integer | MAX }  
      <match_order> ::= { TRUE | FALSE }   
  
<weighted_term> ::=   
  ISABOUT   
   ( {   
        {   
          <simple_term>   
        | <prefix_term>   
        | <generation_term>   
        | <proximity_term>   
        }   
      [ WEIGHT ( weight_value ) ]   
      } [ ,...n ]   
   )   
  
<AND> ::=   
  { AND | & }  
  
<AND NOT> ::=   
  { AND NOT | &! }  
  
<OR> ::=   
  { OR | | }  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *nome da coluna*  
 É o nome de uma coluna indexada de texto completo da tabela especificada na cláusula FROM. As colunas podem ser do tipo **char**, **varchar**, **nchar**, **nvarchar**, **texto**, **ntext**, **imagem**, **xml**, **varbinary**, ou **varbinary (max)**.  
  
 *column_list*  
 Especifica duas ou mais colunas, separadas por vírgulas. *column_list* devem ser colocados entre parênteses. A menos que *language_term* for especificado, o idioma de todas as colunas de *column_list* devem ser iguais.  
  
 \*  
 Especifica que a consulta procura todas as colunas indexadas de texto completo na tabela especificada na cláusula FROM para a condição de pesquisa especificados. As colunas na cláusula CONTAINS devem se originar de uma única tabela que tenha um índice de texto completo. A menos que *language_term* for especificado, o idioma de todas as colunas da tabela deve ser o mesmo.  
  
 PROPRIEDADE ( *column_name* , '*property_name*')  
**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Especifica uma propriedade de documento na qual procurar o critério de pesquisa especificado.  
  
> [!IMPORTANT]  
>  Para a consulta retornar linhas, *property_name* deve ser especificado na propriedade de pesquisa, lista de índice de texto completo e o índice de texto completo deve conter entradas específicas de propriedade de *property_name*. Para obter mais informações, veja [Pesquisar propriedades de documento com listas de propriedades de pesquisa](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 IDIOMA *language_term*  
 É o idioma a ser usado para separação de palavras, lematização, expansões do dicionário de sinônimos e substituições e palavras de ruído (ou [palavra irrelevante](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) remoção como parte da consulta. Esse parâmetro é opcional.  
  
 Se os documentos de idiomas diferentes forem armazenados juntos como BLOBs (objetos binários grandes) em uma única coluna, o LCID (identificador de localidade) de um determinado documento determinará qual idioma usar para indexar seu conteúdo. Ao consultar uma coluna desse tipo, especificando o idioma *language_term* pode aumentar a probabilidade de uma boa correspondência.  
  
 *language_term* pode ser especificado como uma cadeia de caracteres, inteiro ou valor hexadecimal que corresponda ao LCID de um idioma. Se *language_term* for especificado, o idioma que ele representa é aplicado a todos os elementos da condição de pesquisa. Se nenhum valor for especificado, o idioma de texto completo da coluna será usado.  
  
 Quando especificado como uma cadeia de caracteres, *language_term* corresponde do **alias** valor de coluna no [sys. syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) exibição de compatibilidade. A cadeia de caracteres deve ser colocada entre aspas, como em '*language_term*'. Quando especificado como um inteiro, *language_term* é o LCID real que identifica o idioma. Quando especificado como um valor hexadecimal, *language_term* é 0x seguido pelo valor hexadecimal do LCID. O valor hexadecimal não deve exceder oito dígitos, inclusive zeros à esquerda.  
  
 Se o valor está no formato DBCS (conjunto) de caracteres de byte duplo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] converterá em Unicode.  
  
 Se o idioma especificado não for válido ou se não houver nenhum recurso instalado que corresponda ao idioma, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retornará um erro. Para usar os recursos de idioma neutro, especifique 0x0 como *language_term*.  
  
 \<*contains_search_condition*>  
 Especifica o texto a ser pesquisado em *column_name* e as condições para uma correspondência.  
  
*\<contains_search_condition >* é **nvarchar**. Uma conversão implícita acontece quando outro tipo de dados de caractere é usado como entrada. No exemplo a seguir, a variável `@SearchWord`, que está definida como `varchar(30)`, causa uma conversão implícita no predicado `CONTAINS`.
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Como "detecção de parâmetro" não funciona em conversão, use **nvarchar** para melhorar o desempenho. No exemplo, declare `@SearchWord` como `nvarchar(30)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Você também pode usar a dica de consulta OPTIMIZE FOR para casos em que é gerado um plano não ideal.  
  
 *Word*  
 É uma cadeia de caracteres sem espaços ou pontuação.  
  
 *frase*  
 É uma ou mais palavras com espaços entre cada uma.  
  
> [!NOTE]  
>  Alguns idiomas, como aqueles escritos em algumas regiões da Ásia, podem ter frases que consistem em uma ou mais palavras sem espaços entre elas.  
  
\<simple_term >  
Especifica uma correspondência para uma palavra ou frase exata. Exemplos de termos simples válidos são "blue berry", "blueberry" e "Microsoft SQL Server." As frases devem estar entre aspas duplas (""). Palavras em uma frase devem aparecer na mesma ordem conforme especificado na  *\<contains_search_condition >* que aparecem na coluna de banco de dados. A pesquisa de caracteres na palavra ou frase não diferencia maiúsculas e minúsculas. As palavras de ruído (ou [palavras irrelevantes](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) (como um e, ou o) em colunas indexadas de texto completo não são armazenados no índice de texto completo. Se uma palavra de ruído for usada em uma pesquisa de uma palavra única, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retornará uma mensagem de erro indicando que a consulta contém apenas palavras de ruído. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclui uma lista padrão de palavras de ruído no diretório \Mssql\Binn\FTERef de cada instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 A pontuação é ignorada. Portanto, `CONTAINS(testing, "computer failure")` corresponde a uma linha com o valor: "Onde está meu computador? A falha ao localizá-lo pode ser dispendiosa." Para obter mais informações sobre o comportamento do separador de palavras, consulte [configurar e gerenciar separadores de palavras e lematizadores para pesquisa](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
 \<prefix_term >  
 Especifica uma correspondência de palavras ou frases que começam com o texto especificado. Coloque um termo de prefixo entre aspas duplas ("") e adicione um asterisco (\*) antes de fechar aspas, para que todo texto que comece com o termo simple especificado antes do asterisco for correspondido. A cláusula deve ser especificada deste modo: `CONTAINS (column, '"text*"')`. O asterisco corresponde a zero, um ou mais caracteres (da palavra de raiz ou termo na palavra ou frase). Se o texto e o asterisco não estiverem delimitados por aspas duplas e o predicado for `CONTAINS (column, 'text*')`, a pesquisa de texto completo considerará o asterisco como um caractere e pesquisará uma correspondência exata para `text*`. O mecanismo de texto completo não localizará palavras com asterisco (\*) caractere porque os separadores de palavras em geral, ignoram tais caracteres.  
  
 Quando  *\<prefix_term >* é uma frase, cada palavra contida na frase é considerada um prefixo separado. Portanto, uma consulta especificando um termo de prefixo "vinho inter*" corresponde a qualquer linha com o texto "vinho interno", "vinho internacional" e assim por diante.  
  
 \<generation_term >  
 Especifica uma correspondência de palavras quando os termos simples incluídos tiverem variáveis da palavra original a ser pesquisada.  
  
 INFLEXIONAL  
 Especifica que o lematizador dependente de idioma será usado no termo simples especificado. O comportamento do lematizador é definido com base em regras lexicais de cada idioma específico. O idioma neutro não tem um lematizador associado. O idioma das colunas que estão sendo consultadas é usado para fazer referência ao lematizador desejado. Se *language_term* for especificado, o lematizador correspondente para que o idioma é usado.  
  
 Um determinado  *\<simple_term >* dentro de um  *\<generation_term >* não corresponderá a substantivos e verbos.  
  
 THESAURUS  
 Especifica que será usada a enciclopédia correspondente ao idioma de texto completo da coluna ou o idioma especificado na consulta. O mais longo padrão ou padrões do  *\<simple_term >* são comparados com o dicionário de sinônimos e termos adicionais são gerados para expandir ou substituir o padrão original. Se não for encontrada uma correspondência para todo ou parte do  *\<simple_term >*, a parte não correspondente é tratada como um *simple_term*. Para obter mais informações sobre o dicionário de sinônimos de pesquisa de texto completo, consulte [configurar e gerenciar arquivos de dicionário de sinônimos para pesquisa de texto completo](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
 \<generic_proximity_term >  
 Especifica uma correspondência de palavras ou frases que devem estar no documento que está sendo pesquisado.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Recomendamos que você use \<custom_proximity_term >.  
  
 NEAR | ~  
 Indica que a palavra ou frase em cada lado do operador NEAR ou ~ deve ocorrer em um documento para uma correspondência a ser retornada. Você deve especificar dois termos de pesquisa. Um termo de pesquisa fornecido pode ser uma única palavra ou frase que é delimitada por aspas duplas ("*frase*").  
  
 Várias condições de proximidade podem ser encadeadas, como em `a NEAR b NEAR c` ou `a ~ b ~ c`. Os termos de proximidade encadeados devem estar todos no documento para que uma correspondência seja retornada.  
  
 Por exemplo, `CONTAINS(*column_name*, 'fox NEAR chicken')` e `CONTAINSTABLE(*table_name*, *column_name*, 'fox ~ chicken')` retornam todos os documentos na coluna especificada que contêm "raposa" e "galinha". Além disso, CONTAINSTABLE retorna uma classificação para cada documento baseado na proximidade de "raposa" e "galinha". Por exemplo, se um documento contiver a oração, "A raposa comeu a galinha", sua posição será alta porque as condições são mais próximas uma da outra do que em outros documentos.  
  
 Para obter mais informações sobre termos de proximidade genérica, consulte [procurar palavras perto de outra palavra com NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<custom_proximity_term >  
**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
 Especifica uma correspondência de palavras ou frases e, opcionalmente, a distância máxima permitida entre termos de pesquisa. Você também pode especificar que os termos de pesquisa devem ser encontrados na ordem exata em que você especificar (\<match_order >).  
  
 Um termo de pesquisa fornecido pode ser uma única palavra ou frase que é delimitada por aspas duplas ("*frase*"). Cada termo especificado deve estar no documento para que uma correspondência seja retornada. Você deve especificar pelo menos dois termos de pesquisa. O número máximo de termos de pesquisa são 64.  
  
 Por padrão, a condição de proximidade personalizada retorna qualquer linha que contém os termos especificados independentemente da distância interveniente e independentemente da ordem deles. Por exemplo, para corresponder à consulta seguinte, um documento precisaria conter `term1` e "`term3 term4`" em qualquer lugar, em qualquer ordem, simplesmente:  
  
```  
CONTAINS(column_name, 'NEAR(term1,"term3 term4")')  
```  
  
 Os parâmetros opcionais são os seguintes:  
  
 \<maximum_distance >  
 Especifica a distância máxima permitida entre os termos de pesquisa no início e no término de uma cadeia de caracteres para que essa cadeia se qualifique como uma correspondência.  
  
 *inteiro*  
 Especifica um inteiro positivo de 0 para 4294967295. Este valor controla quantos termos não relacionados a pesquisa podem ocorrer entre os primeiro e último termos de pesquisa, excluindo qualquer termo de pesquisa especificado adicional.  
  
 Por exemplo, a consulta a seguir procura `AA` e `BB`, em qualquer ordem, dentro de uma distância máxima de cinco.  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB),5)')  
```  
  
 A cadeia de caracteres `AA one two three four five BB` seria uma correspondência. No exemplo a seguir, a consulta especifica três termos de pesquisa, `AA`, `BB`, e `CC` em uma distância máxima de cinco:  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB,CC),5)')  
```  
  
 Essa consulta corresponderia à cadeia de caracteres a seguir, na qual a distância total é cinco:  
  
 `BB   one two   CC   three four five A  A`  
  
 Observe que interna pesquisa termo, `CC`, não é contado.  
  
 **MÁX.**  
 Retorna qualquer linha que contém as condições especificadas independentemente da distância entre eles. Esse é o padrão.  
  
 \<match_order >  
 Especifica se as condições devem ocorrer na ordem especificada a ser retornada por uma consulta de pesquisa. Para especificar \<match_order >, você também deve especificar \<maximum_distance >.  
  
 \<match_order > leva um dos seguintes valores:  
  
 **TRUE**  
 Impõe a ordem especificada nos termos. Por exemplo, `NEAR(A,B)` só corresponderia a `A … B`.  
  
 **FALSE**  
 Ignora a ordem especificada. Por exemplo, `NEAR(A,B)` corresponderia a `A … B` e `B … A`.  
  
 Esse é o padrão.  
  
 Por exemplo, a condição de proximidade a seguir pesquisa as palavras "`Monday`"", `Tuesday`" e "`Wednesday`" na ordem especificada independentemente da distância entre eles:  
  
```  
CONTAINS(column_name, 'NEAR ((Monday, Tuesday, Wednesday), MAX, TRUE)')  
```  
  
 Para obter mais informações sobre como usar condições de proximidade personalizadas, consulte [procurar palavras perto de outra palavra com NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<weighted_term >  
 Especifica que as linhas correspondentes (retornadas pela consulta) correspondem a uma lista de palavras e frases, sendo que cada uma, opcionalmente, recebe um valor de importância.  
  
 ISABOUT  
 Especifica o  *\<weighted_term >* palavra-chave.  
  
 Peso (*weight_value*)  
 Especifica um valor de importância que é um número de 0,0 a 1,0. Cada componente no  *\<weighted_term >* pode incluir um *weight_value*. *weight_value* é uma maneira de alterar como as várias partes de uma consulta afetam o valor de classificação atribuído a cada linha que corresponde à consulta. WEIGHT não afeta os resultados das consultas CONTAINS, mas impacta a classificação em [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) consultas.  
  
> [!NOTE]  
>  O separador decimal é sempre um ponto, independentemente da localidade do sistema operacional.  
  
 { AND | & } | { AND NOT | &! } | { OR | | }  
 Especifica uma operação lógica entre dois critérios de pesquisa CONTAINS.  
  
 {E | &}  
 Indica que os dois critérios de pesquisa CONTAINS devem ser atendidos para haver uma correspondência. O símbolo E comercial (&) pode ser usado em vez da palavra-chave AND para representar o operador AND.  
  
 {E NÃO | &! }  
 Indica que o segundo critério de pesquisa não deve estar presente para haver uma correspondência. O símbolo E comercial seguido pelo símbolo de ponto de exclamação (&!) pode ser usado em vez da palavra-chave AND NOT para representar o operador AND NOT.  
  
 {OU | |}  
 Indica que qualquer um dos dois critérios de pesquisa CONTAINS deve ser atendido para haver uma correspondência. O símbolo de barra vertical (|) pode ser usado em vez da palavra-chave OR para representar o operador OR.  
  
 Quando  *\<contains_search_condition >* contém grupos entre parênteses, esses entre parênteses grupos são avaliados primeiro. Depois de avaliar grupos entre parênteses, essas regras se aplicam ao usar estes operadores lógicos com os critérios de pesquisa CONTAINS:  
  
-   NOT é aplicado antes de AND.  
  
-   NOT só pode ocorrer depois de AND, como em AND NOT. O operador OR NOT não é permitido. NOT não pode ser especificado antes do primeiro termo. Por exemplo, `CONTAINS (mycolumn, 'NOT "phrase_to_search_for" ' )` não é válido.  
  
-   AND é aplicado antes de OR.  
  
-   Operadores boolianos do mesmo tipo (AND, OR) são associativos e, portanto, podem ser aplicados em qualquer ordem.  
  
 *n*  
 É um espaço reservado que indica que várias condições e termos de pesquisa CONTAINS podem ser especificados dentro dele.  
  
## <a name="general-remarks"></a>Comentários gerais  
 As funções e os predicados de texto completo trabalham em uma única tabela, que está implícita no predicado FROM. Para pesquisar em várias tabelas, use uma tabela unida na cláusula FROM para pesquisar em um conjunto de resultados que é o produto de duas ou mais tabelas.  
  
 Predicados de texto completo não são permitidos no [cláusula OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) quando o nível de compatibilidade do banco de dados é definido como 100.  
  
## <a name="querying-remote-servers"></a>Consultando servidores remotos  
 Você pode usar um nome de quatro partes em CONTAINS ou [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) predicado de consulta de texto completo indexado colunas das tabelas de destino em um servidor vinculado. Para preparar um servidor remoto para receber consultas de texto completo, crie um índice de texto completo nas tabelas e colunas de destino no servidor remoto e, em seguida, adicione o servidor remoto como um servidor vinculado.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Comparação de LIKE à pesquisa de texto completo  
 Ao contrário da pesquisa de texto completo, o predicado [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] funciona apenas com padrões de caracteres. Além disso, não é possível usar o predicado LIKE para consultar dados binários formatados. Além disso, uma consulta LIKE feita em uma grande quantidade de dados de texto não estruturados é bem mais lenta do que uma consulta de texto completo equivalente feita nos mesmos dados. Uma consulta LIKE executada em milhões de linhas de dados pode levar muitos minutos para retornar, enquanto uma consulta de texto completo pode demorar apenas alguns segundos ou menos para ser executada nos mesmos dados, dependendo do número de linhas retornadas e seu tamanho. Outra consideração é que LIKE executa apenas um exame de padrão simples de uma tabela inteira. Uma consulta de texto completo, em contrapartida, reconhece idiomas, aplicando transformações específicas a índice e hora de consulta, como filtrar palavras irrelevantes e fazer expansões flexivas e de dicionário de sinônimos. Essas transformações ajudam consultas de texto completo a melhorar a recuperação delas e a sua posição final dos resultados.  
  
## <a name="querying-multiple-columns-full-text-search"></a>Consultando várias colunas (Pesquisa de Texto Completo)  
 Você pode consultar várias colunas especificando uma lista de colunas para pesquisar. As colunas devem ser da mesma tabela.  
  
 Por exemplo, a consulta a seguir contém o termo de pesquisa `Red` no `Name` e `Color` colunas do `Production.Product` tabela do [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] banco de dados de exemplo.  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Name, Color   
FROM Production.Product  
WHERE CONTAINS((Name, Color), 'Red');  
```  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-contains-with-simpleterm"></a>A. Usando CONTAINS com \<simple_term >  
 O exemplo a seguir localiza todos os produtos com um preço de `$80.99` contendo a palavra `Mountain`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain');  
GO  
```  
  
### <a name="b-using-contains-and-phrase-with-simpleterm"></a>B. Usando CONTAINS e frase com \<simple_term >  
 O exemplo a seguir retorna todos os produtos contendo a expressão `Mountain` ou `Road`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' Mountain OR Road ')  
GO  
```  
  
### <a name="c-using-contains-with-prefixterm"></a>C. Usando CONTAINS com \<prefix_term >  
 O exemplo a seguir retorna todos os nomes de produtos com pelo menos uma palavra que comece com a cadeia de prefixos na coluna `Name`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' "Chain*" ');  
GO  
```  
  
### <a name="d-using-contains-and-or-with-prefixterm"></a>D. Usando CONTAINS e or com \<prefix_term >  
 O exemplo a seguir retorna todas as descrições de categoria contendo cadeias de caracteres com prefixos de `chain` ou `full`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, '"chain*" OR "full*"');  
GO  
```  
  
### <a name="e-using-contains-with-proximityterm"></a>E. Usando CONTAINS com \<proximity_term >  
  
**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 O exemplo a seguir pesquisa o `Production.ProductReview` tabela para todos os comentários que contêm a palavra `bike` em 10 termos da palavra "`control`" e na ordem especificada (ou seja, onde "`bike`"precede"`control`").  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments , 'NEAR((bike,control), 10, TRUE)');  
GO  
```  
  
### <a name="f-using-contains-with-generationterm"></a>F. Usando CONTAINS com \<generation_term >  
 O exemplo a seguir pesquisa todos os produtos com as palavras da forma `ride`: riding, ridden e assim por diante.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, ' FORMSOF (INFLECTIONAL, ride) ');  
GO  
```  
  
### <a name="g-using-contains-with-weightedterm"></a>G. Usando CONTAINS com \<weighted_term >  
 O exemplo a seguir pesquisa todos os nomes de produto que contêm as palavras `performance`, `comfortable`, ou `smooth`, e diferentes pesos são dados a cada uma.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, 'ISABOUT (performance weight (.8),   
comfortable weight (.4), smooth weight (.2) )' );  
GO  
```  
  
### <a name="h-using-contains-with-variables"></a>H. Usando CONTAINS com variáveis  
 O exemplo a seguir usa uma variável em vez de um termo de pesquisa específico.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'Performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
GO  
```  
  
### <a name="i-using-contains-with-a-logical-operator-and"></a>I. Usando CONTAINS com um operador lógico (AND)  
 O exemplo a seguir usa a tabela ProductDescription do banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . A consulta usa o predicado CONTAINS para procurar descrições nas quais a ID de descrição não é igual a 5 e a descrição contém as palavras `Aluminum` e a palavra `spindle`. O critério de pesquisa usa o operador booliano AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'Aluminum AND spindle');  
GO  
```  
  
### <a name="j-using-contains-to-verify-a-row-insertion"></a>J. Usando CONTAINS para verificar uma inserção de linha  
 O exemplo a seguir usa CONTAINS dentro de uma subconsulta SELECT. Usando o banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], a consulta obtém o valor de todos os comentários na tabela ProductReview de um ciclo específico. O critério de pesquisa usa o operador booliano AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.ProductReview   
  (ProductID, ReviewerName, EmailAddress, Rating, Comments)   
VALUES  
  (780, 'John Smith', 'john@fourthcoffee.com', 5,   
'The Mountain-200 Silver from AdventureWorks2008 Cycles meets and exceeds expectations. I enjoyed the smooth ride down the roads of Redmond');  
  
-- Given the full-text catalog for these tables is Adv_ft_ctlg,   
-- with change_tracking on so that the full-text indexes are updated automatically.  
WAITFOR DELAY '00:00:30';     
-- Wait 30 seconds to make sure that the full-text index gets updated.  
  
SELECT r.Comments, p.Name  
FROM Production.ProductReview AS r  
JOIN Production.Product AS p   
    ON r.ProductID = p.ProductID  
    AND r.ProductID = (SELECT ProductID  
FROM Production.ProductReview  
WHERE CONTAINS (Comments,   
    ' AdventureWorks2008 AND   
    Redmond AND   
    "Mountain-200 Silver" '));  
GO  
```  
  
### <a name="k-querying-on-a-document-property"></a>K. Consultando em uma propriedade de documento  
  
**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 A consulta a seguir realiza pesquisa em uma propriedade indexada, `Title`, na coluna `Document` da tabela `Production.Document`. A consulta retorna apenas documentos cuja propriedade `Title` contém a cadeia de caracteres `Maintenance` ou `Repair`.  
  
> [!NOTE]  
>  Para que uma pesquisa de propriedade retorne linhas, o filtro ou filtros que analisam a coluna durante a indexação devem extrair a propriedade especificada. Além disso, o índice de texto completo da tabela especificada deve ter sido configurado para incluir a propriedade. Para obter mais informações, veja [Pesquisar propriedades de documento com listas de propriedades de pesquisa](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Document 
FROM Production.Document  
WHERE CONTAINS(PROPERTY(Document,'Title'), 'Maintenance OR Repair');  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Iniciar a pesquisa de texto completo](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Criar e gerenciar catálogos de texto completo](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CRIAR o catálogo de texto completo &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Criar e gerenciar índices de texto completo](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Consulta com pesquisa de texto completo](../../relational-databases/search/query-with-full-text-search.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT &#40;Transact-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Consulta com pesquisa de texto completo](../../relational-databases/search/query-with-full-text-search.md)   
 [Pesquisa de Texto Completo](../../relational-databases/search/full-text-search.md)   
 [Criar consultas de pesquisa de texto completo &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [ONDE &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [Pesquisar propriedades de documento com listas de propriedades de pesquisa](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
