---
title: Implantações multilíngues e globais (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f69bea8e13780649203d154f475aca07bdc23acc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36011418"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>Implantações multilíngues e globais (Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] dá suporte à implantação de componentes e ferramentas em todos os idiomas com suporte pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter mais informações, consulte [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
## <a name="how-languages-are-used"></a>Como são usados os idiomas  
 A tabela a seguir descreve o suporte de idiomas para os componentes e as ferramentas do [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|Componente ou ferramenta|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Instalação|Selecione o programa de Instalação em Inglês quando você quiser que o aplicativo Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] esteja disponível e tenha suporte em idiomas diferentes do idioma de Instalação. Para obter mais informações, consulte a descrição de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] abaixo.|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|O idioma de Instalação determina o idioma do [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Por exemplo, se você escolher alemão como o idioma de Instalação, o [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] estará disponível em alemão nesse computador.|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|Quando você executa a Instalação em inglês, o aplicativo Web do [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] está disponível e tem suporte em todos os idiomas do aplicativo. [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] pode ser exibido em qualquer idioma de aplicativo e aceita entradas de localidades específicas com base nas preferências de idioma do navegador da Web do cliente. Se as preferências de idioma forem configuradas para um idioma de aplicativo sem suporte, o [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] padronizará para o inglês.<br /><br /> Quando você executar a Instalação em um idioma diferente do inglês, recursos serão incluídos para todos os demais idiomas do aplicativo, mas esse não é um cenário com suporte para que os clientes usem o [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] em um idioma diferente do idioma de Instalação selecionado. Se você tentar acessar o [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] em um idioma diferente do idioma de Instalação, talvez tenha problemas com a exibição e a entrada de dados no aplicativo.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] banco de dados|As informações no banco de dados do [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] não são específicas para nenhuma localidade. Isso permite que o [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] determine como exibir informações, como datas e números, no formato determinado pelas preferências de idioma do navegador da Web do cliente.|  
  
## <a name="see-also"></a>Consulte também  
 [Instalar o Master Data Services](install-master-data-services.md)  
  
  