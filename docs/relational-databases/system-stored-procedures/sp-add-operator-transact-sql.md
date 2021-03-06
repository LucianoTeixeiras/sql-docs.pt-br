---
title: sp_add_operator (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 147269759746e143897757aab5518b784e705915
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751574"
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cria um operador (destinatário da notificação) para uso com alertas e trabalhos.  
  
 
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]   
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]   
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]   
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]   
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@name=** ] **'***name***'**  
 O nome de um operador (destinatário da notificação). Esse nome deve ser exclusivo e não pode conter a porcentagem (**%**) caracteres. *nome da* está **sysname**, sem padrão.  
  
 [  **@enabled=** ] *habilitado*  
 Indica o status atual do operador. *habilitada* está **tinyint**, com um padrão de **1** (habilitado). Se **0**, o operador não está habilitado e não recebe notificações.  
  
 [  **@email_address=** ] **'***email_address***'**  
 O endereço de email do operador. Essa cadeia de caracteres é passada diretamente para o sistema de email. *email_address* está **nvarchar(100)**, com um padrão NULL.  
  
 Você pode especificar um endereço de email físico ou um alias para *email_address*. Por exemplo:  
  
 '**jdoe**'ou'**jdoe@xyz.com**'  
  
> [!NOTE]  
>  Você deve usar o endereço de email para Database Mail.  
  
 [ **@pager_address=** ] **'***pager_address***'**  
 O endereço de pager do operador. Essa cadeia de caracteres é passada diretamente para o sistema de email. *pager_address* está **narchar(100)**, com um padrão NULL.  
  
 [  **@weekday_pager_start_time=** ] *weekday_pager_start_time*  
 A hora depois da qual o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent envia notificação de pager ao operador especificado nos dias de semana, de segunda-feira a sexta-feira. *weekday_pager_start_time*está **int**, com um padrão de **090000**, que indica as 9h00 em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [  **@weekday_pager_end_time=** ] *weekday_pager_end_time*  
 O tempo após o qual **SQLServerAgent** service não mais envia notificação por pager ao operador especificado em dias do semana, de segunda-feira a sexta-feira. *weekday_pager_end_time*está **int**, com um padrão de 180000, que indica às 18h em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [  **@saturday_pager_start_time =**] *saturday_pager_start_time*  
 O tempo após o qual **SQLServerAgent** serviço envia notificação por pager ao operador especificado aos sábados. *saturday_pager_start_time* está **int**, com um padrão de 090000, que indica as 9h00 em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [  **@saturday_pager_end_time=** ] *saturday_pager_end_time*  
 O tempo após o qual **SQLServerAgent** service não mais envia notificação de pager ao operador especificado aos sábados. *saturday_pager_end_time*está **int**, com um padrão de **180000**, que indica às 18h em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [ **@sunday_pager_start_time=** ] *sunday_pager_start_time*  
 O tempo após o qual **SQLServerAgent** serviço envia notificação por pager ao operador especificado aos domingos. *sunday_pager_start_time*está **int**, com um padrão de **090000**, que indica as 9h00 em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [  **@sunday_pager_end_time =**] *sunday_pager_end_time*  
 O tempo após o qual **SQLServerAgent** service não mais envia notificação de pager ao operador especificado aos domingos. *sunday_pager_end_time*está **int**, com um padrão de **180000**, que indica às 18h em um relógio de 24 horas e deve ser inserido com o formato HHMMSS.  
  
 [  **@pager_days=** ] *pager_days*  
 É um número que indica os dias em que o operador está disponível para páginas (sujeito aos horários de início/término especificados). *pager_days*está **tinyint**, com um padrão de **0** indicando que o operador nunca está disponível para receber uma página. Valores válidos são de **0** por meio **127**. *pager_days*é calculado somando os valores individuais para os dias necessários. Por exemplo, de segunda-feira a sexta-feira é **2**+**4**+**8**+**16** + **32** = **62**. A tabela a seguir lista o valor de cada dia da semana.  
  
|Valor|Description|  
|-----------|-----------------|  
|**1**|Domingo|  
|**2**|Segunda-feira|  
|**4**|Terça-feira|  
|**8**|Quarta-feira|  
|**16**|Quinta-feira|  
|**32**|Sexta-feira|  
|**64**|Sábado|  
  
 [  **@netsend_address=** ] **'***netsend_address***'**  
 O endereço de rede do operador para o qual a mensagem de rede é enviada. *netsend_address*está **nvarchar(100)**, com um padrão NULL.  
  
 [  **@category_name=** ] **'***categoria***'**  
 O nome da categoria para este operador. *categoria* está **sysname**, com um padrão NULL.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentários  
 **sp_add_operator** deve ser executado a partir de **msdb** banco de dados.  
  
 É oferecido suporte à chamada por pager pelo sistema de email, que deve ter um recurso de email para pager se você quiser usar chamada por pager.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] gerencia trabalhos de forma fácil e com representação gráfica. Além disso, ele é recomendado para criar e gerenciar a infraestrutura de trabalhos.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros dos **sysadmin** pode executar a função de servidor fixa **sp_add_operator**.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir configura as informações do operador para `danwi`. O operador está habilitado. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent envia notificações por pager de segunda a sexta-feira, das 8h às 17h.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_delete_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
