---
title: sys.dm_fts_memory_buffers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 26f63826244bacc32377a2b7e3315f9b4696fdd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624024"
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna informações sobre buffers de memória pertencentes a um pool de memória específico usado como parte de um rastreamento de texto completo ou um intervalo de rastreamento de texto completo.  
  
> [!NOTE]
> A coluna a seguir será removida em uma versão futura do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**. Evite usar essa coluna em novos trabalhos de desenvolvimento e planeje modificar os aplicativos que atualmente a utilizam.  

  
|coluna|Data type|Description|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|ID do pool de memória alocada.<br /><br /> 0 = Buffers pequenos<br /><br /> 1 = Buffers grandes|  
|**memory_address**|**varbinary(8)**|Endereço do buffer de memória alocado.|  
|**name**|**nvarchar(4000)**|Nome do buffer de memória compartilhado para o qual esta alocação foi feita.|  
|**is_free**|**bit**|Estado atual de buffer de memória.<br /><br /> 0 = Livre<br /><br /> 1 = Ocupado|  
|**row_count**|**int**|Número de linhas que esse buffer está manipulando atualmente.|  
|**bytes_used**|**int**|Quantidade, em bytes, de memória em uso nesse buffer.|  
|**percent_used**|**int**|Porcentagem de memória alocada usada.|  
  
## <a name="permissions"></a>Permissões  

Na [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Na [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], requer o `VIEW DATABASE STATE` permissão no banco de dados.   
  
## <a name="physical-joins"></a>Junções físicas  
 ![Junções significativas dessa exibição de gerenciamento dinâmico](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "junções significativas dessa exibição de gerenciamento dinâmico")  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relações  
  
|De|Para|Relação|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|Muitos para um|  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Pesquisa de texto completo e funções e exibições de gerenciamento dinâmico de pesquisa semântica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

