---
title: Método SetObjectOwner | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43f325382cc556d75d7ab08c5b3dbdc94f68704f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617254"
---
# <a name="setobjectowner-method"></a>Método SetObjectOwner
Especifica o proprietário de um objeto em um [catálogo](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *ObjectName*  
 Um **cadeia de caracteres** valor que especifica o nome do objeto para o qual especificar o proprietário.  
  
 *ObjectType*  
 Um **longo** valor que pode ser um dos [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes que especifica o tipo de proprietário.  
  
 *OwnerName*  
 Um **cadeia de caracteres** valor que especifica a [nome](../../../ado/reference/adox-api/name-property-adox.md) dos [usuário](../../../ado/reference/adox-api/user-object-adox.md) ou [grupo](../../../ado/reference/adox-api/group-object-adox.md) ao proprietário do objeto.  
  
 *ObjectTypeId*  
 Opcional. Um **Variant** valor que especifica o GUID de um tipo de objeto de provedor que não é definido pela especificação do OLE DB. Esse parâmetro é necessário se *ObjectType* é definido como **adPermObjProviderSpecific**; caso contrário, ele não é usado.  
  
## <a name="remarks"></a>Comentários  
 Se o provedor não der suporte especificando os proprietários de objetos, ocorrerá um erro.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Consulte também  
 [GetObjectOwner e Setobjectowner (VB) métodos](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Método GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
