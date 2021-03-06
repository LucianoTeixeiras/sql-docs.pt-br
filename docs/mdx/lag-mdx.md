---
title: Latência (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3c5479aa3ce855b554f34f72c5c86aa86eb04b9f
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740875"
---
# <a name="lag-mdx"></a>Latência (MDX)


  Retorna o membro que é um número especificado de posições antes de um membro especificado no nível do membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Member_Expression.Lag(Index)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
 *Index*  
 Uma expressão numérica válida que especifica o número de posições de membro a serem atrasadas.  
  
## <a name="remarks"></a>Remarks  
 As posições de membros em um nível são determinadas pela ordem natural da hierarquia de atributo. A numeração das posições se baseia em zero.  
  
 Se o retardo especificado for zero, o **latência** função retorna o próprio membro especificado.  
  
 Se o retardo especificado for negativo, o **latência** função retorna um membro subsequente.  
  
 `Lag(1)` é equivalente a [PrevMember](../mdx/prevmember-mdx.md) função. `Lag(-1)` é equivalente a [NextMember](../mdx/nextmember-mdx.md) função.  
  
 O **latência** função é semelhante ao [levar](../mdx/lead-mdx.md) funcionar, exceto que o **levar** função procura na direção oposta a **latência** função. Ou seja, `Lag(n)` é equivalente a `Lead(-n)`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna o valor para dezembro de 2001:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(2) ON 0  
FROM [Adventure Works]  
  
```  
  
 O exemplo a seguir retorna o valor para março de 2002:  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lag(-1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
