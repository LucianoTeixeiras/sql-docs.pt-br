---
title: Função Level (Construtor de Relatórios e SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9dfd17acaa01bd415c5fde547bb714f62936d09e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833874"
---
# <a name="report-builder-functions---level-function"></a>Funções do Construtor de Relatórios – Função Level
  Retorna o nível atual de profundidade em uma hierarquia recursiva.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *escopo*  
 (**String**) (Opcional). O nome de um conjunto de dados, um grupo ou uma região de dados que contém os itens de relatório aos quais a função de agregação deve ser aplicada. Se *scope* não estiver especificado, será usado o escopo atual.  
  
## <a name="return-type"></a>Tipo de retorno  
 Retorna um **Integer**. Se *scope* especificar um conjunto de dados ou uma região de dados ou especificar um agrupamento não recursivo (ou seja, um agrupamento sem nenhum elemento **Parent** ), **Level** retornará 0. Se o *scope* for omitido, ele retornará o nível do escopo atual.  
  
## <a name="remarks"></a>Remarks  
 O valor retornado pela função **Level** é baseado em zero; isto é, o primeiro nível em uma hierarquia é 0.  
  
 A função **Level** pode ser usada para fornecer recuo em uma hierarquia recursiva, como uma lista de funcionários.  
  
 Para obter mais informações sobre hierarquias recursivas, consulte [Criando grupos de hierarquias recursivas &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir fornece o nível de linha no grupo de Funcionários:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Usos de expressões em relatórios &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemplos de expressões &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipos de dados em expressões &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Escopo das expressões para totais, agregações e coleções internas &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
