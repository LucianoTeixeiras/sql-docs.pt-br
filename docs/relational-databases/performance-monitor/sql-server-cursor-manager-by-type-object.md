---
title: SQL Server, objeto Gerenciador de cursor por tipo | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 9c1a0cc508cc9e0ef3bca52a82f8b681c25e6c49
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380217"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server, objeto Cursor Manager by Type
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  O objeto **SQLServer:Gerenciador de Cursor por Tipo** fornece contadores para monitorar cursores, agrupados por tipo.  
  
 Esta tabela descreve os contadores do **Gerenciador de Cursor por Tipo** do SQL Server.  
  
|Contadores do Gerenciador de Cursor por Tipo|Descrição|  
|-------------------------------------|-----------------|  
|**Cursores ativos**|Número de cursores ativos.|  
|**Taxa de Acertos do Cache**|Taxa entre acertos e pesquisas do cache.|  
|**Base do Índice de Ocorrência no Cache**|Somente para uso interno.| 
|**Contagens de Cursor em Cache**|Número de cursores de um determinado tipo no cache.|  
|**Contagem de Uso de Cache de Cursor/s**|Número de vezes em que cada tipo de cursor em cache foi usado.|  
|**Uso de memória do cursor**|Quantidade de memória consumida por cursores, em quilobytes (KB).|  
|**Solicitações de Cursor/s**|Número de solicitações de cursor SQL recebidas por servidor.|  
|**Uso de tabelas de trabalho do cursor**|Número de tabelas de trabalho usadas por cursores.|  
|**Número de planos de cursor ativos**|Número de planos de cursor.|  
  
 Cada contador no objeto contém as seguintes instâncias:  
  
|Instância do Gerenciador de Cursor|Descrição|  
|-----------------------------|-----------------|  
|**_Total**|Informações de todos os cursores.|  
|**Cursor API**|Apenas informações de cursor de API.|  
|**Cursor Global de TSQL**|Apenas informações de cursor global de [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**Cursor Local de TSQL**|Apenas informações do cursor local de [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
  
## <a name="see-also"></a>Consulte Também  
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
