---
title: sys. availability_databases_cluster (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_databases_cluster_TSQL
- sys.availability_databases_cluster
- availability_databases_cluster_TSQL
- availability_databases_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.availability_databases_cluster catalog view
- Availability Groups [SQL Server], databases
ms.assetid: 8d9c57e5-7f39-4315-b466-92748231140a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7d312a5ecb60e1ab046b0108e01ef1834adaa900
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842304"
---
# <a name="sysavailabilitydatabasescluster-transact-sql"></a>sys.availability_databases_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada banco de dados de disponibilidade na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que está hospedando uma réplica de disponibilidade para qualquer grupo de disponibilidade AlwaysOn no cluster Windows Server Failover Clustering (WSFC), independentemente se local copiar banco de dados foi unido ao grupo de disponibilidade.  
  
> [!NOTE]  
>  Quando um banco de dados é adicionado a um grupo de disponibilidade, o banco de dados primário é unido automaticamente ao grupo. Os bancos de dados secundários deve estar preparados em cada réplica secundária para poderem ser unidos ao grupo de disponibilidade.   
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificador exclusivo do grupo de disponibilidade, se houver, do qual o banco de dados está participando.<br /><br /> NULL = o banco de dados não faz parte de uma réplica de disponibilidade em um grupo de disponibilidade.|  
|**group_database_id**|**uniqueidentifier**|Identificador exclusivo do banco de dados no grupo de disponibilidade, se houver, do qual o banco de dados está participando. **group_database_id** é o mesmo para este banco de dados na réplica primária e em cada réplica secundária na qual o banco de dados foi unido ao grupo de disponibilidade.<br /><br /> NULL = o banco de dados não faz parte de uma réplica de disponibilidade em nenhum grupo de disponibilidade.|  
|**database_name**|**sysname**|O nome do banco de dados que foi adicionado ao grupo de disponibilidade.|  
  
## <a name="permissions"></a>Permissões  
 Se o chamador de **sys. availability_databases_cluster** não é o proprietário do banco de dados, as permissões mínimas necessárias para ver a linha correspondente serão ALTER ANY DATABASE ou permissão VIEW ANY DATABASE em nível de servidor ou criar Permissão de banco de dados na **mestre** banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)   
 [sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md)   
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
