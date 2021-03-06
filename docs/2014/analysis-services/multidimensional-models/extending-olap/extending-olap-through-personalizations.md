---
title: Estendendo o OLAP por meio de personalizações | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 67e1af257dcdb9700fcdfa6643a50000f9dc845f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092186"
---
# <a name="extending-olap-through-personalizations"></a>Estendendo OLAP por meio de personalizações
  O Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] fornece muitas funções intrínsecas para uso com as linguagens MDX e DMX. Essas funções são designadas para executar todas as operações, desde cálculos estatísticos padrão ao desvio de membros em uma hierarquia. No entanto, como em qualquer outro produto complexo, há sempre a necessidade de estender a funcionalidade para o produto.  
  
 Assim, o Analysis Services oferece a capacidade de adicionar assemblies e extensões personalizadas a uma instância do serviço, para atender suas necessidades comerciais sempre que a funcionalidade padrão não for suficiente.  
  
## <a name="assemblies"></a>Assemblies  
 Os assemblies permitem estender a funcionalidade de negócios do MDX e DMX. É possível criar a funcionalidade desejada em uma biblioteca, como uma DLL (biblioteca de vínculo dinâmico) e adicionar a biblioteca como um assembly a uma instância ou a um banco de dados do Analysis Services. Em seguida, os métodos públicos na biblioteca são expostos como funções definidas pelo usuário para expressões MDX e DMX, procedimentos, cálculos, ações e aplicativos cliente.  
  
## <a name="personalized-extensions"></a>Extensões personalizadas  
 As extensões de personalização do SQL Server Analysis Services são a base do conceito de implementação de uma arquitetura de plug-in. As extensões de personalização do Analysis Services fazem uma modificação simples e discreta na arquitetura de assemblies gerenciados existente e são expostas através do modelo de objeto <xref:Microsoft.AnalysisServices.AdomdServer> do Analysis Services, da sintaxe MDX e de conjuntos de linhas de esquema.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento de Assemblies de modelo multidimensional](../multidimensional-model-assemblies-management.md)   
 [Extensões de personalização do Analysis Services](analysis-services-personalization-extensions.md)  
  
  
