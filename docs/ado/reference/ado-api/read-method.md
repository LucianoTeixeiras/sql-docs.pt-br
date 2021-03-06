---
title: Método Read | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b5bbc04c94d491c096db047d574cc3b5fd8ee38
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783954"
---
# <a name="read-method"></a>Método Read
Lê um número especificado de bytes de um binário [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *NumBytes*  
 Opcional. Um **longo** valor que especifica o número de bytes a serem lidos do arquivo ou o [StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md) valor **adReadAll**, que é o padrão.  
  
## <a name="return-value"></a>Valor retornado  
 O **leitura** método lê um número especificado de bytes ou o fluxo inteiro de uma **Stream** do objeto e retorna os dados resultantes como um **Variant**.  
  
## <a name="remarks"></a>Comentários  
 Se *NumBytes* mais do que o número de bytes é deixado na **Stream**, somente os bytes restantes são retornados. A leitura de dados não estão preenchidos para corresponder ao comprimento especificado por *NumBytes*. Se não houver nenhum byte à esquerda para ler, uma variante com um valor nulo será retornada. **Leitura** não pode ser usado para ler com versões anteriores.  
  
> [!NOTE]
>  *NumBytes* sempre mede bytes. Para texto **Stream** objetos ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) está **adTypeText**), use [ReadText](../../../ado/reference/ado-api/readtext-method.md).  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método ReadText](../../../ado/reference/ado-api/readtext-method.md)
