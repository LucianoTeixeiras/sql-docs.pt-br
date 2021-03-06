---
title: Criar um conjunto de alterações (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: bd8bd63f7fa3bb2d674076ae7780a132a916e7a1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753578"
---
# <a name="create-a-changeset-master-data-services"></a>Criar um Conjunto de Alterações (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Um conjunto de alterações é uma coleção das alterações pendentes nos dados mestre. Se a entidade requer aprovação para alterações, as alterações pendentes devem ser salvas em um conjunto de alterações e, em seguida, enviadas para aprovação do administrador.  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   Você deve ter permissão para acessar a área funcional do Gerenciador. Para obter mais informações, consulte [Permissões de área funcional &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)  
  
-   Você deve ter pelo menos o acesso de leitura para a entidade ou um de seus atributos.  
  
## <a name="to-create-a-local-changeset"></a>Para criar um conjunto de alterações local  
  
1.  Na home page do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , selecione o modelo e a versão e clique em **Gerenciador**.  
  
2.  Clique em uma entidade no menu **Entidades** .  
  
3.  No painel direito, escolha **Conjuntos de Alterações** e clique em **Criar**.  
  
4.  Insira um nome para o conjunto de alterações e clique em **Salvar**.  
  
     O nome do conjunto de alterações deve ser exclusivo dentro de um modelo.  
  
## <a name="to-create-a-changeset-for-approval"></a>Para criar um conjunto de alterações para aprovação  
  
1.  Na home page do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , selecione o modelo e a versão e clique em **Gerenciador**.  
  
2.  Clique em uma entidade no menu **Entidades** .  
  
3.  Faça alterações na entidade e clique em**OK**.  
  
4.  **Escolher um Conjunto de Alterações** será exibida.  
  
5.  Clique em **Novo**, insira um nome para o conjunto de alterações e clique em **Salvar**. O nome do conjunto de alterações deve ser exclusivo dentro de um modelo.  
  
6.  Para usar um conjunto de alterações existente, clique em **Existente** e escolha o conjunto de alterações na lista. Somente conjuntos de alterações que estão em um estado aberto ou rejeitado estão disponíveis.  
  
## <a name="next-steps"></a>Next Steps  
 [Aplicar e atualizar um conjunto de alterações &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Confirmar ou enviar um conjunto de alterações &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Aprovar ou rejeitar um conjunto de alterações &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
