---
title: Caixa de diálogo Atualizar Tabela (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8c5575f73ff75ef9276bab52571e8670f28e0be
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52780668"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Caixa de diálogo Atualizar Tabela (Visual Database Tools)
  Essa caixa de diálogo lhe permite especificar a tabela a ser atualizada.  
  
 Essa caixa de diálogo aparece se mais de uma tabela forem exibidas no painel Diagrama quando o tipo de consulta é mudado para consulta Update.  
  
 Selecione a tabela a ser atualizada, depois clique em **OK**.\  
  
> [!NOTE]  
>  Se a tabela for publicada para replicação, você precisará fazer alterações no esquema usando a instrução Transact-SQL [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) ou o SMO (SQL Server Management Objects). Ao fazer alterações no esquema com o Criador de Tabelas ou com o Criador do Diagrama de Banco de Dados, ele tenta descartar e recriar a tabela. Não é possível descartar objetos publicados, portanto, haverá falha na alteração de esquema.  
  
## <a name="see-also"></a>Consulte também  
 [Criar consultas Atualização &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
