---
title: Criar um administrador de entidades (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 717be1e8-488e-4219-8d1e-ca9084b864cd
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 14d2c5ca414281e8a3faf5b0fb627452503dd4d8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822220"
---
# <a name="create-an-entity-administrator-master-data-services"></a>Criar um Administrador de Entidade (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Em [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], crie um administrador de entidade quando você quiser que um grupo ou usuário tenha todas as permissões para todos os objetos em uma ou mais entidades ou tenha permissão para aprovar os conjuntos de alterações pendentes.  
  
> [!TIP]  
>  Para simplificar a administração, crie um grupo local ou do Windows e configure-o como um administrador de entidade. Isso lhe permitirá adicionar e remover usuários do grupo sem acessar o [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Permissões de Usuário e Grupo** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
## <a name="to-create-an-entity-administrator"></a>Para criar um Administrador de Entidade  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Permissões de Usuário e Grupo**.  
  
2.  Selecione a linha para o usuário ou grupo que você deseja editar, em seguida, clique em **Editar Usuário Selecionado**.  
  
3.  Clique na guia **Modelos** e, se quiser, escolha um modelo na lista **Modelos** e, em seguida, clique em **Editar**.  
  
4.  Clique na entidade à qual você deseja conceder permissões e, em seguida, clique em **Admin** no menu.  
  
5.  Conclua a etapa 4 para cada entidade para a qual o grupo ou o usuário deverá ser o administrador.  
  
6.  Clique em **Salvar**.  
  
## <a name="see-also"></a>Consulte Também  
 [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [Atribuir permissões de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Atribuir permissões de membro de hierarquia &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Permissões de objeto de modelo &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Permissões de membro de hierarquia &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
