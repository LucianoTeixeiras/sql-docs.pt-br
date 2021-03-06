---
title: Carregamento de dados (suplemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 465b14ab5cb96f3f587222427ea793bbaf225b01
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762398"
---
# <a name="loading-data-mds-add-in-for-excel"></a>Carregando dados (suplemento MDS para Excel)
  No [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], você deve carregar dados do repositório do MDS em uma planilha ativa do Excel antes de poder trabalhar com ele. Quando você terminar o trabalho com os dados, publique-o no repositório do MDS para que outros usuários possam compartilhá-lo.  
  
 Os dados carregados são limitados àqueles que você tem permissão para acessar. A permissão para acessar os dados é definida no aplicativo Web do [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] ou programaticamente.  
  
 Ao carregar grandes quantidades de dados, você pode definir os avisos que são exibidos quando os dados podem demorar muito tempo para carregar. Para fazer isso, no grupo **Opções** , clique em **Configurações**. Na guia **Dados** , selecione **Exibir aviso de filtro para grandes conjuntos de dados**.  
  
> [!WARNING]  
>  Uma pasta de trabalho habilitada para MDS deve ser aberta e atualizada somente no Excel com o Suplemento de MDS para Excel. Abrir uma pasta de trabalho habilitada para MDS no Excel em um computador no qual o Suplemento do Excel do MDS não está instalado não tem suporte e pode causar corrupção do arquivo da pasta de trabalho. Se você quiser compartilhar dados com outra pessoa, envie por email um arquivo de consulta de atalho, em vez de salvar a planilha e enviá-la por email. Para obter mais informações sobre a consulta, consulte [Enviar um arquivo de consulta de atalho por email &#40;Suplemento MDS para Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Filtrando dados  
 Você pode filtrar dados antes de carregar para limitar a quantidade de dados que você vai fazer o download. Isso inclui a seleção dos atributos (colunas) que você deseja carregar, a ordem em que deseja exibir os atributos e os membros (linhas de dados) com os quais deseja trabalhar. Para obter mais informações, consulte [filtrar dados antes de carregar &#40;suplemento MDS para Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Conectar-se automaticamente e carregar dados usados frequentemente  
 Se você desejar conectar-se sempre ao mesmo servidor e carregar o mesmo conjunto de dados, poderá criar arquivos de consulta de atalho que contenham informações de conexão e de filtro. Para obter mais informações sobre arquivos de consulta, consulte [Arquivos de consulta de atalho &#40;Suplemento MDS para Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Atualizando dados  
 Os dados do repositório do MDS poderão ser atualizados por outros usuários depois que você carregá-los. Você pode recuperar esses dados sem perder as alterações feitas nos dados não MDS. Para obter mais informações, consulte [Atualizando dados &#40;Suplemento MDS para Excel&#41;](refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Filtre os dados do MDS antes de carregá-los no Excel.|[Filtrar dados antes de carregar &#40;suplemento do MDS para Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Carregue os dados do MDS no Excel.|[Carregar dados do MDS no Excel](export-data-to-excel-from-master-data-services.md)|  
|Altere a ordem das colunas antes de baixar os dados.|[Reordenar colunas &#40;Suplemento MDS para Excel&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Conteúdo relacionado  
  
-   [Conexões &#40;Suplemento MDS para Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Arquivos de consulta de atalho &#40;Suplemento MDS para Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Suplemento do Master Data Services para Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Segurança &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
