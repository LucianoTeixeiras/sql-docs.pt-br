---
title: Método Close (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec9b51d08e10df0f829308d163b573c0670c78e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637254"
---
# <a name="close-method-sqlserverresultset"></a>Método close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Libera imediatamente o banco de dados e os recursos do JDBC do objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), em vez de aguardar que isso aconteça quando ele for fechado automaticamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método close é especificado pelo método close na interface java.sql.ResultSet.  
  
 Um objeto SQLServerResultSet será fechado automaticamente pelo objeto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) que o gerou quando aquele objeto SQLServerStatement objeto for fechado, reexecutado ou usado para recuperar o próximo resultado de uma sequência de vários resultados. Um objeto SQLServerResultSet também é fechado automaticamente quando é coletado como lixo.  
  
 Ao executar uma instrução que produz um único conjunto de resultados grande, apenas de encaminhamento, somente leitura, você pode estar interessado apenas em algum conjunto inicial de linhas no conjunto de resultados retornado. Nesse caso, o aplicativo pode chamar o método [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) do objeto de instrução associado antes de fechar o conjunto de resultados, para minimizar o tempo de processamento necessário para descartar as linhas desnecessárias restantes. Ao decidir se essa técnica será usada ou não, é recomendável considerar a compensação entre o tempo de processamento que seria economizado e o tempo e a viagem de ida e volta adicional ao servidor, necessários para cancelar a execução.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
