---
title: Eventos WillChangeField e Fieldchangecomplete (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f046a3a33e05228ab5e49116bc46eb9451f43129
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673654"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>Eventos WillChangeField e FieldChangeComplete (ADO)
O **eventos WillChangeField** evento é chamado antes de uma operação pendente altera o valor de um ou mais [campo](../../../ado/reference/ado-api/field-object.md) objetos no [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md). O **FieldChangeComplete** evento é chamado após o valor de um ou mais **campo** objetos foi alterado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *cFields*  
 Um **longo** que indica o número de **campo** objetos no *campos*.  
  
 *Fields*  
 Para **eventos WillChangeField**, o *campos* parâmetro é uma matriz de **variantes** que contém **campo** objetos com os valores originais. Para **FieldChangeComplete**, o *campos* parâmetro é uma matriz de **variantes** que contém **campo** objetos com os valores alterados .  
  
 *pError*  
 Uma [erro](../../../ado/reference/ado-api/error-object.md) objeto. Ele descreve o erro ocorrido se o valor de *adStatus* é **adStatusErrorsOccurred**; caso contrário, ele não está definido.  
  
 *adStatus*  
 Uma [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valor de status.  
  
 Quando **eventos WillChangeField** é chamado, esse parâmetro é definido como **adStatusOK** se a operação que causou o evento foi bem-sucedida. Ele é definido como **adStatusCantDeny** se esse evento não é possível solicitar o cancelamento da operação pendente.  
  
 Quando **FieldChangeComplete** é chamado, esse parâmetro é definido como **adStatusOK** se a operação que causou o evento foi bem-sucedida, ou ao **adStatusErrorsOccurred** se a operação falhou.  
  
 Antes de **eventos WillChangeField** retorna, defina esse parâmetro como **adStatusCancel** ao cancelamento de solicitação da operação pendente.  
  
 Antes de **FieldChangeComplete** retorna, defina esse parâmetro como **adStatusUnwantedEvent** para evitar notificações subsequentes.  
  
 *pRecordset*  
 Um **Recordset** objeto. O **Recordset** para que esse evento ocorreu.  
  
## <a name="remarks"></a>Comentários  
 Um **eventos WillChangeField** ou **FieldChangeComplete** evento pode ocorrer ao definir o [valor](../../../ado/reference/ado-api/value-property-ado.md) propriedade e chamar o [atualização](../../../ado/reference/ado-api/update-method.md) método com os parâmetros de matriz de campo e o valor.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de modelo de eventos ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Resumo do manipulador de eventos ADO](../../../ado/guide/data/ado-event-handler-summary.md)
