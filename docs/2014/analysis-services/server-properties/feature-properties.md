---
title: Propriedades do recurso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c9047bc6bae67b005d8ed93e4831557a0dac9b5
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368048"
---
# <a name="feature-properties"></a>Propriedades de recurso
  As propriedades do recurso pertencem aos recursos do produto, a maioria delas avançadas, incluindo propriedades que controlam vínculos entre instâncias do servidor.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oferece suporte às propriedades de servidor listadas na tabela a seguir. Para obter mais informações sobre as propriedades de servidor adicionais e como defini-las, consulte [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Aplica-se a:** Somente o modo de servidor multidimensional  
  
## <a name="properties"></a>Propriedades  
  
|Propriedade|Padrão|Descrição|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|1|Uma propriedade booliana que indica se procedimentos armazenados CLR estão habilitados.|  
|`LinkInsideInstanceEnabled`|1|Uma propriedade booliana que indica se um objeto vinculado pode ser criado dentro da mesma instância do servidor.|  
|`LinkToOtherInstanceEnabled`|0|Uma propriedade booliana que indica se objetos em servidores remotos podem ser vinculados.|  
|`LinkFromOtherInstanceEnabled`|0|Uma propriedade booliana que indica se objetos podem ser vinculados de outras instâncias do servidor.|  
|`ConnStringEncryptionEnabled`|1|Uma propriedade booliana que indica se a cadeia de caracteres de conexão está criptografada no arquivo de configuração de servidor.|  
|`UseCachedPageAllocators`|0|Uma propriedade booliana que indica se alocadores da página em cache estão habilitados.|  
|`ComUdfEnabled`|0|Uma propriedade booliana que indica se as funções definidas pelo usuário como objetos COM estão habilitadas.|  
|`SQMSupportEnabled`|1|Uma propriedade booliana que indica se os relatórios de erro e de uso de recursos são enviados automaticamente ao [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|  
|`ResourceMonitoringEnabled`|1|Uma propriedade booliana que indica se os contadores de monitoramento de recursos internos estão habilitados. Essa propriedade é ativada por padrão. Quando está habilitada, esta propriedade permite que os contadores coletem dados de uso sobre CPU, memória e atividade de E/S.<br /><br /> Os contadores de monitoramento de recursos internos são usados pelo DMV (Exibições de gerenciamento dinâmico) que relatam sobre a utilização do recurso. Se você desabilitar esta propriedade, as consultas do DMV ainda serão executadas, mas o conjunto de resultados será inválido. Os DMVs que dependem desta propriedade incluem o seguinte:<br />**DISCOVER_OBJECT_ACTIVITY**<br />**DISCOVER_COMMAND_OBJECTS**<br />**DISCOVER_SESSIONS** (para SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Em um sistema de vários núcleos que usa arquitetura de NUMA, desabilitar esta propriedade pode melhorar o desempenho da consulta, particularmente para cargas de trabalho altas de vários usuários. Você precisará executar testes de comparação para determinar se o desempenho da consulta melhorou como o resultado da alteração desta propriedade. Para conhecer as práticas recomendadas sobre como fazer testes de comparação, inclusive limpar o cache e evitar erros comuns, consulte [Guia de operações do SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Consulte também  
 [Configurar propriedades de servidor no Analysis Services](server-properties-in-analysis-services.md)   
 [Determina o Modo de Servidor de uma instância do Analysis Services.](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Usar DMVs &#40;Exibições de Gerenciamento Dinâmico&#41; para monitorar o Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
