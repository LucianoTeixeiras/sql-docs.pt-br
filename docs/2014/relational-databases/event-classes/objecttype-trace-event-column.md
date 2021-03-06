---
title: Coluna de evento de rastreamento ObjectType | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31ba88f3bc49d78dc8c68ac77ba6bda90e63aad0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52803748"
---
# <a name="objecttype-trace-event-column"></a>Coluna de evento de rastreamento ObjectType
  A coluna Object Type é usada em diversos eventos de rastreamento. Este tópico descreve os possíveis valores dessa coluna e as definições a ela associadas.  
  
## <a name="object-type-column-values"></a>Valores da coluna Object Type  
  
|Valor|Definição|  
|-----------|----------------|  
|8259|Restrição CHECK|  
|8260|Padrão (restrição ou autônomo)|  
|8262|Restrição FOREIGN KEY|  
|8272|Procedimento armazenado|  
|8274|Regra|  
|8275|Tabela do sistema|  
|8276|Gatilho em servidor|  
|8277|Tabela (definida pelo usuário)|  
|8278|Exibição|  
|8280|Procedimento armazenado estendido|  
|16724|Gatilho CLR|  
|16964|banco de dados|  
|16975|Object|  
|17222|Catálogo de texto completo|  
|17232|Procedimento armazenado CLR|  
|17235|esquema|  
|17475|Credencial|  
|17491|Evento DDL|  
|17741|Evento de gerenciamento|  
|17747|Evento de segurança|  
|17749|Evento de usuário|  
|17985|Função de agregação CLR|  
|17993|Função SQL com valor de tabela embutida|  
|18000|Função de partição|  
|18002|Procedimento do filtro de replicação|  
|18004|Função SQL com valor de tabela|  
|18259|Função do servidor|  
|18263|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows|  
|19265|Chave assimétrica|  
|19277|Chave mestra|  
|19280|Chave Primária|  
|19283|ObfusKey|  
|19521|Logon de chave assimétrica|  
|19523|Logon de certificado|  
|19538|Role|  
|19539|Logon do SQL|  
|19543|Logon do Windows|  
|20034|Associação de serviço remoto|  
|20036|Notificação de eventos em banco de dados|  
|20037|Notificação de eventos|  
|20038|Função SQL escalar|  
|20047|Notificação de eventos em objeto|  
|20051|Sinônimo|  
|20307|Sequência|  
|20549|Ponto de extremidade|  
|20801|Consultas ad hoc que podem ser armazenadas em cache|  
|20816|Consultas preparadas que podem ser armazenadas em cache|  
|20819|Fila do serviço do Service Broker|  
|20821|Restrição UNIQUE|  
|21057|Função de aplicativo|  
|21059|Certificado|  
|21075|Servidor|  
|21076|Gatilho Transact-SQL|  
|21313|Assembly|  
|21318|Função CLR escalar|  
|21321|Função SQL escalar embutida|  
|21328|Esquema de partição|  
|21333|User|  
|21571|Contrato do serviço do Service Broker|  
|21572|Gatilho em banco de dados|  
|21574|Função CLR com valor de tabela|  
|21577|Tabela interna (por exemplo, Tabela Nó XML, Tabela Fila.)|  
|21581|Tipo de mensagem do Service Broker|  
|21586|Rota do Service Broker|  
|21587|Estatísticas|  
|21825<br /><br /> 21827<br /><br /> 21831<br /><br /> 21843<br /><br /> 21847|User|  
|22099|Serviço do Service Broker|  
|22601|Índice|  
|22604|Logon de certificado|  
|22611|Esquema XML|  
|22868|Tipo|  
  
## <a name="see-also"></a>Consulte também  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
