---
title: Método ownUpdatesAreVisible (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.ownUpdatesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eacbb1a8-ac9a-4f44-832e-ae0af476522e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99d7412a9864fc4a720ba48630e4c469db353c5c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842794"
---
# <a name="ownupdatesarevisible-method-sqlserverdatabasemetadata"></a>Método ownUpdatesAreVisible (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera se as próprias atualizações de um conjunto de resultados são visíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean othersUpdatesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *tipo*  
  
 Um inteiro que indica o tipo do conjunto de resultados, que pode ser um dos valores a seguir, conforme definido em java.sql.ResultSet ou SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Tipos java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Tipos SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Valor retornado  
 **True** se as atualizações são visíveis. Caso contrário, **false**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método ownUpdatesAreVisible é especificado pelo método ownUpdatesAreVisible na interface DatabaseMetadata.  
  
## <a name="see-also"></a>Consulte Também  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
