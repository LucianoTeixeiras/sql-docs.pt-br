---
title: Adicionar e verificar uma conexão de dados (Construtor de Relatórios e SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6e49b55bb199ae64acb8cb12f87f06a2882a88f9
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50027805"
---
# <a name="add-and-verify-a-data-connection-report-builder-and-ssrs"></a>Adicionar e verificar uma conexão de dados (Construtor de Relatórios e SSRS)
  No Construtor de Relatórios, você pode adicionar uma fonte de dados compartilhada do servidor de relatório ou criar uma fonte de dados inserida no relatório. No Designer de Relatórios, você pode criar uma fonte de dados compartilhada ou uma fonte de dados inserida e implantá-la em um servidor de relatório.  
  
 Para adicionar uma fonte de dados compartilhada ao relatório, procure um servidor de relatório e selecione uma fonte de dados compartilhada. A fonte de dados compartilhada no seu relatório aponta para a definição de fonte de dados compartilhada no servidor de relatório.  
  
 Para criar uma fonte de dados inserida, você deve ter informações de conexão com a fonte de dados externa e deve saber quais permissões são necessárias para acessar os dados. Em geral, essas informações derivam do proprietário da fonte de dados. Você pode testar a conexão para verificar se as credenciais especificadas são suficientes.  
  
 Para obter mais informações, consulte [Conexões de dados, fontes de dados e cadeias de conexão no Construtor de Relatórios](https://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34) e [Especificar as credenciais no Construtor de Relatórios](https://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-connection-to-a-shared-data-source-in-report-builder"></a>Para criar uma conexão com uma fonte de dados compartilhada no Construtor de Relatórios  
  
1.  Na barra de ferramentas do painel Dados do Relatório, clique em **Nova** e em **Fonte de Dados**. A caixa de diálogo **Propriedades da Fonte de Dados** é aberta.  
  
2.  Na caixa de texto **Nome** , digite um nome para a fonte de dados.  
  
    > [!NOTE]  
    >  Esse é o nome salvo na definição de relatório local. Esse nome não é o nome da fonte de dados compartilhada no servidor de relatório.  
  
3.  Selecione **Usar uma conexão compartilhada ou modelo de relatório**. A lista de fontes de dados compartilhadas e modelos de relatório usados recentemente é exibida. Para selecionar uma em um servidor de relatório, clique em **Procurar** e procure a pasta no servidor de relatório em que as fontes de dados compartilhadas estão disponíveis.  
  
4.  Selecione a fonte de dados compartilhada e clique em **Abrir**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 A fonte de dados será exibida no painel de dados do relatório.  
  
### <a name="to-verify-a-data-connection"></a>Para verificar uma conexão de dados  
  
1.  Na barra de ferramentas no painel de dados do relatório, clique duas vezes na fonte de dados. A caixa de diálogo **Propriedades da Fonte de Dados** é aberta.  
  
2.  Clique em **Testar Conexão**.  
  
3.  Se a conexão for bem-sucedida, a seguinte mensagem aparecerá: Conexão criada com êxito". [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Se a conexão não for bem-sucedida, a seguinte mensagem aparecerá: "Não é possível conectar à fonte de dados".  
  
5.  Clique em **Detalhes**e use as informações para corrigir o problema.  
  
     Para obter mais informações, consulte [Especificar as credenciais no Construtor de Relatórios](https://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Consulte Também  
 [Conjuntos de dados de relatório &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Localizando, exibindo e gerenciando relatórios &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Conexões de dados, fontes de dados e cadeias de conexão no Construtor de Relatórios](https://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
  
  
