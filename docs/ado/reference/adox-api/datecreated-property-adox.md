---
title: Propriedade DateCreated (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46c6017f7b0c9bbeeb654c2cf6aa3965aafff8e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747584"
---
# <a name="datecreated-property-adox"></a>Propriedade DateCreated (ADOX)
Indica a data em que o objeto foi criado.  
  
## <a name="return-values"></a>Valores de retorno  
 Retorna um **Variant** valor que especifica a data de criação. O valor é null se **DateCreated** não tem suporte pelo provedor.  
  
## <a name="remarks"></a>Comentários  
 O **DateCreated** propriedade é nula para objetos acrescentados recentemente. Depois de anexar um novo [modo de exibição](../../../ado/reference/adox-api/view-object-adox.md) ou [procedimento](../../../ado/reference/adox-api/procedure-object-adox.md), você deve chamar o [atualizar](../../../ado/reference/ado-api/refresh-method-ado.md) o método da [exibições](../../../ado/reference/adox-api/views-collection-adox.md) ou [procedimentos ](../../../ado/reference/adox-api/procedures-collection-adox.md) coleção para obter valores para o **DateCreated** propriedade.  
  
## <a name="applies-to"></a>Aplica-se a  
  
||||  
|-|-|-|  
|[Objeto Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Objeto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Objeto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Consulte também  
 [DateCreated e DateModified (VB) propriedades](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Propriedade DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
