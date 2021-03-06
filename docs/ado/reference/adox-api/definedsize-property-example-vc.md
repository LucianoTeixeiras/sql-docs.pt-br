---
title: Exemplo da propriedade DefinedSize (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DefinedSize property [ADOX], VC++ example
ms.assetid: cc752ae4-58c4-4a7b-bfb2-0454e90fe2e7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c16f76e086dfc78ffed967ef33300a09630a798
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616594"
---
# <a name="definedsize-property-example-vc"></a>Exemplo da propriedade DefinedSize (VC++)
Este exemplo demonstra a [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) propriedade de uma [coluna](../../../ado/reference/adox-api/column-object-adox.md). O código irá redefinir o tamanho da coluna FirstName do **funcionários** tabela da *Northwind* banco de dados. Em seguida, a alteração nos valores de FirstName [campo](../../../ado/reference/ado-api/field-object.md) de uma [conjunto de registros](../../../ado/reference/ado-api/recordset-object-ado.md) com base no **funcionários** tabela é exibida. Observe que por padrão, o campo FirstName fica preenchido com espaços após você redefinir o **DefinedSize** propriedade.  
  
```  
// BeginDefinedSizeCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define ADOX object pointers, initialize pointers. These are in the ADODB namespace.  
   _CatalogPtr m_pCatNorthwind = NULL;  
   _ColumnPtr m_pColFirstName = NULL;  
   _ColumnPtr m_pColNewFirstName = NULL;  
  
   // Define ADODB object pointers  
   ADODB::_RecordsetPtr m_pRstEmployees = NULL;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");  
   _bstr_t aryFirstName[10];  
  
   try {  
      // Open a Recordset for the Employees table.  
      TESTHR(hr = m_pRstEmployees.CreateInstance(__uuidof(ADODB::Recordset)));  
      TESTHR(hr = m_pCatNorthwind.CreateInstance(__uuidof (Catalog)));  
      TESTHR(hr = m_pColNewFirstName.CreateInstance(__uuidof(Column)));  
  
      m_pRstEmployees->Open("Employees", strCnn,ADODB::adOpenKeyset, ADODB::adLockReadOnly, ADODB::adCmdTable);  
  
      long lngSize = m_pRstEmployees->RecordCount;  
      aryFirstName[lngSize];  
  
      // Open a catalog for the Northwind database, using same connection as rstEmployees.  
      m_pCatNorthwind->PutActiveConnection(m_pRstEmployees->GetActiveConnection());  
  
      // Loop through the recordset displaying the contents, of the FirstName field, the field's defined size,  
      // and its actual size.  Also store FirstName values in aryFirstName array.  
      m_pRstEmployees->MoveFirst();  
      printf("\nOriginal Defined Size and Actual Size");  
      int iCount = 0;  
      while (!(m_pRstEmployees->EndOfFile)) {  
         printf("\nEmployee Name:");  
         printf("%s ", (LPSTR)(_bstr_t)m_pRstEmployees->Fields->GetItem("FirstName")->Value);  
         printf("%s\n", (LPSTR)(_bstr_t)m_pRstEmployees->Fields->GetItem("LastName")->Value);  
         printf("  FirstName Defined size: %d\n", m_pRstEmployees->Fields->GetItem("FirstName")->DefinedSize);  
         printf("  FirstName Actual size: %d\n", m_pRstEmployees->Fields->GetItem("FirstName")->ActualSize);  
         aryFirstName[iCount] = (_bstr_t) m_pRstEmployees->Fields->GetItem("FirstName")->Value;  
         m_pRstEmployees->MoveNext();  
      }  
      m_pRstEmployees->Close();  
  
      // Redefine the DefinedSize of FirstName in the catalog.  
      m_pColFirstName = m_pCatNorthwind->Tables->GetItem("Employees")->Columns->GetItem("FirstName");  
      m_pColNewFirstName->Name = m_pColFirstName->Name;  
      m_pColNewFirstName->Type = m_pColFirstName->Type;  
      m_pColNewFirstName->DefinedSize = (m_pColFirstName->DefinedSize) + 1;  
  
      // Append new FirstName column to catalog.  
      m_pCatNorthwind->Tables->GetItem("Employees")->Columns->Delete(m_pColFirstName->Name);  
      m_pCatNorthwind->Tables->GetItem("Employees")->Columns->Append(_variant_t((IDispatch*)m_pColNewFirstName, true),   
         adVarWChar,  
         m_pColNewFirstName->DefinedSize);  
  
      // Open Employee table in Recordset for updating.  
      m_pRstEmployees->Open("Employees",  
         m_pCatNorthwind->GetActiveConnection(),   
         ADODB::adOpenKeyset,  
         ADODB::adLockOptimistic,  
         ADODB::adCmdTable);  
  
      // Loop through the recordset displaying the contents of the FirstName field,the field's defined size,  
      // and its actual size. Also restore FirstName values from aryFirstName.  
      m_pRstEmployees->MoveFirst();  
      printf("\n\nNew Defined Size and Actual Size");  
      iCount = 0;  
      while (!(m_pRstEmployees->EndOfFile)) {  
         m_pRstEmployees->Fields->GetItem("FirstName")->Value = aryFirstName[iCount];  
         printf("\nEmployee Name: ");  
         printf("%s ", (LPSTR) (_bstr_t)m_pRstEmployees->Fields->GetItem("FirstName")->Value);  
         printf("%s\n", (LPSTR)(_bstr_t)m_pRstEmployees->Fields->GetItem("LastName")->Value);  
         printf("  FirstName Defined size: %d\n", m_pRstEmployees->Fields->GetItem("FirstName")->DefinedSize);  
         printf("  FirstName Actual size: %d\n", m_pRstEmployees->Fields->GetItem("FirstName")->ActualSize);  
         m_pRstEmployees->MoveNext();  
      }  
      m_pRstEmployees->Close();  
  
      // Restore original FirstName column to catalog  
      m_pCatNorthwind->Tables->GetItem("Employees")->Columns->Delete(m_pColNewFirstName->Name);  
  
      m_pCatNorthwind->Tables->GetItem("Employees")->Columns->Append(_variant_t((IDispatch*)m_pColFirstName,   
         true),   
         adVarWChar,  
         m_pColFirstName->DefinedSize);  
  
      // Restore original FirstName values to Employees table.  
      m_pRstEmployees->Open("Employees",   
         m_pCatNorthwind->GetActiveConnection(),   
         ADODB::adOpenKeyset,   
         ADODB::adLockOptimistic,  
         ADODB::adCmdTable);  
  
      m_pRstEmployees->MoveFirst();  
      iCount = 0;  
      while ( !(m_pRstEmployees->EndOfFile) ) {  
         m_pRstEmployees->Fields->GetItem("FirstName")->Value = aryFirstName[iCount];  
         m_pRstEmployees->MoveNext();  
         iCount++;  
      }  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in DefinedSizeX...." << endl;  
   }  
  
   if (m_pRstEmployees)  
      if (m_pRstEmployees->State == 1)  
         m_pRstEmployees->Close();  
  
   m_pCatNorthwind = NULL;  
  
   ::CoUninitialize();  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Column (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Propriedade DefinedSize (ADOX)](../../../ado/reference/adox-api/definedsize-property-adox.md)
