---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: de689f8a0239ce81b9fcf99b846f8d4767a4dbde
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606514"
---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Detalhes da mensagem  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|20596|  
|Origem do evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbólico||  
|Texto da mensagem|Somente '%s' ou membros de db_owner podem descartar o agente anônimo.|  
  
## <a name="explanation"></a>Explicação  
 Você não tem permissões adequadas para descartar o agente da assinatura anônima. O logon usado para chamar [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) deve ser um membro da função de servidor fixa **sysadmin** no Distribuidor ou da função de banco de dados fixa **db_owner** no banco de dados de distribuição ou, então, o usuário deve ter iniciado a primeira execução do agente.  
  
## <a name="user-action"></a>Ação do usuário  
 Efetue logon com as credenciais apropriadas e execute **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de erros e eventos &#40;Replicação&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
