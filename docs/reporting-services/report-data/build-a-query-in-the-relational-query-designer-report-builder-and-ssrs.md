---
title: Compilar uma consulta no designer de consultas relacionais (Construtor de Relatórios e SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 28b25861-f3b4-4c3e-a9b0-03d6e4cfea26
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9c2e626cb890343f42095a1702942a5aefc37a75
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021652"
---
# <a name="build-a-query-in-the-relational-query-designer-report-builder-and-ssrs"></a>Compilar uma consulta no designer de consulta relacional (Construtor de Relatórios e SSRS)
  Um designer de consulta ajuda a especificar quais dados devem ser recuperados de uma fonte de dados externa para um conjunto de dados de relatório. Você usa um designer de consulta quando compila uma consulta em um assistente ou cria uma consulta de conjunto de dados.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Um conjunto de dados se baseia em uma fonte de dados. O tipo de fonte de dados e o ambiente de criação determinam qual designer de consulta é aberto quando você define a consulta de conjunto de dados. Os recursos do designer de consulta variam de acordo com a fonte de dados subjacente. Para obter mais informações sobre as camadas de dados, consulte [Conexões de dados, fontes de dados e cadeias de conexão no Construtor de Relatórios](https://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34) ou [Conexões de dados, fontes de dados e cadeias de conexão &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 É possível usar um designer de consulta para as seguintes tarefas:  
  
-   Explorar os metadados de vários esquemas na fonte de dados externa  
  
-   Especificar campos a serem recuperados para o conjunto de dados  
  
-   Especificar relações entre dois objetos, como tabelas  
  
-   Especificar filtros para restringir os dados antes de serem recuperados como dados de relatório  
  
-   Indicar se é necessário criar parâmetros  
  
-   Especificar agregações para executar cálculos na fonte de dados externa  
  
 Depois de abrir um designer de consulta, você cria uma consulta da mesma forma para um conjunto de dados inserido ou um compartilhado. Os procedimentos a seguir usam uma consulta do conjunto de dados inserida.  
  
 Para obter mais informações, consulte [Interface do usuário do Designer de Consultas Relacionais &#40;Construtor de Relatórios&#41;](../../reporting-services/report-data/relational-query-designer-user-interface-report-builder.md).  
  
### <a name="to-build-a-query-for-an-embedded-dataset-in-report-design-view"></a>Para compilar uma consulta para um conjunto de dados inserido na exibição Design do Relatório  
  
1.  Abra o designer de consulta. No painel Dados do Relatório, clique com o botão direito do mouse no conjunto de dados e clique em **Consulta**.  
  
     O designer de consulta associado à fonte de dados é aberto.  
  
2.  No painel de exibição Banco de dados, expanda as pastas que mostrem uma exibição hierárquica dos objetos de esquema de banco de dados, como tabelas, exibições e procedimentos armazenados. Clique na caixa de seleção para selecionar todos os campos para um objeto ou expanda o nó para selecionar campos individuais.  
  
     À medida que você seleciona campos no painel de exibição Banco de Dados, o painel **Selecionar campos** exibe suas seleções.  
  
     Se você selecionar campos de mais de uma tabela de banco de dados relacionada, use o painel Relações para exibir as relações de tabelas detectadas no esquema de banco de dados.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     A lista de campos do conjunto de dados é exibida no painel de dados do relatório.  
  
### <a name="to-specify-limits-for-a-query"></a>Para especificar limites para uma consulta  
  
1.  No designer de consultas relacionais, verifique se você tem campos selecionados e se os campos são exibidos no painel **Campos selecionados** .  
  
2.  Na barra de ferramentas do painel Filtros aplicados, clique em **Adicionar Filtro**. Uma nova linha de filtro é exibida.  
  
3.  Em **Nome do campo**, clique para exibir a lista suspensa de campos e clique no nome do campo pelo qual você deseja filtrar. Por exemplo, para filtrar por quantidade, clique no campo que contém o número de itens.  
  
4.  Em **Operador**, clique para exibir a lista suspensa de operadores e selecione o operador de comparação a ser usado no filtro.  
  
5.  Em **Valor**, digite o valor pelo qual você deseja filtrar. Por exemplo, para filtrar quantidade maior que 100, digite 100.  
  
6.  Selecione a opção de parâmetro nessa linha para criar um parâmetro de conjunto de dados e permitir a um usuário especificar um valor de filtro. Um parâmetro de relatório correspondente ao parâmetro do conjunto de dados é criado automaticamente.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 A lista de campos do conjunto de dados é exibida no painel de dados do relatório.  
  
### <a name="to-view-a-query-result-set"></a>Para exibir um conjunto de resultados da consulta  
  
1.  Na barra de ferramentas do designer de consultas, clique em **Executar Consulta (!)**.  
  
    > [!NOTE]  
    >  O designer de consulta usa credenciais do momento do design para executar a consulta e recuperar o conjunto de resultados. Para obter mais informações, consulte [Especificar as credenciais no Construtor de Relatórios](https://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53).  
  
 A consulta é executada na fonte de dados e retorna dados de exemplo no painel de resultados Consulta.  
  
## <a name="see-also"></a>Consulte Também  
 [Conjuntos de dados de relatório &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Adicionar dados de fontes de dados externas &#40;SSRS&#41;](../../reporting-services/report-data/add-data-from-external-data-sources-ssrs.md)   
 [Designers de Consultas &#40;Construtor de Relatórios&#41;](https://msdn.microsoft.com/library/553f0d4e-8b1d-4148-9321-8b41a1e8e1b9)   
 [Criar um conjunto de dados compartilhado ou um conjunto de dados inserido &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Modo de exibição de Design de relatório &#40;Construtor de Relatórios&#41;](../../reporting-services/report-builder/report-design-view-report-builder.md)   
 [Modo de exibição de Design de conjunto de dados compartilhados &#40;Construtor de Relatórios&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Designers de Consultas do Reporting Services](https://msdn.microsoft.com/library/07efd3f1-804f-45f7-b62a-3e727a3d9835)  
  
  
