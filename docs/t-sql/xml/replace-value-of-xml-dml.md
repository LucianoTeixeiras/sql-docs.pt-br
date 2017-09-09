---
title: Substituir o valor de (XML DML) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- update keyword
- replacement values [XML DML]
- updating node values
- replace value of XML DML statement
ms.assetid: c310f6df-7adf-493b-b56b-8e3143b13ae7
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7b559d81e2cca495885f740092ac182a4554a012
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="replace-value-of-xml-dml"></a>substituir o valor de (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Atualiza o valor de um nó no documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
replace value of Expression1   
with Expression2  
```  
  
## <a name="arguments"></a>Argumentos  
 *Expression1*  
 Identifica um nó cujo valor será atualizado. Deve identificar apenas um único nó. Ou seja, *Expression1* deve ser um singleton estático. Se o XML for digitado, o tipo do nó deverá ser um tipo simples. Se forem selecionados vários nós, um erro será gerado. Se *Expression1* retorna uma sequência vazia, nenhuma substituição de valor ocorrerá e nenhum erro será retornado. *Expression1* deve retornar um único elemento que simplesmente digitou conteúdo (lista ou tipos atômicos), um nó de texto ou um nó de atributo. *Expression1* não pode ser um tipo de união, um tipo complexo, uma instrução de processamento, um nó de documento ou um nó de comentário. Se for, um erro será retornado.  
  
 *Expression2*  
 Identifica o novo valor do nó. Isso pode ser uma expressão que retorna um nó digitado simples, porque **Data ()** será usado implicitamente. Se o valor é uma lista de valores, o **atualizar** instrução substituirá o valor antigo com a lista. Modificar uma instância XML digitada, *Expression2* devem ser do mesmo tipo ou um subtipo de *expressão*1. Caso contrário, um erro é retornado. Modificar uma instância XML não digitada, *Expression2* deve ser uma expressão que pode ser atomizada. Caso contrário, um erro é retornado.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir do **substituir o valor de** instrução XML DML ilustra como atualizar nós em um documento XML.  
  
### <a name="a-replacing-values-in-an-xml-instance"></a>A. Substituindo valores em uma instância XML  
 No exemplo a seguir, uma instância de documento é atribuída primeiro a uma variável do **xml** tipo. Em seguida, **substituir o valor de** instruções XML DML atualizam os valores no documento.  
  
```  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Manufacturing steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>';  
SELECT @myDoc;  
  
-- update text in the first manufacturing step  
SET @myDoc.modify('  
  replace value of (/Root/Location/step[1]/text())[1]  
  with     "new text describing the manu step"  
');  
SELECT @myDoc;  
-- update attribute value  
SET @myDoc.modify('  
  replace value of (/Root/Location/@LaborHours)[1]  
  with     "100.0"  
');  
SELECT @myDoc;  
```  
  
 Observe que o destino atualizado deve ser, no máximo, um nó que seja explicitamente especificado na expressão de caminho adicionando um "[1]" no fim da expressão.  
  
### <a name="b-using-the-if-expression-to-determine-replacement-value"></a>B. Usando a expressão if para determinar o valor de substituição  
 Você pode especificar o **se** expressão em Expression2 do **substituir o valor de XML DML** instrução, conforme mostrado no exemplo a seguir. Expression1 identifica que o atributo LaborHours do primeiro centro de trabalho será atualizado. Expression2 usa uma **se** expressão para determinar o novo valor do atributo LaborHours.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours=".1"  
            MachineHours=".2" >Manu steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
--SELECT @myDoc  
  
SET @myDoc.modify('  
  replace value of (/Root/Location[1]/@LaborHours)[1]  
  with (  
       if (count(/Root/Location[1]/step) > 3) then  
         "3.0"  
       else  
          "1.0"  
      )  
')  
SELECT @myDoc  
```  
  
### <a name="c-updating-xml-stored-in-an-untyped-xml-column"></a>C. Atualizando XML armazenado em uma coluna XML sem tipo  
 O exemplo a seguir atualiza XML armazenado em uma coluna:  
  
```  
drop table T  
go  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the current <ProductDescription> element  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
-- update the ProductName attribute value  
UPDATE T  
SET x.modify('  
  replace value of (/Root/ProductDescription/@ProductName)[1]  
  with "New Road Bike" ')  
-- verify the update  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
```  
  
### <a name="d-updating-xml-stored-in-a-typed-xml-column"></a>D. Atualizando XML armazenado em uma coluna XML com tipo  
 Este exemplo substitui os valores em um documento de instruções de fabricação armazenado em uma coluna XML digitada.  
  
 No exemplo, primeiro você cria uma tabela (T) com uma coluna XML digitada no banco de dados AdventureWorks. Depois, você copia a instância XML de instruções de fabricação da coluna Instructions na tabela ProductModel para a tabela T. Em seguida, as inserções são aplicadas ao XML na tabela T.  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
--insert a new location - <Location 1000/>.   
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
insert <MI:Location LocationID="1000"  LaborHours="1000"  LotSize="1000" >  
           <MI:step>Do something using <MI:tool>hammer</MI:tool></MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
go  
-- Now replace manu. tool in location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/MI:step/MI:tool)[1]   
  with   "screwdriver"  
')  
go  
select Instructions  
from T  
-- Now replace value of lot size  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/@LotSize)[1]   
  with   500 cast as xs:decimal ?  
')  
go  
select Instructions  
from T  
```  
  
 Observe o uso de **cast** ao substituir o valor LotSize. Isso é necessário quando o valor dever ser de um tipo específico. Neste exemplo, se 500 fosse o valor, a conversão explícita não seria necessária.  
  
## <a name="see-also"></a>Consulte também  
 [Comparar XML digitado com XML não digitado](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Criar instâncias de dados XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Métodos de tipos de dados xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguagem de modificação de dados XML &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
