---
title: Interface ADORecordConstruction | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21975fb2442aea97e362cd71b24c087f58addc0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686864"
---
# <a name="adorecordconstruction-interface"></a>Interface ADORecordConstruction
O **ADORecordConstruction**interface é usada para construir o ADO **registro** objeto a partir de um banco de dados OLE **linha** objeto em um aplicativo C/C++.  
  
 Esta interface dá suporte as seguintes propriedades:  
  
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Somente gravação.<br />Define o contêiner de um banco de dados OLE **linha** objeto esse ADO **registro** objeto.|  
|[linha](../../../ado/reference/ado-api/row-property-ado.md)|Leitura/gravação.<br />Obtém/define um banco de dados OLE **linha** objeto de/nesse ADO **registro** objeto.|  
  
## <a name="methods"></a>Métodos  
 Nenhum.  
  
## <a name="events"></a>Eventos  
 Nenhum.  
  
## <a name="remarks"></a>Comentários  
 Dado um banco de dados OLE **linha** objeto (`pRow`), a construção de ADO **registro** objeto (`adoR`), de valores para as três operações básicas a seguir:  
  
1.  Criar um ADO **registro** objeto:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Consulta a **IADORecordConstruction** interface sobre o **registro** objeto:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Chame o **IADORecordConstruction::put_Row** método de propriedade para definir o banco de dados OLE **linha** objeto ADO **registro** objeto:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 O resultante **objeto adoR** objeto agora representa o ADO **registro** objeto construído a partir do OLE DB **linha** objeto.  
  
 ADO **registro** objeto também pode ser construído a partir do contêiner de um banco de dados OLE **linha** objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Versão:** ADO 2.0 e posterior  
  
 **Biblioteca:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
