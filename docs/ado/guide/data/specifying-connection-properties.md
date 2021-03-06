---
title: Especificar as propriedades de Conexão | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection properties [ADO]
- connections [ADO]
ms.assetid: 49456201-b085-4851-9686-e814136b07be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 885d201736adb3cd16efbea4f3907cd0aa324128
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622754"
---
# <a name="specifying-connection-properties"></a>Especificar propriedades de conexão
Você pode fornecer muitas das informações especificadas por um [cadeia de caracteres de conexão](../../../ado/guide/data/creating-a-connection-string.md) definindo propriedades da **Conexão** objeto antes de abrir a conexão. Por exemplo, você pode obter o mesmo efeito como a cadeia de caracteres de conexão é discutido em [criando uma cadeia de Conexão](../../../ado/guide/data/creating-a-connection-string.md) usando o código a seguir.  
  
```  
With objConn  
.Provider = "SQLOLEDB"  
.Properties("Data Source") = "MySqlServer"  
   .Properties("Integrated Security") = "SSPI"  
.Open  
.DefaultDatabase = "Northwind"  
End With  
```  
  
 DefaultDatabase é definido apenas depois de abrir a conexão.  
  
> [!NOTE]
>  No ADO, você não deve usar uma senha que contenha ponto e vírgula (";"), a menos que a senha é colocada entre aspas simples.
