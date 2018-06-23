---
title: Método Execute (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: 34
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5c32261e06788f366a6c5ce5af24c508b87a6882
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36008703"
---
# <a name="execute-method-xmla"></a>Método Execute (XMLA)
  Envia o XML para comandos Analysis (XMLA) para uma instância de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Isso inclui solicitações que envolvem transferência de dados, como a recuperação ou a atualização dos dados no servidor.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Ação SOAP** "urn: schemas-microsoft-com: XML-análise: executar"  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhum|  
|Valor padrão|Nenhum|  
|Cardinalidade|0-1: elemento opcional que ocorre apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|Nenhum|  
|Elementos filho|[Comando](xml-elements-properties/command-element-xmla.md), [parâmetros](xml-elements-properties/parameters-element-xmla.md), [propriedades](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 O `Execute` método executa comandos XMLA fornecidos no `Command` elemento e retorna qualquer dado resultante usando o XMLA [linhas](xml-data-types/rowset-data-type-xmla.md) tipo de dados (para conjuntos de resultados de tabela) ou o XMLA [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) tipo de dados (para conjuntos de resultados multidimensionais).  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um exemplo da chamada do método `Execute` que contém uma instrução SELECT da linguagem MDX.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Método Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [Métodos &#40;XMLA&#41;](xml-elements-methods.md)   
 [Elementos XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Conjuntos de linhas de esquema do Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  