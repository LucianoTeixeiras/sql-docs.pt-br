---
title: Definindo procedimentos armazenados | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4fdfb9e72609596fe41813ad6de3fde2dd070320
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142276"
---
# <a name="defining-stored-procedures"></a>Definindo procedimentos armazenados
  Você pode usar procedimentos armazenados para chamar rotinas externas a partir [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. É possível gravar rotinas externas chamadas por um procedimento armazenado em uma linguagem CLR (Common Language Runtime), como C, C++, C#, Visual Basic ou Visual Basic .NET. Um procedimento armazenado pode ser criado e então chamado a partir de diversos contextos, como outros procedimentos armazenados, medidas calculadas ou aplicativos cliente. Os procedimentos armazenados simplificam o desenvolvimento e a implementação de bancos de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ao possibilitar que um código comum seja desenvolvido e então armazenado em um único local. Eles podem ser usados para adicionar a seus aplicativos funcionalidades comerciais que não existem como funcionalidade nativa do MDX.  
  
 Esta seção fornece as informações necessárias para você entender, projetar e implementar procedimentos armazenados.  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Projetando procedimentos armazenados](../multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Descreve como projetar assemblies para uso com o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Criando procedimentos armazenados](creating-stored-procedures.md)|Descreve como criar assemblies para o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Chamando procedimentos armazenados](calling-stored-procedures.md)|Fornece informações sobre como usar assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Acessando o contexto de consulta nos procedimentos armazenados](accessing-query-context-in-stored-procedures.md)|Descreve como acessar informações de escopo e contexto com assemblies.|  
|[Configurando a segurança para procedimentos armazenados](setting-security-for-stored-procedures.md)|Descreve como configurar a segurança de assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Depurando procedimentos armazenados](debugging-stored-procedures.md)|Descreve como depurar assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento de Assemblies de modelo multidimensional](../multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
