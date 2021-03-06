---
title: Propriedade UnderlyingValue | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7bcb751fb32634fc544dfa11ee862cd47112514
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836064"
---
# <a name="underlyingvalue-property"></a>Propriedade UnderlyingValue
Indica o valor atual de um [campo](../../../ado/reference/ado-api/field-object.md) objeto no banco de dados.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um **Variant** valor que indica o valor de **campo**.  
  
## <a name="remarks"></a>Comentários  
 Use o **UnderlyingValue** propriedade para retornar o valor do campo atual do banco de dados. O valor do campo na **UnderlyingValue** propriedade é o valor que é visível para a transação e pode ser o resultado de uma atualização recente por outra transação. Isso pode ser diferente de [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) propriedade, que reflete o valor que foi retornado originalmente para o [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Isso é semelhante a usar o [ressincronizar](../../../ado/reference/ado-api/resync-method.md) método, mas o **UnderlyingValue** propriedade retorna apenas o valor para um campo específico do registro atual. Isso é o mesmo valor que o [ressincronizar](../../../ado/reference/ado-api/resync-method.md) usa o método para substituir o [valor](../../../ado/reference/ado-api/value-property-ado.md) propriedade.  
  
 Quando você usa essa propriedade com o **OriginalValue** propriedade, você pode resolver conflitos que podem surgir de atualizações em lotes.  
  
## <a name="record"></a>Record  
 Para [registro](../../../ado/reference/ado-api/record-object-ado.md) objetos, essa propriedade ficará vazia para campos adicionados antes [atualização](../../../ado/reference/ado-api/update-method.md) é chamado.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de OriginalValue e UnderlyingValue exemplo das propriedades (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Exemplo de OriginalValue e UnderlyingValue propriedades (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Propriedade OriginalValue (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Método Resync](../../../ado/reference/ado-api/resync-method.md)
