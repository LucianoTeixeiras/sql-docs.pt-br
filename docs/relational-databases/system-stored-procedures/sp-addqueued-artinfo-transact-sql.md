---
title: sp_addqueued_artinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c326a8e3a5fa2bd95f536d434ff9782952ba70d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590891"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  O [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) procedimento deve ser usado em vez de **sp_addqueued_artinfo**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) gera um script que contém o **sp_addqueued_artinfo** e **sp_addsynctrigger** chamadas.  
  
 Cria o [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) tabela no assinante que é usado para rastrear as informações de assinatura de artigo (atualização enfileirada e atualização imediata com atualização enfileirada como Failover). Esse procedimento armazenado é executado no assinante, no banco de dados de assinatura.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@artid=** ] **'**_artid_**'**  
 É o nome da ID do artigo. *artid* está **int**, sem padrão  
  
 [  **@article=**] **'**_artigo_**'**  
 É o nome do artigo para o qual gerar um script. *artigo* está **sysname**, sem padrão  
  
 [  **@publisher=**] **'**_publisher_**'**  
 É o nome do servidor do Publicador. *Publisher* está **sysname**, sem padrão.  
  
 [  **@publisher_db=**] **'**_publisher_db_**'**  
 É o nome do banco de dados Publicador. *publisher_db* está **sysname**, sem padrão.  
  
 [  **@publication=**] **'**_publicação_**'**  
 É o nome da publicação para a qual gerar um script. *publicação* está **sysname**, sem padrão.  
  
 [  **@dest_table=** ] _' dest_table_**'**  
 É o nome da tabela de destino. *dest_table* está **sysname**, sem padrão.  
  
 [ **@owner =** ] **'**_proprietário_**'**  
 É o proprietário da assinatura. *proprietário* está **sysname**, sem padrão.  
  
 [  **@cft_table=** ] **'**_cft_table_**'**  
 Nome da tabela de conflito de atualização enfileirada para esse artigo. *cft_table*está **sysname**, sem padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_addqueued_artinfo** é usado pelo agente de distribuição como parte da inicialização de assinatura. Esse procedimento armazenado não é executado com frequência pelos usuários, mas pode ser útil se o usuário precisar configurar manualmente uma assinatura.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) em vez de **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros dos **sysadmin** função de servidor fixa ou **db_owner** banco de dados fixa podem executar **sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>Consulte também  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
