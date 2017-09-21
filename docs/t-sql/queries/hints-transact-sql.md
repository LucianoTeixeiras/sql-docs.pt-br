---
title: Dicas (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query optimizer [SQL Server], hints
- hints [SQL Server], about hints
- SELECT statement [SQL Server], hints
- hints [SQL Server]
- INSERT statement [SQL Server], hints
- UPDATE statement [SQL Server], hints
- DELETE statement [SQL Server], hints
ms.assetid: 99412475-b0df-4264-9938-33a0b302b41a
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2d8b50a38299162677b1f7d5bbff501fba9881
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="hints-transact-sql"></a>dicas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Dicas são opções ou estratégias especificadas para aplicação pelo processador de consultas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em instruções SELECT, INSERT, UPDATE ou DELETE. As dicas substituem todos os planos de execução que o otimizador de consulta possa selecionar para uma consulta.  
  
> [!CAUTION]  
>  Porque o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] normalmente, o otimizador de consulta seleciona o melhor plano de execução para uma consulta, é recomendável que \<as dicas join_hint >, \<query_hint >, e \<table_hint > ser usados apenas como último recurso por experiente os desenvolvedores e administradores de banco de dados.
  
 As seguintes dicas são descritas nesta seção:  
  
-   [Dicas de junção](../../t-sql/queries/hints-transact-sql-join.md)  
  
-   [Dicas de consulta](../../t-sql/queries/hints-transact-sql-query.md)  
  
-   [Dica de tabela](../../t-sql/queries/hints-transact-sql-table.md)  
  
  
