---
title: Classe SoapException do Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de33b2cdbc082e609e392d36aa53b8c5bbd2ce4f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160486"
---
# <a name="reporting-services-soapexception-class"></a>Classe SoapException do Reporting Services
  Você deve tratar de erros específicos do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] que sabe que podem acontecer. Por exemplo, em um aplicativo onde você solicita que o usuário crie uma pasta, pode ser possível que ele tente criar uma pasta que já exista. Como desenvolvedor, você não tem controle sobre o que o usuário digita no nome da pasta e nos campos de caminho do seu aplicativo, mas tem controle sobre o que o usuário experimenta quando alguém incidentalmente tenta criar um item já existente.  
  
 Para facilitar a captura de condições de erro específicas, o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifica um código de erro para a exceção e retorna a classificação do erro usando propriedades da classe **SoapException**. Para obter mais informações, consulte “Classe SoapException” na documentação do SDK do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 A tabela a seguir lista as propriedades públicas da classe **SoapException**.  
  
|Propriedade pública|Description|  
|---------------------|-----------------|  
|**Actor**|O código que causou a exceção. O valor é a URL para o método do serviço Web.|  
|**Detail**|Informações de erro específicas do aplicativo. O valor é definido pelo servidor de relatório e está em formato XML. Para obter mais informações, consulte [Propriedade Detail](detail-property.md) e [Usando a propriedade Detail para tratar erros específicos](../best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|Uma URL ou URN para um arquivo de Ajuda associado ao erro. O valor é normalmente definido pelo serviço Web e define uma URL como Ajuda e Suporte do [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Como o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dá suporte a diversos links de ajuda para erros ocorridos, o servidor de relatório define informações de link de ajuda como parte da propriedade **Detail**. Para obter mais informações, consulte [Elemento HelpLink](helplink-element.md).|  
|**Mensagem**|Uma mensagem descritiva e localizada que descreve o erro. Esse texto poderia aparecer na interface do usuário do aplicativo.|  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao tratamento de exceção no Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Tabela de erros de SoapException](soapexception-errors-table.md)  
  
  
