---
title: Exemplo de propriedades de DefaultDatabase (VC + +) e provedor | Microsoft Docs
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
- C++
helpviewer_keywords:
- provider property [ADO], VC++ example
- DefaultDatabase property [ADO], VC++ example
ms.assetid: d9868c99-425a-4b10-af67-1929ed513fda
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75bef2df222023fe54ec5c890b3321677f2a7a40
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="provider-and-defaultdatabase-properties-example-vc"></a>Exemplo de propriedades de DefaultDatabase (VC + +) e o provedor
Este exemplo demonstra o [provedor](../../../ado/reference/ado-api/provider-property-ado.md) propriedade abrindo três [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) objetos usando provedores diferentes. Ele também usa o [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md) propriedade para definir o banco de dados padrão para o provedor do Microsoft ODBC.  
  
```  
// Provider_and_DefaultDatabase_Properties.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void ProviderX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
  
   ProviderX();  
   ::CoUninitialize();  
}  
  
void ProviderX() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define. These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection1 = NULL;  
   _ConnectionPtr pConnection2 = NULL;  
   _ConnectionPtr pConnection3 = NULL;  
  
   try {  
      // Open a Connection using the Microsoft ODBC provider.  
      TESTHR(pConnection1.CreateInstance(__uuidof(Connection)));  
      pConnection1->ConnectionString = "DSN=Data;user id='MyUserId';password='MyPassword';";  
      pConnection1->Open("", "", "", adConnectUnspecified);  
      pConnection1->DefaultDatabase = "pubs";  
      // Display the provider  
      printf("\n\nConnection1 provider: %s \n\n", (LPCSTR)pConnection1->Provider);  
  
      // Open a connection using the OLE DB Provider for Microsoft Jet.  
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));  
      pConnection2->Provider = "Microsoft.Jet.OLEDB.4.0";  
  
      char *sConn = "c:\\Northwind.mdb";  
      pConnection2->Open(sConn, "admin", "", NULL);  
      // Display the provider  
      printf("Connection2 provider: %s \n\n",(LPCSTR)pConnection2->Provider);  
  
      // Requires SQL Server authentication  
      // Open a Connection using the Microsoft SQL Server provider.  
      TESTHR(pConnection3.CreateInstance(__uuidof(Connection)));  
      pConnection3->Provider = "sqloledb";  
      pConnection3->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", NULL);  
      // Display the provider.  
      printf("Connection3 provider: %s\n\n", (LPCSTR)pConnection3->Provider);  
   }  
  
   catch (_com_error &e) {  
      // Notify the user of errors if any.  
      PrintProviderError(pConnection1);  
      if (pConnection2)  
         PrintProviderError(pConnection2);  
  
      if (pConnection3)   
         PrintProviderError(pConnection3);  
  
      PrintComError(e);  
   }  
  
   if (pConnection1)  
      if (pConnection1->State == adStateOpen)  
         pConnection1->Close();  
  
   if (pConnection2)  
      if (pConnection2->State == adStateOpen)  
         pConnection2->Close();  
  
   if (pConnection3)  
      if (pConnection3->State == adStateOpen)  
         pConnection3->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print COM errors.   
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de Conexão (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Propriedade DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)   
 [Propriedade Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)