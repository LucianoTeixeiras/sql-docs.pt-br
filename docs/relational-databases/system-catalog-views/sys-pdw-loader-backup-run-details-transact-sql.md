---
title: sys.pdw_loader_backup_run_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 76c6b3030ba8701e5d5bb1753a09b1390a713e07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727965"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contém mais informações detalhadas, além das informações no [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md), e sobre backup em andamento e concluído e operações de restauração na [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e sobre em andamento e concluir o backup, restauração e operações de carregamento em [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. As informações persistem entre os reinícios do sistema.  
  
|Nome da coluna|Tipo de dados|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|Identificador exclusivo de um backup específico ou a restauração da execução.<br /><br /> run_id e pdw_node_id formam a chave para esta exibição.||  
|pdw_node_id|**int**|Identificador exclusivo de um nó de dispositivo para o qual esse registro contém detalhes.<br /><br /> run_id e pdw_node_id formam a chave para esta exibição.|Consulte node_id na [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(16)**|O status atual da execução.|'CANCELLED', 'COMPLETED', 'FAILED', 'QUEUED', 'RUNNING'|  
|start_time|**datetime**|Hora em que a operação iniciada neste nó específico.||  
|end_time|**datetime**|Hora em que a operação foi encerrado neste nó específico, se houver.||  
|total_elapsed_time|**int**|Total de tempo a operação tem em execução neste nó específico.|Se total_elapsed_time exceder o valor máximo para um inteiro (24,8 dias em milissegundos), ela causará falha de materialização devido a estouro.<br /><br /> O valor máximo em milissegundos é equivalente a 24,8 dias.|  
|Progresso|**int**|Progresso da operação expressada como uma porcentagem.|0 a 100|  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e Parallel Data Warehouse exibições do catálogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
