---
title: Conjunto de linhas DBSCHEMA_CATALOGS | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0632d90765112ee54de8e78a66fdefa1ff27334f
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemacatalogs-rowset"></a>Conjunto de linhas DBSCHEMA_CATALOGS
  Identifica os atributos físicos associados a catálogos acessíveis a partir do DBMS (sistema de gerenciamento de banco de dados).  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DBSCHEMA_CATALOGS** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|O nome do catálogo. Não pode ser nulo.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Uma descrição legível da tabela.|  
|**FUNÇÕES**|**DBTYPE_WSTR**||Uma lista de funções delimitadas por vírgulas às quais pertence o usuário atual.<br /><br /> Um asterisco (\*) é incluído como uma função se o usuário atual é um administrador do servidor ou banco de dados.<br /><br /> **Username** é anexado a **ROLES** quando uma das funções usa a segurança dinâmica.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||A data da última modificação do catálogo.|  
  
 O conjunto de linhas é classificado em **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DBSCHEMA_CATALOGS** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Opcional|  
  
## <a name="see-also"></a>Consulte também  
 [Conjuntos de linhas do esquema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  