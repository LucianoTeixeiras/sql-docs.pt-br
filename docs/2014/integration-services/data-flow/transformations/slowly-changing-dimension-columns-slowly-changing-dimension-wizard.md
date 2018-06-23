---
title: Colunas da Dimensão de Alteração Lenta (Assistente para Dimensões de Alteração Lenta) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8b999432cdf3b3bec55eaf007005da7bbefab0f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36020743"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a>Colunas da Dimensão de Alteração Lenta (Assistente para Dimensões de Alteração Lenta)
  Use a caixa de diálogo **Colunas de Dimensão de Alteração Lenta** para selecionar um tipo de alteração para cada coluna de dimensão de alteração lenta.  
  
 Para obter mais informações sobre este assistente, consulte [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opções  
 **Colunas de Dimensão**  
 Selecione uma coluna de dimensão na lista.  
  
 **Alterar Tipo**  
 Selecione um **Atributo Fixo**ou um dos dois tipos de atributos de alteração. Use **Atributo Fixo** caso o valor em uma coluna não deva ser alterado; assim o [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tratará as alterações como erros. Use **Atributo de alteração** para substituir os valores existentes por com valores alterados. Use **Atributo Histórico** para salvar valores alterados em novos registros, marcando os registros anteriores como desatualizados.  
  
 **Remover**  
 Selecione uma coluna de dimensão e a remova da lista de colunas mapeadas clicando em **Remover**.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar saídas por meio do Assistente para Dimensões de Alteração Lenta](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  