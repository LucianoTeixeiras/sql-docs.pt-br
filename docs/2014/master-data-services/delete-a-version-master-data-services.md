---
title: Excluir uma versão (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d75d6719219a41dfc42071a82375a66bdd877a57
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822997"
---
# <a name="delete-a-version-master-data-services"></a>Excluir uma versão (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclua uma versão quando tiver certeza de que já não precisa dos dados mestres associados à versão. Depois de excluir uma versão, você não poderá recuperar os dados mestres associados.  
  
> [!WARNING]  
>  Se um modelo tiver somente uma versão e você a excluir, ele se tornará inutilizável.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para ver a exibição mdm.viw_SYSTEM_SCHEMA_VERSION e executar o procedimento armazenado mds.udpVersionDelete no banco de dados do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Para obter mais informações, consulte [Segurança do objeto de banco de dados &#40;Master Data Services&#41;](database-object-security-master-data-services.md).  
  
### <a name="to-delete-a-version"></a>Para excluir uma versão  
  
1.  Abra o [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e conecte-se à instância do [!INCLUDE[ssDE](../includes/ssde-md.md)] de seu banco de dados do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Abra a exibição mdm.viw_SYSTEM_SCHEMA_VERSION.  
  
3.  Localize a versão do modelo que você deseja excluir e copie o valor no campo **ID** .  
  
4.  Crie uma nova consulta.  
  
5.  Digite o texto a seguir, substituindo *version_ID* pelo valor copiado na etapa 2.  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  Executa a consulta.  
  
    > [!NOTE]  
    >  Talvez seja necessário aguardar alguns minutos para que o aplicativo Web reflita a alteração.  
  
## <a name="see-also"></a>Consulte também  
 [Versões &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Copiar uma versão &#40;Master Data Services&#41;](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
