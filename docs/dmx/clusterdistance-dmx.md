---
title: ClusterDistance (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ClusterDistance
dev_langs:
- DMX
helpviewer_keywords:
- ClusterDistance function
ms.assetid: a13152b3-4cd1-4c79-8a3e-207624198330
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ba8bb17dbd5e443a56b4eb218fae814f8fbcff4
ms.contentlocale: pt-br
ms.lasthandoff: 08/02/2017

---
# <a name="clusterdistance-dmx"></a>ClusterDistance (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  O **ClusterDistance** função retorna a distância do caso de entrada do cluster especificado, ou se nenhum cluster for especificado, a distância do caso de entrada do cluster mais provável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
ClusterDistance([<ClusterID expression>])  
```  
  
## <a name="applies-to"></a>Aplica-se a  
 Essa função só pode ser usada se o modelo de mineração de dados subjacente oferecer suporte a clustering. A função pode ser usada com qualquer tipo de modelo de clusterização (EM, K-Means etc.), mas o resultado será diferente de acordo com o algoritmo.  
  
## <a name="return-type"></a>Tipo de retorno  
 Valor escalar.  
  
## <a name="remarks"></a>Comentários  
 O **ClusterDistance** função retorna a distância entre o caso de entrada e o cluster que tem a maior probabilidade de caso de entrada.  
  
 No caso da clusterização K-Means, como qualquer caso pode pertencer a apenas um cluster, com um peso de associação de 1.0, a distância do cluster sempre será 0. No entanto, em K-Means, pressupõe-se que cada cluster tem um centroide. Para obter o valor do centroide, consulte ou procure a tabela aninhada NODE_DISTRIBUTION no conteúdo do modelo de mineração. Para obter mais informações, consulte [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md).  
  
 No caso do método de clusterização de EM padrão, todos os pontos dentro do cluster são considerados igualmente prováveis; portanto, por design, não há centroide para o cluster. O valor de **ClusterDistance** entre um caso específico e um cluster específico *N* é calculada da seguinte maneira:  
  
 ClusterDistance(N) =1–(membershipWeight(N))  
  
 Ou:  
  
 ClusterDistance(N) = 1 – ClusterProbability (N))  
  
## <a name="related-prediction-functions"></a>Funções de previsão relacionadas  
 O [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fornece as seguintes funções adicionais para consultar modelos de clusterização:  
  
-   Use o [Cluster &#40; DMX &#41;](../dmx/cluster-dmx.md) função para retornar o cluster mais provável.  
  
-   Use o [ClusterProbability &#40; DMX &#41;](../dmx/clusterprobability-dmx.md) função para obter a probabilidade de um caso pertence a um determinado cluster. Este valor serve como o inverso da distância de cluster.  
  
-   Use o [PredictHistogram &#40; DMX &#41;](../dmx/predicthistogram-dmx.md) função para retornar um histograma da probabilidade do caso de entrada existir em cada um dos clusters do modelo.  
  
-   Use o [PredictCaseLikelihood &#40; DMX &#41;](../dmx/predictcaselikelihood-dmx.md) função para retornar uma medida de 0 a 1 que indica como um caso de entrada é existir, considerando o modelo aprendido pelo algoritmo.  
  
## <a name="example1-obtaining-cluster-distance-to-the-most-likely-cluster"></a>Exemplo 1: Obtendo a distância do cluster para um cluster mais provável  
 O exemplo a seguir retorna a distância do caso especificado para o cluster ao qual o caso provavelmente pertence.  
  
```  
SELECT  
    ClusterDistance()  
FROM  
    [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Resultados do exemplo:  
  
|Expressão|  
|----------------|  
|0.0477390930705145|  
  
 Para descobrir qual é esse cluster, você pode substituir  `Cluster` for `ClusterDistance` no exemplo anterior.  
  
 Resultados do exemplo:  
  
|$CLUSTER|  
|--------------|  
|Cluster 6|  
  
## <a name="example2-obtaining-distance-to-a-specified-cluster"></a>Exemplo 2: Obtendo a distância para um cluster especificado  
 A sintaxe a seguir usa o conjunto de linhas do esquema de conteúdo do modelo de mineração para retornar a lista de IDs de nó e legendas de nó para os clusters que existem no modelo de mineração. Você pode usar a legenda do nó como o argumento de identificador de cluster no **ClusterDistance** função.  
  
```  
SELECT NODE_UNIQUE_NAME, NODE_CAPTION   
FROM <model>.CONTENT   
WHERE NODE_TYPE = 5  
```  
  
 Resultados do exemplo:  
  
|NODE_UNIQUE_NAME|NODE_CAPTION|  
|------------------------|-------------------|  
|001|Cluster 1|  
|002|Cluster 2|  
  
 A sintaxe a seguir retorna a distância do caso especificado do cluster rotulado como Cluster 2.  
  
```  
SELECT  
    ClusterDistance('Cluster 2')  
AS [Cluster 2 Distance]  
FROM [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
    '2-5 Miles' AS [Commute Distance],  
    'Graduate Degree' AS [Education],  
    0 AS [Number Cars Owned],  
    0 AS [Number Children At Home]) AS t  
```  
  
 Resultados do exemplo:  
  
|Distância do Cluster 2|  
|------------------------|  
|0.97008209236394|  
  
## <a name="see-also"></a>Consulte também  
 [Cluster &#40; DMX &#41;](../dmx/cluster-dmx.md)   
 [Extensões de mineração de dados &#40; DMX &#41; Referência de função](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funções &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Conteúdo do modelo de mineração para Clustering modelos &#40; Analysis Services – mineração de dados &#41;](../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
