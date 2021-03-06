---
title: ShortestLineTo (tipo de dados geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c495bd27ef5464b0fa56b94513c24eeb4641240e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689204"
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (tipo de dados geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retorna uma instância de **LineString** com dois pontos que representam a distância mais curta entre as duas instâncias de **geografia**. O comprimento da instância de **LineString** retornado é a distância entre as duas instâncias de **geografia**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>Argumentos  
 *geography_other*  
 Especifica a segunda instância de **geography** para a qual a instância de **geography** de chamada está tentando determinar a distância mais curta.  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Tipo de retorno do CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 O método retorna uma instância de **LineString** com pontos de extremidade nas bordas das duas instâncias de **geografia** sem intersecção que estão sendo comparadas. O comprimento de **LineString** retornado é igual à distância mais curta entre as duas instâncias de **geografia**. Uma instância de **LineString** vazia é retornada quando as duas instâncias de **geografia** se interseccionam.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Chamando ShortestLineTo() em instâncias sem interseção  
 Este exemplo localiza a distância mais curta entre uma instância de `CircularString` e uma instância de `LineString` e retorna a instância de `LineString` que conecta os dois pontos:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Chamando ShortestLineTo() em instâncias com interseção  
 Este exemplo retorna uma instância de `LineString` vazia porque a instância de `LineString` cruza a instância de `CircularString`:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>Consulte Também  
 [Métodos estendidos em instâncias geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
