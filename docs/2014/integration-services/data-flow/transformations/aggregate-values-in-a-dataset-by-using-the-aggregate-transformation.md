---
title: Agregar valores em um conjunto de dados por meio da transformação Agregação | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3004bf8173756b291db1eb4ef99cfdcd7c8afdcc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818021"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a>Agregar valores em um conjunto de dados por meio da transformação Agregação
  Para adicionar e configurar uma transformação de Agregação, o pacote já deve incluir pelo menos uma tarefa de Fluxo de Dados e uma origem.  
  
### <a name="to-aggregate-values-in-a-dataset"></a>Para agregar valores em um conjunto de dados  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra o projeto do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contém o pacote desejado.  
  
2.  No Gerenciador de Soluções, clique duas vezes no pacote para abri-lo.  
  
3.  Clique na guia **Fluxo de Dados** e na **Caixa de Ferramentas**, arraste a transformação Agregação para a superfície de design.  
  
4.  Conecte a transformação Agregação ao fluxo de dados arrastando um conector da fonte ou transformação anterior para a transformação Agregação.  
  
5.  Clique duas vezes na transformação.  
  
6.  Na caixa de diálogo **Editor da Transformação Agregação** , clique na guia **Agregações** .  
  
7.  Na lista **Colunas de Entrada Disponíveis** , marque a caixa de seleção ao lado das colunas nas quais deseja agregar os valores. As colunas selecionadas aparecem na tabela.  
  
    > [!NOTE]  
    >  É possível selecionar uma coluna diversas vezes, aplicando diversas transformações à coluna. Para identificar exclusivamente as agregações, um número é anexado ao nome padrão do alias de saída da coluna.  
  
8.  Como opção, modifique o valor nas colunas **Alias de Saída** .  
  
9. Para alterar a operação de agregação padrão, **Agrupar por**selecione uma operação diferente na lista **Operação** .  
  
10. Para alterar a comparação padrão, selecione os sinalizadores de comparação individuais listados na coluna **Sinalizadores de Comparação** . Por padrão, uma comparação ignora a diferença entre maiúsculas e minúsculas, tipo kana, caracteres sem-espaçamento e largura do caractere.  
  
11. Como opção, para a agregação **Distinção de contagem** , especifique um número exato de valores distintos na coluna **Chaves de Distinção de Contagem** ou selecione uma contagem aproximada na coluna **Escala de Distinção de Contagem** .  
  
    > [!NOTE]  
    >  O fornecimento do número de valores distintos, exato ou aproximado, melhora o desempenho, pois a transformação pode alocar antecipadamente uma quantidade da memória para fazer seu trabalho.  
  
12. Como opção, clique em **Avançado** e atualize o nome da saída da transformação Agregação. Se as agregações incluirem uma `Group By` operação, você pode selecionar uma contagem aproximada de agrupamento de valores de chave em de **escala de chaves** coluna ou especifique um número exato de agrupamento de valores de chave no **chaves** coluna.  
  
    > [!NOTE]  
    >  O fornecimento do número de valores distintos, exato ou aproximado, melhora o desempenho, pois a transformação pode alocar antecipadamente uma quantidade da memória para fazer seu trabalho.  
  
    > [!NOTE]  
    >  As opções **Escala de Chaves** e **Chaves** são mutuamente exclusivas. Se você digitar valores em ambas as colunas, o valor maior em **Escala de Chaves** ou **Chaves** será usado.  
  
13. Como opção, clique na guia **Avançado** e defina os atributos que se aplicam à otimização de todas as operações realizadas pela transformação Agregação.  
  
14. Clique em **OK**.  
  
15. Para salvar o pacote atualizado, clique em **Salvar Itens Selecionados** no menu **Arquivo** .  
  
## <a name="see-also"></a>Consulte também  
 [Transformação Agregação](aggregate-transformation.md)   
 [Transformações do Integration Services](integration-services-transformations.md)   
 [Caminhos do Integration Services](../integration-services-paths.md)   
 [Tarefa de Fluxo de Dados](../../control-flow/data-flow-task.md)  
  
  
