---
title: Usando a propriedade Detail para tratar erros específicos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1966cd4898731b5176541a8dd0707bf0deef25bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222876"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Usando a propriedade Detail para manipular erros específicos
  Para classificar ainda mais as exceções, o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] retorna informações de erro adicionais na propriedade **InnerText** dos elementos filho da propriedade **Detail** da exceção SOAP. Como a propriedade **Detail** é um objeto **XmlNode**, você pode acessar o texto interno do elemento filho **Message** usando o código a seguir.  
  
 Para obter uma lista de todos os elementos filho disponíveis contidos na propriedade **Detail**, consulte [Propriedade Detail](../soapexception-class/detail-property.md). Para obter mais informações, consulte “Propriedade Detail” na documentação do SDK do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 A linha de código a seguir grava o código de erro específico retornado na Exceção SOAP para o console. Você também pode avaliar o código de erro e executar ações específicas.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao tratamento de exceção no Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException do Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)   
 [Tabela de erros de SoapException](../soapexception-class/soapexception-errors-table.md)  
  
  
