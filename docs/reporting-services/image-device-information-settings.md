---
title: Configurações de informações de dispositivo de imagem | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b59fcf947a283ef60f5dd34f60e2cf365092cfa7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738724"
---
# <a name="image-device-information-settings"></a>Configurações das informações do dispositivo do Image
  A tabela a seguir lista as configurações de informações de dispositivo para renderização no formato do IMAGE.  
  
|Configuração|Valor|  
|-------------|-----------|  
|**Colunas**|O número de colunas a ser definido para o relatório. Esse valor substitui as configurações originais do relatório.|  
|**ColumnSpacing**|O espaçamento entre colunas a ser definido para o relatório. Esse valor substitui as configurações originais do relatório.|  
|**DpiX**|A resolução horizontal da imagem de saída. O valor padrão é **96**. Aplica-se aos formatos de saída **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**DpiY**|A resolução vertical da imagem de saída. O valor padrão é **96**. Aplica-se aos formatos de saída **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**EndPage**|A última página do relatório a ser renderizado. O valor padrão é o valor de **StartPage**.|  
|**MarginBottom**|O valor da margem inferior, em polegadas, a ser definido para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **1in**). Esse valor substitui as configurações originais do relatório.|  
|**MarginLeft**|O valor da margem esquerda, em polegadas, a ser definido para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **1in**). Esse valor substitui as configurações originais do relatório.|  
|**MarginRight**|O valor da margem direita, em polegadas, a ser definido para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **1in**). Esse valor substitui as configurações originais do relatório.|  
|**MarginTop**|O valor da margem superior, em polegadas, a ser definido para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **1in**). Esse valor substitui as configurações originais do relatório.|  
|**OutputFormat**|Um dos formatos de saída de [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) com suporte: **BMP**, **EMF**, **GIF**, **JPEG**, **PNG**ou **TIFF**.|  
|**PageHeight**|A altura da página, em polegadas, a ser definida para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **11in**). Esse valor substitui as configurações originais do relatório.|  
|**PageWidth**|A largura da página, em polegadas, a ser definida para o relatório. Inclua um valor inteiro ou um decimal seguido de "in" (por exemplo, **8,5in**). Esse valor substitui as configurações originais do relatório.|  
|**PrintDpiX**|A resolução horizontal da imagem de saída. O valor padrão é **300**. Aplica-se ao formato de saída de metarquivo avançado (**EMF**).|  
|**PrintDpiY**|A resolução vertical da imagem de saída. O valor padrão é **300**. Aplica-se ao formato de saída de metarquivo avançado (**EMF**).|  
|**StartPage**|A primeira página do relatório a ser renderizada. O valor **0** indica que todas as páginas serão renderizadas. O valor padrão é **1**.|  
  
## <a name="see-also"></a>Consulte Também  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passando configurações de informações de dispositivos para extensões de renderização](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar parâmetros de extensão de renderização em RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referência técnica &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
