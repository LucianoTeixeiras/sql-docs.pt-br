---
title: Método getCatalogs (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2792bd3a13be5ceb4ee8965065f6c6619f389d22
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601227"
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>Método getCatalogs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera os nomes de catálogo disponíveis no servidor conectado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 O método getCatalogs é especificado pelo método getCatalogs na interface java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  No SQL Azure, você deve se conectar ao banco de dados mestre para chamar **sqlserverdatabasemetadata. GetCatalogs**. O SQL Azure não é compatível com o retorno de todo o conjunto de catálogos de um banco de dados do usuário. **Sqlserverdatabasemetadata. GetCatalogs** usa a exibição de sys. Databases para obter os catálogos. Consulte a discussão de permissões no [sys. Databases (banco de dados do SQL Azure)](https://go.microsoft.com/fwlink/?LinkId=217396) entender **sqlserverdatabasemetadata. GetCatalogs** comportamento no SQL Azure.  
  
 O conjunto de resultados retornado pelo método getCatalogs conterá as seguintes informações:  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|O nome do catálogo, inclusive bancos de dados do sistema no [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o método getCatalogs para retornar os nomes de todos os bancos de dados que estão contidos no [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], inclusive os bancos de dados do sistema.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membros SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
