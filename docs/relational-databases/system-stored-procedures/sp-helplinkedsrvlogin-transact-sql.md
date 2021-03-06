---
title: sp_helplinkedsrvlogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4242494c94518817dd7ba161ddc16e1c47b51952
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659094"
---
# <a name="sphelplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornece informações sobre mapeamentos de logon definidos em um servidor vinculado específico usado para consultas distribuídas e procedimentos armazenados remotos.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@rmtsrvname=**] **'***rmtsrvname***'**  
 É o nome do servidor vinculado para o qual o mapeamento de logon se aplica. *rmtsrvname* está **sysname**, com um padrão NULL. Se for NULL, todos os mapeamentos de logon definidos em todos os servidores vinculados definidos no computador local que executa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serão retornados.  
  
 [  **@locallogin=**] **'***locallogin***'**  
 É o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login no servidor local que tem um mapeamento para o servidor vinculado *rmtsrvname*. *locallogin* está **sysname**, com um padrão NULL. NULL Especifica que todos os mapeamentos de logon definidos em *rmtsrvname* são retornados. Se não for NULL, um mapeamento de *locallogin* à *rmtsrvname* já deve existir. *locallogin* pode ser um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logon ou um usuário do Windows. O usuário do Windows deve ter acesso ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diretamente ou por meio de sua associação em um grupo do Windows com acesso concedido.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**Servidor vinculado**|**sysname**|Nomes do servidor vinculado.|  
|**Logon local**|**sysname**|Logon local ao qual o mapeamento aplica.|  
|**Mapeamento de autoatendimento**|**smallint**|0 = **logon local** é mapeado para **logon remoto** ao se conectar ao **servidor vinculado**.<br /><br /> 1 = **logon local** é mapeado para o mesmo logon e senha ao se conectar ao **servidor vinculado**.|  
|**Logon remoto**|**sysname**|Nome de logon no **LinkedServer** que é mapeado para **LocalLogin** quando **IsSelfMapping** é 0. Se **IsSelfMapping** é 1, **RemoteLogin** é NULL.|  
  
## <a name="remarks"></a>Comentários  
 Antes de excluir mapeamentos de logon, use **sp_helplinkedsrvlogin** para determinar os servidores vinculados que estão envolvidos.  
  
## <a name="permissions"></a>Permissões  
 Nenhuma permissão é verificada.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. Exibindo todos os mapeamentos de logon para todos os servidores vinculados  
 O exemplo a seguir exibe todos os mapeamentos de logon para todos os servidores vinculados definidos no computador local que executa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>B. Exibindo todos os mapeamentos de logon para um servidor vinculado  
 O exemplo a seguir exibe todos os mapeamentos de logon definidos localmente para o servidor vinculado `Sales`.  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>C. Exibindo todos os mapeamentos de logon para um logon local  
 O exemplo a seguir exibe todos os mapeamentos de logon definidos localmente para o logon `Mary`.  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de segurança armazenados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
