---
title: Editor Resolver Referência de Coluna | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d007e9bd3b4822cb09bdae8f3736bbd76f26009e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52771198"
---
# <a name="resolve-column-reference-editor"></a>Resolver editor de referência de coluna
  Quando um caminho de entrada é desconectado ou se houver qualquer coluna não mapeada no caminho, um ícone de erro será exibido ao lado do caminho de dados correspondente. Para simplificar a resolução de erros de referência de coluna, o novo editor Resolver Referências permite vincular colunas de saída não mapeadas com colunas de entrada não mapeadas para todos os caminhos da árvore de execução. O editor Resolver Referências também realçará os caminhos para indicar quais caminhos estão sendo resolvidos.  
  
> [!NOTE]  
>  Agora é possível editar um componente até mesmo quando seu caminho de entrada está desconectado  
  
 Depois que todas as referências a coluna foram resolvidas, se não houver erros de caminho de dados, nenhum ícone de erro será exibido ao lado dos caminhos de dados.  
  
## <a name="options"></a>Opções  
 Colunas de Saída Não Mapeadas (Origem):  
 Colunas do caminho upstream que não estão mapeadas no momento  
  
 Colunas Mapeadas (Origem):  
 Colunas do caminho upstream que estão mapeadas para colunas do caminho downstream  
  
 Colunas Mapeadas (Destino):  
 Colunas do caminho upstream que estão mapeadas para colunas do caminho downstream  
  
 Colunas de Entrada Não Mapeadas (Destino):  
 Colunas do caminho downstream que não estão mapeadas no momento  
  
 Excluir Colunas de Entrada Não Mapeadas  
 Selecione Excluir Colunas de Entrada Não Mapeadas para ignorar colunas não mapeadas no destino do caminho de dados. O botão Visualizar Alterações exibe uma lista das alterações que ocorrerão quando você pressionar o botão OK.  
  
  
