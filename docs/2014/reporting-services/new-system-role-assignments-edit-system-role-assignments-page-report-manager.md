---
title: 'Novas atribuições de função do sistema: Editar página de atribuições de função do sistema (Gerenciador de relatórios) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 26a2ca4499787fce12508e55bb5197b6f0c6f527
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053986"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a>Atribuições de nova função do sistema: página Editar atribuições de função do sistema (Gerenciador de Relatórios)
  Use a página Atribuição de Nova Função do Sistema ou Editar Atribuições de Função do Sistema para definir a segurança do servidor de relatório. Toda a segurança é definida por atribuições de função que mapeiam usuários específicos ou grupos até as tarefas que eles podem executar. A lista de tarefas é representada como uma definição de função que você seleciona ao fazer a atribuição da função.  
  
 No nível do sistema, as atribuições de função que você cria ou modifica se aplicam ao servidor de relatórios como um todo. Por exemplo, a capacidade de criar agendas compartilhadas é especificada no nível do sistema porque agendas compartilhadas são usadas em todo o sistema.  
  
 Por padrão, o Reporting Services fornece duas funções predefinidas de nível de sistema:  
  
-   A função Usuário do Sistema inclui tarefas que permitem aos usuários exibir as propriedades e as agendas compartilhadas do servidor de relatório, bem como executar definições de relatório, o que lhes permite exibir relatórios de clickthrough que foram publicados no servidor de relatório. A maioria dos usuários deve ter essa função atribuída.  
  
-   O Administrador de Sistema inclui tarefas para criar e gerenciar agendas compartilhadas, definir propriedades do servidor e criar atribuições de função de nível de sistema para outros usuários. Poucos usuários necessitam de permissões nesse nível.  
  
## <a name="navigation"></a>Navegação  
 Use o procedimento a seguir para navegar para este local na interface do usuário.  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a>Para abrir a página Atribuição de Nova Função do Sistema ou a página Editar Atribuições de Função do Sistema  
  
1.  Abra o Gerenciador de Relatórios.  
  
2.  Na parte superior da página, no canto direito, clique em **Configurações de Site**. Esse procedimento abre a página Propriedades Gerais do site.  
  
3.  Selecione a guia **Segurança** . Você deve ter permissões de Gerenciador de Conteúdo e de Administrador de Sistema para acessar essa página.  
  
4.  Para criar uma atribuição de nova função, clique em **Atribuição de Nova Função** na barra de ferramentas. Para editar uma atribuição de função existente, clique em **Editar** , ao lado de um grupo ou usuário na página de propriedades de Segurança.  
  
## <a name="options"></a>Opções  
 **Grupo ou usuário**  
 Digite o nome de uma conta de grupo ou usuário do seu domínio. Se o servidor de relatório estiver sendo executado em uma conta local, você deve especificar grupos ou usuários locais. Se o servidor de relatório estiver sendo executado em uma conta de domínio, você deverá especificar grupos ou usuários de domínio. Insira a conta neste formato: \<domínio >\\< conta\>.  
  
> [!NOTE]  
>  Esta caixa só está disponível na página Atribuição de Nova Função.  
  
 **Roles**  
 Fornece uma lista de funções no nível de sistema que você pode atribuir a outros usuários. Você pode especificar várias funções para uma única atribuição de função.  
  
 O Gerenciador de Relatórios não exibe as tarefas em cada função nem fornece um modo de adicionar ou modificar as tarefas. Você deve usar as funções como elas são definidas. Para criar, modificar, ou excluir funções, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Para obter mais informações, consulte [criar, excluir ou modificar uma função &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 Observe que, se você estiver usando [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] com Advanced Services, você deve usar as funções padrão que são fornecidas.  
  
 **Descrições**  
 Exibe informações adicionais sobre a função. Para funções predefinidas como Usuário do Sistema ou Administrador do Sistema, a descrição resume as tarefas às quais cada função dá suporte.  
  
 **Excluir atribuição de função**  
 Clique para excluir uma atribuição de função existente de um usuário ou grupo. Não será possível excluir uma atribuição de função se ela for a única que resta (cada item deve ter pelo menos uma atribuição de função).  
  
> [!NOTE]  
>  Este botão só está disponível na página Editar Atribuição de Função.  
  
## <a name="see-also"></a>Consulte também  
 [Ajuda de F1 do Gerenciador de relatórios](../../2014/reporting-services/report-manager-f1-help.md)   
 [Atribuições de função](security/role-assignments.md)   
 [Definições de função](security/role-definitions.md)  
  
  
