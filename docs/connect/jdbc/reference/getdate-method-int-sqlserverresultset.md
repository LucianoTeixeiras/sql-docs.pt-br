---
title: Método getDate (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e6b6cfe2-b7c4-4d41-8e09-c68b5086a503
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f434b15a49b607ad204b0d70c50381177b7743a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47725136"
---
# <a name="getdate-method-int-sqlserverresultset"></a>Método getDate (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o valor do índice da coluna designada na linha atual do objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) como um objeto java.sql.Date na linguagem de programação Java.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.Date getDate(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *columnIndex*  
  
 Um **int** que indica o índice de coluna.  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto de data.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método getDate é especificado pelo método getDate na interface java.sql.ResultSet.  
  
 Esse método retorna uma parte de data válida de um tipo de dados datetime ou smalldatetime do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], com a parte de hora definida como a linha de base de hora do Java de 00:00 (meia-noite).  
  
## <a name="see-also"></a>Consulte Também  
 [Método getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
