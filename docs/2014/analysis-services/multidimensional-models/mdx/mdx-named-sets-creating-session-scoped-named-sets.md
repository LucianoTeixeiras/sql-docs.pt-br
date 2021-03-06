---
title: Criando no escopo da sessão conjuntos nomeados (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96b34d8b3fd2dce31f604c50a7431b993a29beca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216366"
---
# <a name="creating-session-scoped-named-sets-mdx"></a>Criando conjuntos nomeados no escopo da sessão (MDX)
  Para criar um conjunto nomeado que esteja disponível por meio de uma sessão da linguagem MDX, use a instrução [CREATE SET](/sql/mdx/mdx-data-definition-create-set). Um conjunto nomeado criado com a instrução CREATE SET não será removido até que a sessão MDX seja encerrada.  
  
 Como discutido neste tópico, a sintaxe da palavra-chave WITH é direta e fácil usar.  
  
> [!NOTE]  
>  Para obter mais informações sobre conjuntos nomeados, consulte [Criando conjuntos nomeados em MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
## <a name="create-set-syntax"></a>Sintaxe de CREATE SET  
 Use a sintaxe a seguir para uma instrução CREATE SET:  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 Na sintaxe de CREATE SET, o parâmetro `cube name` contém o nome do cubo que contém os membros do conjunto nomeado. Se o parâmetro `cube name` não for especificado, o cubo atual será usado como o cubo que contém o membro do conjunto nomeado. Além disso, o parâmetro `Set_Identifier` contém o alias do conjunto nomeado, e o parâmetro `Set_Expression` contém a expressão de conjunto à qual o alias do conjunto nomeado fará referência.  
  
## <a name="create-set-example"></a>Exemplo de CREATE SET  
 O exemplo a seguir usa a instrução CREATE SET para criar o conjunto nomeado `SetCities_2_3` com base no cubo Loja. Os membros do conjunto nomeado `SetCities_2_3` são as lojas localizadas em Cidade 2 e Cidade 3.  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 Ao usar a instrução CREATE SET para definir o conjunto nomeado `SetCities_2_3` , esse conjunto nomeado continuará disponível durante a sessão MDX atual. O exemplo a seguir é uma consulta válida que retornaria os membros de Cidade 2 e Cidade 3 e que poderia ser executada a qualquer momento após a criação do conjunto nomeado `SetCities_2_3` e antes do fim da sessão.  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando no escopo da consulta conjuntos nomeados &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
