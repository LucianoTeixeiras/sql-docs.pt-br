---
title: Segurança do Snapshot Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e63cee642738036933b0a1e2a9da6b48192fba9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124166"
---
# <a name="snapshot-agent-security"></a>Segurança do Snapshot Agent
  A caixa de diálogo **Segurança do Snapshot Agent** permite specificar:  
  
-   A conta [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows na qual o Snapshot Agent é executado no Distribuidor. A conta do Windows é também referida como *conta do processo*, porque o processo do agente é executado nessa conta.  
  
-   O contexto no qual o SnapshotAgent faz conexões com o Editor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . A conexão pode ser feita representando a conta do Windows ou no contexto de uma conta do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] especificada por você.  
  
    > [!NOTE]  
    >  O Snapshot Agent faz conexões com o Editor mesmo que o Publicador e o Distribuidor estejam no mesmo computador. O Snapshot Agent também faz conexões com o Distribuidor; essas conexões são sempre feitas representando a conta do Windows na qual o agente é executado.  
  
     Para Editores Oracle, especifique o contexto no qual o Snapshot Agent faz conexão com o Publicador na caixa de diálogo **Propriedades do Publicador** (disponível na caixa de diálogo **Propriedades do Distribuidor** ). Para obter mais informações, consulte [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Todas as contas devem ser válidas, com a senha correta especificada para cada conta. Contas e senhas não são validadas até que um agente seja executado.  
  
## <a name="options"></a>Opções  
 **Process account**  
 Insira uma conta  Windows na qual o Snapshot Agent é executado no Distribuidor. A conta do Windows especificada deve:  
  
-   Ser, no mínimo, um membro da função de banco de dados fixa **db_owner** no banco de dados de distribuição.  
  
-   Ter permissões de gravação no compartilhamento de instantâneo.  
  
 **Senha** e **Confirmar senha**  
 Insira a senha para a conta do Windows.  
  
 **Conectar ao Publicador**  
 Selecione se o Snapshot Agent deve fazer conexões com o Publicador e o Distribuidor representando a conta especificada na caixa de texto **Conta de processo** ou usando uma conta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se você optar por usar uma conta do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , insira um logon e uma senha [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  É recomendável a seleção para representar a conta do Windows em vez de usar uma conta do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 A conta do Windows ou do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usada para conexão com o Assinante deve ser, no mínimo, um membro da função de banco de dados fixa **db_owner** no banco de dados de publicação.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar logons e senhas na replicação](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modelo de segurança do agente de replicação](security/replication-agent-security-model.md)   
 [Visão geral dos agentes de replicação](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  
