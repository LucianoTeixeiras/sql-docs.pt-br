---
title: spatial_reference_systems (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c2ab77dbaf90edf1421a0d15073258c370de4c7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643434"
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Lista os sistemas de referência espaciais (SRIDs) com suporte do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|O SRID com suporte do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar(128)**|A autoridade do SRID.|  
|authorized_spatial_reference_id|**int**|O SRID especificado pela autoridade indicada em **authority_name**.|  
|well_known_text|**nvarchar(4000)**|A representação WKT do SRID.|  
|unit_of_measure|**nvarchar(128)**|O nome da unidade de medida.|  
|unit_conversion_factor|**float**|O comprimento da unidade de medida em metros.|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
