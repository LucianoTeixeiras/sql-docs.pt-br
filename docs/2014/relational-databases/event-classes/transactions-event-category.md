---
title: Categoria de evento de transações | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 076e68de4dc5d4e25f6cabe6b39ac4a61a05033a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801098"
---
# <a name="transactions-event-category"></a>Categoria de eventos Transactions
  As classes de evento **Transactions** podem ser usadas para monitorar o status das transações. Os nomes da classe de evento que são predeterminados com **TM:** são usados para rastrear as operações relacionadas à transação que são enviadas pela interface de gerenciamento de transações.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Classe de evento DTCTransaction](dtctransaction-event-class.md)|Rastreia as transações coordenadas pelo MS DTC (Coordenador de Transações Distribuídas da [!INCLUDE[msCoName](../../includes/msconame-md.md)] ). Essas são transações distribuídas entre dois ou mais bancos de dados ou instâncias do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe de evento SQLTransaction](sqltransaction-event-class.md)|Rastreia as instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN e ROLLBACK TRAN.|  
|[TM: Begin Tran concluída a classe de evento](tm-begin-tran-completed-event-class.md)|Indica que uma solicitação BEGIN TRANSACTION foi concluída.|  
|[TM: Begin Tran Starting a classe de evento](tm-begin-tran-starting-event-class.md)|Indica que uma solicitação BEGIN TRANSACTION está iniciando.|  
|[TM: Commit Tran concluída a classe de evento](tm-commit-tran-completed-event-class.md)|Indica que uma solicitação COMMIT TRANSACTION foi concluída.|  
|[TM: Classe de evento Commit Tran Starting](tm-commit-tran-starting-event-class.md)|Indica que uma solicitação COMMIT TRANSACTION está iniciando.|  
|[TM: Promote Tran concluída a classe de evento](tm-promote-tran-completed-event-class.md)|Indica que uma solicitação PROMOTE TRANSACTION foi concluída.|  
|[TM: Classe de evento promote Tran Starting](tm-promote-tran-starting-event-class.md)|Indica que uma solicitação PROMOTE TRANSACTION está iniciando.|  
|[TM: Classe de evento Rollback Tran Completed](tm-rollback-tran-completed-event-class.md)|Indica que uma solicitação ROLLBACK TRANSACTION foi concluída.|  
|[TM: Classe de evento começando do Rollback Tran](tm-rollback-tran-starting-event-class.md)|Indica que uma solicitação ROLLBACK TRANSACTION está iniciando.|  
|[TM: Classe de evento de Completed Save Tran](tm-save-tran-completed-event-class.md)|Indica que uma solicitação SAVE TRANSACTION foi concluída.|  
|[TM: Classe de evento Save Tran Starting](tm-save-tran-starting-event-class.md)|Indica que uma solicitação SAVE TRANSACTION está iniciando.|  
|[Classe de evento TransactionLog](transactionlog-event-class.md)|Rastreia quando as transações são gravadas em um log de transações do banco de dados.|  
  
  
