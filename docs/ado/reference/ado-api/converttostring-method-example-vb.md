---
title: "Exemplo do método ConvertToString (VB) | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ConvertToString method [ADO], Visual Basic example
ms.assetid: 31731e4f-3c0c-451e-8cbc-c9df28fabf6c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 94c84810ba74671d27c4ffd98556b6aa2878e660
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="converttostring-method-example-vb"></a>Exemplo do método ConvertToString (VB)
```  
'BeginConvertToStringVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' to integrate this code replace the server name  
     ' in the CreateObject call  
  
     ' RDS variables  
    Dim rdsDS As RDS.DataSpace  
    Dim rdsDC As RDS.DataControl  
    Dim rdsDF As Object  
     ' recordset and connection variables  
    Dim rsAuthors As ADODB.Recordset  
    Dim strSQLAuthors As String  
    Dim strCnxn As String  
    Dim varString As Variant  
  
     ' Create a DataSpace object  
    Set rdsDS = New RDS.DataSpace  
     ' Create a DataFactory object  
    Set rdsDF = rdsDS.CreateObject("RDSServer.DataFactory", "http://MyServer") 'MyServer  
  
     ' Get all of the Author records  
  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    strSQLAuthors = "SELECT * FROM Authors"  
    Set rsAuthors = rdsDF.Query(strCnxn, strSQLAuthors)  
     ' Show results  
    Debug.Print "Old RDS recordset count:" & rsAuthors.RecordCount  
  
     ' Convert the recordset into a MIME formatted string  
    varString = rdsDF.ConvertToString(rsAuthors)  
    Debug.Print "Recordset as MIME format string:"  
    Debug.Print varString  
  
     ' Convert string value back into an ADO Recordset  
    Set rdsDC = New RDS.DataControl  
    rdsDC.SQL = varString  
    rdsDC.ExecuteOptions = adcExecSync  
    rdsDC.FetchOptions = adcFetchUpFront  
    rdsDC.Refresh  
     ' Show results  
    Debug.Print "New ADO recordset count:" & rdsDC.Recordset.RecordCount  
  
     ' clean up  
    rsAuthors.Close  
    Set rsAuthors = Nothing  
    Set rdsDC = Nothing  
    Set rdsDS = Nothing  
    Set rdsDC = Nothing  
  
ErrorHandler:  
  
    If Not rsAuthors Is Nothing Then  
        If rsAuthors.State = adStateOpen Then rsAuthors.Close  
    End If  
    Set rsAuthors = Nothing  
    Set rdsDC = Nothing  
    Set rdsDS = Nothing  
    Set rdsDC = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndConvertToStringVB  
```  
  
## <a name="see-also"></a>Consulte também  
 [Método ConvertToString (RDS)](../../../ado/reference/rds-api/converttostring-method-rds.md)   
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)