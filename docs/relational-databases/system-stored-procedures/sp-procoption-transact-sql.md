---
title: sp_procoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_procoption
- sp_procoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_procoption
ms.assetid: 6f0221bd-70b4-4b04-b15d-722235aceb3c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcde4fd9439862dd88bdb1ff8c9eb40ff85ce0d4
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590420"
---
# <a name="spprocoption-transact-sql"></a>sp_procoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Define ou limpa um procedimento armazenado para execução automática. Um procedimento armazenado que é definido como execuções de execução automática sempre que uma instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é iniciado.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_procoption [ @ProcName = ] 'procedure'   
    , [ @OptionName = ] 'option'   
    , [ @OptionValue = ] 'value'   
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@ProcName =** ] **'**_procedimento_**'**  
 É o nome do procedimento para o qual definir uma opção. *procedimento* está **nvarchar(776)**, sem padrão.  
  
 [  **@OptionName =** ] **'**_opção_**'**  
 É o nome da opção a ser definida. O único valor para *opção* é **inicialização**.  
  
 [  **@OptionValue =** ] **'**_valor_**'**  
 Se deseja definir a opção on (**true** ou **na**) ou desativado (**false** ou **off**). *valor* está **varchar(12)**, sem padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou um número de erro (falha)  
  
## <a name="remarks"></a>Comentários  
 Procedimentos de inicialização devem estar na **mestre** de banco de dados e não pode conter parâmetros de entrada ou saída. A execução dos procedimentos armazenados inicia quando todos os bancos de dados são recuperados e a mensagem "A recuperação foi concluída" é registrada na inicialização.  
  
## <a name="permissions"></a>Permissões  
 Exige associação à função de servidor fixa **sysadmin** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir define um procedimento para execução automática.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';   
```  
  
 O exemplo a seguir interrompe a execução automática de um procedimento.  
  
```  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';   
```  
  
## <a name="see-also"></a>Consulte também  
 [Executar um procedimento armazenado](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)  
  
  
