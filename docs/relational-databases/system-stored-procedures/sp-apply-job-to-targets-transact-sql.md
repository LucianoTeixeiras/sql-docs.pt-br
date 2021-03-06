---
title: sp_apply_job_to_targets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1583f6de4938451b03eabfb7c9425120fa37f2fc
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537830"
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aplica um trabalho a um ou mais servidores de destino ou aos servidores de destino pertencentes a um ou mais grupos de servidores de destino.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@job_id =**] *job_id*  
 O número de identificação do trabalho a ser aplicado aos servidores de destino ou grupos de servidores de destino especificados. *job_id* está **uniqueidentifier**, com um padrão NULL.  
  
 [  **@job_name =**] **'**_job_name_**'**  
 O nome do trabalho a ser aplicado aos grupos de servidores de destino ou servidores de destino associados especificados. *job_name* está **sysname**, com um padrão NULL.  
  
> [!NOTE]  
>  Qualquer um dos *job_id* ou *job_name* deve ser especificado, mas não podem ser especificados.  
  
 [  **@target_server_groups =**] **'**_target_server_groups_**'**  
 Uma lista separada por vírgulas de grupos de servidores de destino aos quais o trabalho especificado será aplicado. *target_server_groups* está **nvarchar(2048)**, com um padrão NULL.  
  
 [  **@target_servers=** ] **'**_target_servers_**'**  
 Uma lista separada por vírgulas de servidores de destino aos quais o trabalho especificado será aplicado. *target_servers*está **nvarchar(2048)**, com um padrão NULL.  
  
 [  **@operation=** ] **'**_operação_**'**  
 Se o trabalho especificado deve ser aplicado aos ou removidos dos servidores de destino ou grupos de servidores de destino especificados. *operação*está **varchar(7)**, com um padrão APPLY. As operações válidas são **APPLY** e **remover**.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_apply_job_to_targets** fornece uma maneira fácil de aplicar (ou remover) um trabalho de vários servidores de destino, e é uma alternativa à chamada **sp_add_jobserver** (ou **sp_delete_jobserver**) uma vez para cada servidor de destino necessário.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros dos **sysadmin** função fixa de servidor pode executar este procedimento.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir aplica o trabalho `Backup Customer Information` criado anteriormente a todos os servidores de destino do grupo `Servers Maintaining Customer Information`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
