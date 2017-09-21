---
title: sqlsrv_query | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1dbc5c20a1d9fb1210bb7729f36299ea4392ebc
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prepara e executa uma instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sqlsrv_query( resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Parâmetros  
*$conn*: o recurso de conexão associado à instrução preparada.  
  
*$tsql*: expressão Transact-SQL que corresponde à instrução preparada.  
  
*$params* [opcional]: uma **matriz** de valores que correspondem aos parâmetros em uma consulta parametrizada. Cada elemento da matriz pode ser um dos seguintes:  
  
-   Um valor literal.  
  
-   Uma variável do PHP.  
  
-   Uma **matriz** com a seguinte estrutura:  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    A descrição de cada elemento da matriz está na tabela abaixo:  
  
    |Elemento|Descrição|  
    |-----------|---------------|  
    |*$value*|Um valor literal, uma variável do PHP ou uma variável do PHP por referência.|  
    |*$direction*[opcional]|Um dos seguintes **SQLSRV_PARAM _\* ** constantes usadas para indicar a direção do parâmetro: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. O valor padrão é **SQLSRV_PARAM_IN**.<br /><br />Para obter mais informações sobre constantes do PHP, consulte [constantes &#40; Drivers da Microsoft para PHP para SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[opcional]|Um **SQLSRV_PHPTYPE _\* ** constante que especifica o tipo de dados do PHP do valor retornado.<br /><br />Para obter mais informações sobre constantes do PHP, consulte [constantes &#40; Drivers da Microsoft para PHP para SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[opcional]|Um **SQLSRV_SQLTYPE _\* ** constante que especifica o tipo de dados do SQL Server do valor de entrada.<br /><br />Para obter mais informações sobre constantes do PHP, consulte [constantes &#40; Drivers da Microsoft para PHP para SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [opcional]: uma matriz associativa que define as propriedades de consulta. As chaves com suporte são as seguintes:  
  
|Chave|Valores com suporte|Descrição|  
|-------|--------------------|---------------|  
|QueryTimeout|Um valor inteiro positivo.|Define o tempo limite da consulta em segundos. Por padrão, o driver aguardará resultados indefinidamente.|  
|SendStreamParamsAtExec|**true** ou **false**<br /><br />O valor padrão é **true**.|Configura o driver para enviar todos os dados de fluxo na execução (**true**), ou para enviar dados de fluxo em partes (**false**). Por padrão, o valor é definido como **true**. Para obter mais informações, consulte [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Rolável|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Para obter mais informações sobre esses valores, consulte [Especificando um tipo de cursor e selecionando linhas](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Valor de retorno  
Um recurso de instrução. Se a instrução não pode ser criada e/ou executada, **false** é retornado.  
  
## <a name="remarks"></a>Comentários  
O **sqlsrv_query** função é adequada para consultas únicas e deve ser a opção padrão para executar consultas, a menos que circunstâncias especiais se apliquem. Essa função fornece um método simplificado para executar uma consulta com uma quantidade mínima de código. A função **sqlsrv_query** realiza a preparação e a execução da instrução e pode ser usada para executar consultas parametrizadas.  
  
Para obter mais informações, consulte [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Exemplo  
No exemplo a seguir, uma única linha é inserida na tabela *Sales.SalesOrderDetail* do banco de dados AdventureWorks. O exemplo supõe que o SQL Server e o banco de dados [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) estejam instalados no computador local. Toda a saída será gravada no console quando o exemplo for executado da linha de comando.  
  
> [!NOTE]  
> Embora o exemplo a seguir usa uma instrução INSERT para demonstrar o uso de **sqlsrv_query** para a execução de uma instrução única, o conceito se aplica a qualquer instrução Transact-SQL.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Row successfully inserted.\n";  
}  
else  
{  
     echo "Row insertion failed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir atualiza um campo na tabela *Sales.SalesOrderDetail* do banco de dados AdventureWorks. O exemplo supõe que o SQL Server e o banco de dados [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) estejam instalados no computador local. Toda a saída será gravada no console quando o exemplo for executado da linha de comando.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Assign literal parameter values. */  
$params = array( 5, 10);  
  
/* Execute the query. */  
if( sqlsrv_query( $conn, $tsql, $params))  
{  
      echo "Statement executed.\n";  
}   
else  
{  
      echo "Error in statement execution.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[Referência da API do driver JDBC](../../connect/php/sqlsrv-driver-api-reference.md)  
[Como executar consultas parametrizadas](../../connect/php/how-to-perform-parameterized-queries.md)  
[Sobre exemplos de código na documentação](../../connect/php/about-code-examples-in-the-documentation.md)  
[Como enviar dados como um fluxo](../../connect/php/how-to-send-data-as-a-stream.md)  
[Usando parâmetros direcionais](../../connect/php/using-directional-parameters.md)  
  
