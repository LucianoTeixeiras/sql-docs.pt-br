---
title: Elemento BaseProperty (CSDLBI) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b82b9b6f137b09768fbfdadb78d98f9cd293e81e
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="baseproperty-element-csdlbi"></a>Elemento BaseProperty (CSDLBI)
  O elemento BaseProperty é um tipo complexo que serve como base para outros elementos.  
  
 Seus atributos podem aparecer em colunas e em medidas.  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 A tabela a seguir lista os elementos e atributos que definem o elemento BaseProperty.  
  
|Nome|É obrigatório|Descrição|  
|----------|-----------------|-----------------|  
|Alinhamento|Não|O nome fornecido ao membro (coluna, medida, propriedade de navegação, hierarquia ou nível) que é definido pela implementação do tipo Member|  
|FormatString|Não|O nome para exibição do membro.|  
|IsRightToLeft|Não|Um valor booliano que indica se o campo contém texto que pode ser lido da direita para a esquerda.<br /><br /> Se esse atributo for omitido, será usada a configuração padrão (do modelo).|  
|SortDirection|Não|Um valor que indica como os valores de campo geralmente são classificados. O conteúdo desse atributo é definido pelo tipo simples SortDirection.<br /><br /> Se esse atributo for omitido, será atribuída uma direção de classificação com base no tipo de dados do campo.|  
|Unidades|Não|O símbolo que se aplica a valores de campos para expressar unidades.<br /><br /> Se ele for omitido, as unidades serão desconhecidas.|  
  
## <a name="alignment-element"></a>Elemento Alignment  
 Esse tipo simples define o formato de nomenclatura que é usado para resolver a ambiguidade de membros.  
  
|Valor|Description|  
|-----------|-----------------|  
|Nenhuma|Use o nome do atributo.|  
|Contexto|Use o nome da relação de entrada.|  
|Mesclagem|Concatene o nome da relação de entrada e o nome da propriedade, de acordo com as regras da gramática atual.|  
  
## <a name="sortdirection-element"></a>Elemento SortDirection  
 Esse tipo simples define o formato de nomenclatura que é usado para resolver a ambiguidade de membros.  
  
|Valor|Description|  
|-----------|-----------------|  
|Nenhuma|Use o nome do atributo.|  
|Contexto|Use o nome da relação de entrada.|  
|Mesclagem|Concatene o nome da relação de entrada e o nome da propriedade.|  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre o modelo de objeto de tabela em compatibilidade 1050 1103 por meio de níveis](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  