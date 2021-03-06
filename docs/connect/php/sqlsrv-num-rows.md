---
title: sqlsrv_num_rows | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- API Reference, sqlsrv_num_rows
- sqlsrv_num_rows
ms.assetid: c832210e-bb2a-47b5-a505-160b02d1d95e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 500e9e48d541c3f518dc6dec0e779b90c896ee9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640614"
---
# <a name="sqlsrvnumrows"></a>sqlsrv_num_rows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Informa o número de linhas em um conjunto de resultados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sqlsrv_num_rows( resource $stmt )  
```  
  
#### <a name="parameters"></a>Parâmetros  
*$stmt*: o conjunto de resultados cujas linhas serão contadas.  
  
## <a name="return-value"></a>Valor retornado  
**false** se houve um erro ao calcular o número de linhas. Caso contrário, representa o número de linhas no conjunto de resultados.  
  
## <a name="remarks"></a>Remarks  
sqlsrv_num_rows requer um cursor do lado do cliente, estático ou de conjunto de chaves e retornará **false** se você usar um cursor de avanço ou dinâmico. (O padrão é um cursor de avanço.) Para obter mais informações sobre os cursores, consulte [sqlsrv_query](../../connect/php/sqlsrv-query.md) e [Tipos de cursor &#40;Driver SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
## <a name="example"></a>Exemplo  
  
```  
<?php  
   $server = "server_name";  
   $conn = sqlsrv_connect( $server, array( 'Database' => 'Northwind' ) );  
  
   $stmt = sqlsrv_query( $conn, "select * from orders where CustomerID = 'VINET'" , array(), array( "Scrollable" => SQLSRV_CURSOR_KEYSET ));  
  
   $row_count = sqlsrv_num_rows( $stmt );  
  
   if ($row_count === false)  
      echo "\nerror\n";  
   else if ($row_count >=0)  
      echo "\n$row_count\n";  
?>  
```  
  
O exemplo a seguir mostra que quando há mais de um conjunto de resultados (uma consulta em lotes), o número de linhas é disponibilizado apenas quando um cursor do lado do cliente é usado.  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
$tsql = "select * from HumanResources.Department";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
// works  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
  
// fails  
// $stmt = sqlsrv_query($conn, $tsql);  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"forward"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"static"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"keyset"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"dynamic"));  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
?>  
```  
  
## <a name="see-also"></a>Consulte Também  
[Referência da API do driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
