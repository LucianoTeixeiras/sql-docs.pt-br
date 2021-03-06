---
title: Propriedade OriginalValue (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d25c44883c7f04f1543639ecc870c00ad5beb9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648985"
---
# <a name="originalvalue-property-ado"></a>Propriedade OriginalValue (ADO)
Indica o valor de uma [campo](../../../ado/reference/ado-api/field-object.md) que existiam no registro antes de todas as alterações foram feitas.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um **Variant** valor que representa o valor de um campo antes de qualquer alteração.  
  
## <a name="remarks"></a>Comentários  
 Use o **OriginalValue** propriedade para retornar o valor do campo original para um campo do registro atual.  
  
 Na *modo de atualização imediata* (no qual o provedor grava as alterações à fonte de dados subjacentes depois de chamar o [atualizar](../../../ado/reference/ado-api/update-method.md) método), o **OriginalValue** retorna de propriedade o valor do campo que existiam antes de todas as alterações (ou seja, desde a última **atualização** chamada de método). Isso é o mesmo valor que o [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) usa o método para substituir o [valor](../../../ado/reference/ado-api/value-property-ado.md) propriedade.  
  
 Na *modo de atualização em lotes* (em que o provedor armazena em cache várias alterações e os grava em fonte de dados subjacente somente quando você chama o [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) método), o **OriginalValue** propriedade retorna o valor do campo que existiam antes de todas as alterações (ou seja, desde a última **UpdateBatch** chamada de método). Isso é o mesmo valor que o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) usa o método para substituir o **valor** propriedade. Quando você usa essa propriedade com o [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) propriedade, você pode resolver conflitos que podem surgir de atualizações em lotes.  
  
## <a name="record"></a>Record  
 Para [registro](../../../ado/reference/ado-api/record-object-ado.md) objetos, o **OriginalValue** propriedade ficará vazia para campos adicionados antes [atualização](../../../ado/reference/ado-api/update-method.md) é chamado.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de OriginalValue e UnderlyingValue exemplo das propriedades (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Exemplo de OriginalValue e UnderlyingValue propriedades (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Propriedade UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
