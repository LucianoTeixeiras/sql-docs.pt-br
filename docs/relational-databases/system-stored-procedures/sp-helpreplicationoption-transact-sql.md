---
title: sp_helpreplicationoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationoption
- sp_helpreplicationoption_TSQL
helpviewer_keywords:
- sp_helpreplicationoption
ms.assetid: ef988dbc-dd0b-4132-80ab-81eebec1cffe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14357c7700980a1e3cc241d2e6b300e830aa4319
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818888"
---
# <a name="sphelpreplicationoption-transact-sql"></a>sp_helpreplicationoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mostra os tipos de opções de replicação habilitados para um servidor. Esse procedimento armazenado é executado em qualquer servidor, em qualquer banco de dados.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpreplicationoption [ [ @optname =] 'option_name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@optname =**] **'***option_name***'**  
 É o nome da opção de replicação que deve ser consultada. *option_name* está **sysname**, com um padrão NULL.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|**Transacional**|Um conjunto de resultados é retornado quando replicação transacional é habilitada.|  
|**mesclagem**|Um conjunto de resultados é retornado quando replicação de mesclagem é habilitada.|  
|NULL (padrão)|Um conjunto de resultados não é retornado.|  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Nome da opção de replicação e pode ser um dos seguintes:<br /><br /> **Transacional**<br /><br /> **mesclagem**|  
|**value**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**versão_principal**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**versão_secundária**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**revisão**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**install_failures**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_helpreplicationoption** é usado para obter informações sobre opções de replicação habilitadas em um servidor específico. Para obter informações sobre um determinado banco de dados, use **sp_helpreplicationdboption**.  
  
## <a name="permissions"></a>Permissões  
 As permissões de execução têm como padrão a função **public** .  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
