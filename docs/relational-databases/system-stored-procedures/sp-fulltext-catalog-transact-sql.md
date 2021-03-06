---
title: sp_fulltext_catalog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab482a70374c9a11256719811db02dd4eb1586e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663234"
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Cria e remove um catálogo de texto completo, e inicia e interrompe a ação de indexação de um catálogo. Catálogos de texto completo podem ser criados para cada banco de dados.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md), e [DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) em vez disso.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@ftcat=**] **'***fulltext_catalog_name***'**  
 É o nome do catálogo de texto completo. Nomes de catálogo devem ser exclusivos para cada banco de dados. *fulltext_catalog_name* está **sysname**.  
  
 [  **@action=**] **'***ação***'**  
 É a ação a ser executada. *ação* está **varchar(20)**, e pode ser um destes valores.  
  
> [!NOTE]  
>  Os catálogos de texto completo podem ser criados, descartados e modificados conforme necessário. Entretanto, evite fazer alterações de esquema em vários catálogos ao mesmo tempo. Essas ações podem ser executadas usando o **sp_fulltext_table** procedimento armazenado, que é a maneira recomendada.  
  
|Valor|Description|  
|-----------|-----------------|  
|**Criar**|Cria um catálogo de texto completo novo, vazio no sistema de arquivos e adiciona uma linha associada em **sysfulltextcatalogs** com o *fulltext_catalog_name* e *root_directory*, Se estiver presente, os valores. *fulltext_catalog_name* deve ser exclusivo no banco de dados.|  
|**Drop**|Descartes *fulltext_catalog_name* removê-lo do sistema de arquivos e excluindo a linha associada na **sysfulltextcatalogs**. Haverá falha nessa ação se esse catálogo contiver índices para uma ou mais tabelas. **sp_fulltext_table** '*table_name*', 'drop' deve ser executado para descartar as tabelas do catálogo.<br /><br /> Um erro será exibido se o catálogo não existir.|  
|**start_incremental**|Inicia uma população incremental para *fulltext_catalog_name*. Um erro será exibido se o catálogo não existir. Se uma população de índice de texto completo já estiver ativa, um aviso será exibido, mas nenhuma ação de população ocorrerá. Com a população incremental somente as linhas alteradas são recuperadas para indexação de texto completo, desde que haja uma **carimbo de hora** colunas presentes na tabela cujo texto completo indexado.|  
|**start_full**|Inicia uma população completa para *fulltext_catalog_name*. Todas as linhas de todas as tabelas associadas a esse catálogo de texto completo são recuperadas para a indexação de texto completo, mesmo que já tenham sido indexadas.|  
|**Parar**|Interrompe uma população de índice para *fulltext_catalog_name*. Um erro será exibido se o catálogo não existir. Nenhum aviso será exibido se a população já estiver parada.|  
|**Recompilar**|Recria *fulltext_catalog_name*. Quando um catálogo é recriado, o catálogo existente é excluído e um novo catálogo é criado em seu lugar. Todas as tabelas que têm referências de indexação de texto completo são associadas ao novo catálogo. A recriação redefine os metadados de texto completo nas tabelas do sistema de banco de dados.<br /><br /> Se o controle de alterações estiver definido como OFF, a recriação não fará com que ocorra um novo preenchimento do catálogo de texto completo recém-criado. Nesse caso, para preencher novamente, execute **sp_fulltext_catalog** com o **start_full** ou **start_incremental** ação.|  
  
 [  **@path=**] **'***root_directory***'**  
 É o diretório raiz (não o caminho físico completo) para um **criar** ação. *root_directory* está **nvarchar(100)** e tem um valor padrão de NULL, que indica o uso do local padrão especificado na configuração. Esse é o subdiretório Ftdata no diretório Mssql; Por exemplo, C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\FTData. O diretório raiz especificado deve residir em uma unidade no mesmo computador, deve consistir em mais informações além da letra da unidade e não pode ser um caminho relativo. Unidades de rede, unidades removíveis, discos flexíveis e caminhos UNC não têm suporte. Os catálogos de texto completo devem ser criados em um disco rígido local associado a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **@path** é válido somente quando *ação* é **criar**. Para ações diferentes de **crie** (**interromper**, **recompilar**e assim por diante), **@path** deve ser NULL ou omitido.  
  
 Se a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for um servidor virtual em um cluster, o diretório de catálogo especificado precisará estar em uma unidade de disco compartilhada da qual o recurso do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seja dependente. Se @path não for especificado, o local padrão do diretório de catálogo é a unidade de disco compartilhado, no diretório que foi especificado quando o servidor virtual foi instalado.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentários  
 O **start_full** ação é usada para criar um instantâneo completo dos dados de texto completo *fulltext_catalog_name*. O **start_incremental** ação é usada para reindexar somente as linhas alteradas no banco de dados. População incremental pode ser aplicada somente se a tabela tem uma coluna do tipo **carimbo de hora**. Se uma tabela no catálogo de texto completo não contiver uma coluna do tipo **carimbo de hora**, a tabela sofrerá uma população completa.  
  
 Os dados do catálogo de texto completo e do índice são armazenados em arquivos criados em um diretório de catálogo de texto completo. O diretório de catálogo de texto completo é criado como um subdiretório do diretório especificado na **@path** ou no diretório de catálogo de texto completo do servidor padrão se **@path** não é especificado. O nome do diretório de catálogo de texto completo é criado de uma forma que garante que ele será exclusivo no servidor. Portanto, todos os diretórios de catálogo de texto completo em um servidor podem compartilhar o mesmo caminho.  
  
## <a name="permissions"></a>Permissões  
 O chamador precisa ser membro do **db_owner** função. Dependendo da ação solicitada, o chamador não deve ser negado permissões ALTER ou CONTROL (qual **db_owner** tem) no catálogo de texto completo do destino.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-create-a-full-text-catalog"></a>A. Criar um catálogo de texto completo  
 Este exemplo cria um catálogo de texto completo vazio, **Cat_Desc**, no **AdventureWorks2012** banco de dados.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. Para recriar um catálogo de texto completo  
 Este exemplo recria um catálogo de texto completo existente, **Cat_Desc**, no **AdventureWorks2012** banco de dados.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. Iniciar a população de um catálogo de texto completo  
 Este exemplo inicia uma população completa da **Cat_Desc** catálogo.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D. Interromper a população de um catálogo de texto completo  
 Este exemplo interrompe a população do **Cat_Desc** catálogo.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. Para remover um catálogo de texto completo  
 Este exemplo remove os **Cat_Desc** catálogo.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Pesquisa de Texto Completo](../../relational-databases/search/full-text-search.md)  
  
  
