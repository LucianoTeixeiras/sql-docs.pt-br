---
title: STIsRing (tipo de dados geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsRing_TSQL
- STIsRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsRing (geometry Data Type)
ms.assetid: ea0063be-1c74-4cc4-ac6f-b65321ddfa54
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dfe97518539396e53a8b0f051bf80186b85791f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676184"
---
# <a name="stisring-geometry-data-type"></a>STIsRing (tipo de dados geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retornará 1 se uma instância de **geometry** atender a estes requisitos:
-   É uma instância de **LineString**.  
-   É fechada.  
-   É simples.  
-   Retorna 0 se a instância de **LineString** não atende aos requisitos.  

 Para que uma instância de **geometry** seja fechada e simples, [STIsClosed()](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md) e [STIsSimple()](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md) devem retornar 1 quando invocados na instância. Para determinar o tipo de instância de uma **geometry**, use [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.STIsRing ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Tipo de retorno do CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Esse método retornará nulo se a instância não for uma **LineString**.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma instância `LineString` vazia e usa `STIsRing()` para testar se a instância é um anel.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0, 0 0)', 0);  
SELECT @g.STIsRing();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [STIsClosed &#40;tipo de dados geometry&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STGeometryType &#40;tipo de dados geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [STIsSimple &#40;tipo de dados geometry&#41;](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)   
 [Métodos OGC em instâncias geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

