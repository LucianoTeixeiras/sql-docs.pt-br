---
title: 'Lição 1: Convertendo uma tabela em uma estrutura hierárquica | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 66e77d0badf14a804cb82249d03ed552e1f8dcfb
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788698"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lição 1: Convertendo uma tabela em uma estrutura hierárquica
  Os clientes que possuem tabelas que usam autojunções para expressar relações hierárquicas podem converter as tabelas em uma estrutura hierárquica usando esta lição como guia. É relativamente fácil fazer a migração dessa representação para outra usando `hierarchyid`. Depois da migração, os usuários terão uma representação hierárquica compacta e fácil de entender, que poderá ser indexada de várias formas para proporcionar consultas eficientes.  
  
 Esta lição examina uma tabela existente, cria uma tabela contendo uma coluna `hierarchyid`, popula a tabela com os dados da tabela de origem e, depois, demonstra três estratégias de indexação. Eis os tópicos desta lição:  
  
-   [Examinando a estrutura atual da tabela Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Populando uma tabela com dados hierárquicos existentes](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Otimizando a tabela NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Resumo: Convertendo uma tabela em uma estrutura hierárquica](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prerequisites  
 Esta lição exige o banco de dados de exemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
 [Examinando a estrutura atual da tabela Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Próxima lição  
 [Lição 2: Criando e gerenciando dados em uma tabela hierárquica](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
