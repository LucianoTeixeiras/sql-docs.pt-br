---
title: Avaliar a integridade do grupo de disponibilidade usando políticas de grupo
description: Saiba como exibir as políticas do sistema de grupo que o painel Always On usa para fornecer informações sobre a integridade do grupo de disponibilidade.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b409c3d4811bd713478fa9b83c4904c6fb4bd789
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53212065"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Avaliar a integridade do grupo de disponibilidade Always On usando políticas de grupo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  As políticas do sistema de grupos de disponibilidade Always On são usadas pelo painel Always On para fornecer informações sobre a integridade do grupo de disponibilidade ao usuário. Elas são muito úteis na solução inicial de problemas operacionais do grupo de disponibilidade. Essas políticas podem ser estendidas e usadas para personalizar o Painel Always On ou executadas imediatamente a fim de relatar as informações de integridade desejadas.  
  
 Há 14 políticas de sistema para grupos de disponibilidade. Para obter informações detalhadas sobre cada política, veja [Políticas Always On para problemas operacionais com Grupos de Disponibilidade Always On (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Exibir ou avaliar as políticas de sistema de grupos de disponibilidade  
 Para exibir ou executar as políticas de sistema de grupos de disponibilidade no SSMS (SQL Server Management Studio), faça o seguinte:  
  
1.  No **Pesquisador de Objetos**, expanda **Gerenciamento**, **Gerenciamento de Política**, **Políticas** e, em seguida, **Políticas do Sistema**.  
  
2.  Clique com o botão direito do mouse em uma das políticas e clique em **Avaliar**. Se você quiser avaliar a política selecionada, pronto, é só isso! Você pode clicar em **Exibir**, na caixa **Detalhes do destino**, para ver os detalhes dos resultados da avaliação.  
  
3.  Para exibir todos as políticas de sistema dos grupos de disponibilidade, no painel **Selecionar uma página**, clique em **Seleção de Política**.  
  
## <a name="next-steps"></a>Próximas etapas  
 [The Always On health model, part 2: Extending the health model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (O modelo de integridade do Always On, parte 2: estendendo o modelo de integridade).  
  
  
