---
title: Propriedade DateModified (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02731da2b023b7230b3407e0eb386fe8e5aaaf87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786304"
---
# <a name="datemodified-property-adox"></a>Propriedade DateModified (ADOX)
Indica a data em que o objeto foi modificado pela última vez.  
  
## <a name="return-values"></a>Valores de retorno  
 Retorna um **Variant** valor que especifica a data de modificação. O valor é null se **DateModified** não tem suporte pelo provedor.  
  
## <a name="remarks"></a>Comentários  
 O **DateModified** propriedade é nula para objetos acrescentados recentemente. Depois de anexar um novo [modo de exibição](../../../ado/reference/adox-api/view-object-adox.md) ou [procedimento](../../../ado/reference/adox-api/procedure-object-adox.md), você deve chamar o [atualizar](../../../ado/reference/ado-api/refresh-method-ado.md) o método da [exibições](../../../ado/reference/adox-api/views-collection-adox.md) ou [procedimentos ](../../../ado/reference/adox-api/procedures-collection-adox.md) coleção para obter valores para o **DateModified** propriedade.  
  
## <a name="applies-to"></a>Aplica-se a  
  
||||  
|-|-|-|  
|[Objeto Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Objeto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Objeto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Consulte também  
 [DateCreated e DateModified (VB) propriedades](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Propriedade DateCreated (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
