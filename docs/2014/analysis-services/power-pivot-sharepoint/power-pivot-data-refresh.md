---
title: Atualização de dados PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 29dce22921ec7922f97f7daa8c3a9d8f9e362a82
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210445"
---
# <a name="powerpivot-data-refresh"></a>Atualização de dados PowerPivot
  Depois de criar uma pasta de trabalho que contém dados PowerPivot, você pode atualizar os dados periodicamente executando novamente uma consulta ou um comando para obter informações atualizadas das origens usadas inicialmente para criar a pasta de trabalho. Esse processo é denominado `data refresh`, e você pode atualizar dados sob demanda no [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ou como uma operação agendada executada como um processo do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] em um servidor de aplicativo em um farm do SharePoint. Para obter mais informações, consulte:  
  
-   [Atualização de dados PowerPivot com SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Configurar o PowerPivot conta de atualização de dados autônoma &#40;PowerPivot para SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Configurar credenciais armazenadas para atualização de dados do PowerPivot do &#40;PowerPivot para SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Agendar uma atualização de dados &#40;PowerPivot para SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Exibir histórico de atualização de dados &#40;PowerPivot para SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  O [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e os Serviços do Excel do SharePoint Server 2013 usam uma arquitetura diferente para a atualização de dados dos modelos de dados PowerPivot. A arquitetura com suporte do SharePoint 2013 utiliza os Serviços do Excel como componente primário para carregar modelos de dados PowerPivot. A arquitetura de atualização de dados anterior utilizada baseava-se em um servidor que executava o Serviço do Sistema PowerPivot e o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no modo do SharePoint para carregar modelos de dados. Para obter mais informações, consulte o seguinte:  
> 
>  -   [Atualização de dados PowerPivot com SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Atualizar pastas de trabalho e a atualização de dados agendada &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
