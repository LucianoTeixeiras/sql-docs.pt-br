---
title: Usando assemblies de nome forte personalizados | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eb106ea00037c6c9c8fc236186c9d0882decdd0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122796"
---
# <a name="using-strong-named-custom-assemblies"></a>Usando assemblies de nome forte personalizados
  Um nome forte identifica um assembly e inclui seu nome de texto, o número de versão de quatro partes, informações de cultura (se fornecidas), uma chave pública e uma assinatura digital armazenada no manifesto do assembly. Um nome forte identifica exclusivamente um assembly para o CLR (common language runtime) e garante a integridade binária.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Usando AllowPartiallyTrustedCallersAttribute  
 Para usar assemblies de nome forte com relatórios, é necessário permitir que o assembly de nome forte seja chamado por um código parcialmente confiável usando o atributo **AllowPartiallyTrustedCallers** do assembly. Você pode usar **AllowPartiallyTrustedCallersAttribute** para permitir que assemblies de nome forte sejam chamados pelo Designer de Relatórios ou pelo servidor de relatório em expressões de relatório. Para permitir que o código parcialmente confiável chame assemblies de nome forte, adicione o atributo de nível de assembly a seguir ao seu arquivo de atributo de assembly.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **AllowPartiallyTrustedCallersAttribute** só será efetivo quando aplicado por um assembly de nome forte no nível de assembly. Para obter mais informações sobre como aplicar atributos no nível de assembly, consulte “Aplicando atributos” na documentação do SDK do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
> [!CAUTION]  
>  Quando **AllowPartiallyTrustedCallersAttribute** estiver presente, as verificações de segurança de **FullTrustLinkDemand** serão impedidas, fazendo com que o assembly possa ser chamado de qualquer outro assembly parcialmente confiável. Todas as verificações de segurança, incluindo os atributos de segurança declarativos de nível de classe e de nível de método, devem ser declaradas de forma explícita.  
  
## <a name="see-also"></a>Consulte também  
 [Usar assemblies personalizados com relatórios](using-custom-assemblies-with-reports.md)  
  
  
