---
title: sp_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexes_TSQL
- sp_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexes
ms.assetid: 25469e72-9d95-463f-912a-193471c8f5e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b1a14d1cf8c9eac0ace93e3aac6e16219fd60eb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791244"
---
# <a name="spindexes-transact-sql"></a>sp_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações de índice da tabela remota especificada.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_indexes [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_db' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @table_server=] '*table_server*'  
 É o nome de um servidor vinculado que executa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para o qual as informações da tabela estão sendo solicitadas. *table_server* está **sysname**, sem padrão.  
  
 [ @table_name=] '*table_name*'  
 É o nome da tabela remota para a qual as informações de índice devem ser fornecidas. *table_name* está **sysname**, com um padrão NULL. Se NULL, todas as tabelas no banco de dados especificado serão retornadas.  
  
 [ @table_schema=] '*table_schema*'  
 Especifica o esquema de tabela. No ambiente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], isso corresponde ao proprietário de tabela. *table_schema* está **sysname**, com um padrão NULL.  
  
 [ @table_catalog=] '*table_db*'  
 É o nome do banco de dados no qual *table_name* reside. *table_db* está **sysname**, com um padrão NULL. Se for NULL, *table_db* assume como padrão **mestre**.  
  
 [ @index_name=] '*index_name*'  
 É o nome do índice para o qual as informações estão sendo solicitadas. *índice* está **sysname**, com um padrão NULL.  
  
 [ @is_unique=] '*is_unique*'  
 É o tipo de índice para o qual as informações devem ser retornadas. *is_unique* está **bit**, com um padrão de NULL, e pode ser um dos valores a seguir.  
  
|Valor|Description|  
|-----------|-----------------|  
|1|Retorna informações sobre índices exclusivos.|  
|0|Retorna informações sobre índices que não são exclusivos.|  
|NULL|Retorna informações sobre todos os índices.|  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|TABLE_CAT|**sysname**|Nome do banco de dados onde a tabela especificada reside.|  
|TABLE_SCHEM|**sysname**|Esquema da tabela.|  
|TABLE_NAME|**sysname**|Nome da tabela remota.|  
|NON_UNIQUE|**smallint**|Se o índice é exclusivo ou não exclusivo:<br /><br /> 0 = Exclusivo<br /><br /> 1 = Não exclusivo|  
|INDEX_QUALIFER|**sysname**|Nome do proprietário do índice. Alguns produtos DBMS permitem que outros usuários, que não o proprietário da tabela, criam índices. Na [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], essa coluna é sempre o mesmo que **TABLE_NAME**.|  
|INDEX_NAME|**sysname**|Nome do índice.|  
|TYPE|**smallint**|Tipo de índice:<br /><br /> 0 = Estatísticas de uma tabela<br /><br /> 1 = Clusterizado<br /><br /> 2 = Com hash<br /><br /> 3 = outros|  
|ORDINAL_POSITION|**int**|Posição ordinal da coluna no índice. A primeira coluna no índice é 1. Esta coluna sempre retorna um valor.|  
|COLUMN_NAME|**sysname**|É o nome correspondente da coluna para cada coluna do TABLE_NAME retornado.|  
|ASC_OR_DESC|**varchar**|É a ordem usada no agrupamento:<br /><br /> A = Crescente<br /><br /> D = Decrescente<br /><br /> NULL = Não aplicável<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sempre retorna A.|  
|CARDINALITY|**int**|É o número de linhas na tabela ou valores exclusivos no índice.|  
|PAGES|**int**|É o número de páginas para armazenar o índice ou a tabela.|  
|FILTER_CONDITION|**nvarchar (** 4000 **)**|O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não retorna um valor.|  
  
## <a name="permissions"></a>Permissões  
 Requer a permissão SELECT no esquema.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna todas as informações de índice da tabela `Employees` do banco de dados `AdventureWorks2012` do servidor vinculado `Seattle1`.  
  
```  
EXEC sp_indexes @table_server = 'Seattle1',   
   @table_name = 'Employee',   
   @table_schema = 'HumanResources',  
   @table_catalog = 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Consulte também  
 [Distribuído procedimentos armazenados de consultas &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
