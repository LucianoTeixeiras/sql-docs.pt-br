---
title: Construtor SQLServerClob (SQLServerConnection, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd30a7f645aa4e8513056ed53c97587a45ccaae1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722914"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Construtor SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inicializa uma nova instância da classe [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md), quando for fornecido um objeto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) e uma cadeia de caracteres de dados.  
  
> [!NOTE]  
>  Esse método foi substituído no JDBC Driver versão 2.0. Em vez disso, use o método [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) da classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *conexão*  
  
 Um objeto SQLServerConnection.  
  
 *data*  
  
 Os dados CLOB.  
  
## <a name="see-also"></a>Consulte Também  
 [Construtores SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [Membros SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
