---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd700923bb41475c7ee9880f812adf6155407218
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798114"
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID do evento|41301|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|COMMIT_DEPENDENCY_FAILURE|  
|Texto da mensagem|Uma transação anterior na qual a transação atual obteve uma dependência foi anulada, e a transação atual não pode mais ser confirmada.|  
  
## <a name="explanation"></a>Explicação  
A transação encontrou uma falha de dependência e agora está condenada.  
  
Esse erro também pode ser causado por transações dependentes demais. Qualquer transação de gravação pode ter um número limitado de transações dependentes. Por exemplo, esse erro pode ocorrer se muitas transações de leitura tentarem executar uma dependência na transação de atualização.  
  
## <a name="user-action"></a>Ação do usuário  
Não execute nenhum trabalho na transação. Chame ROLLBACK TRAN para reverter a transação. Para obter mais informações, veja [OLTP in-memory &#40;Otimização na memória&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Consulte Também  
[Habilitar e desabilitar grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
