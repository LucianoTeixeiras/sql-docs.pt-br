---
title: StringFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2740c7fb25b71e3588bebb924ea9d5f907e3560
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657714"
---
# <a name="stringformatenum"></a>StringFormatEnum
Especifica o formato ao recuperar um [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) como uma cadeia de caracteres.  
  
|Constante|Valor|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Delimita linhas por *RowDelimiter*, colunas por *ColumnDelimiter*e os valores por nulos *NullExpr*. Esses três parâmetros do [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) método são válidas somente com um *StringFormat* dos **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>Equivalente do ADO/WFC  
 Pacote: **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>Aplica-se a  
 [Método GetString (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
