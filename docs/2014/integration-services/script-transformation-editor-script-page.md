---
title: Editor de transformação scripts (página Script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 102988ac347543a4d2e2110d4c8511c398be9348
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060676"
---
# <a name="script-transformation-editor-script-page"></a>Editor de Transformação Scripts (página Script)
  Use a guia **Script** da caixa de diálogo **Editor de Transformação Scripts** para especificar um script e propriedades relacionadas.  
  
 Para saber mais sobre o componente Script, consulte [componente de Script](data-flow/transformations/script-component.md) e [Configurando o componente Script no Editor de componente de Script](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Para obter informações sobre a programação do componente Script, consulte [Estender o fluxo de dados com o componente de Script](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Opções  
 **Propriedades**  
 Visualize e modifique as propriedades da transformação Scripts. Muitas das propriedades exibidas são somente leitura. Você pode modificar as seguintes propriedades:  
  
|Valor|Description|  
|-----------|-----------------|  
|**Descrição**|Descreva a finalidade da transformação scripts.|  
|**LocaleID**|Especifique a localidade para fornecer informações de solicitação e de conversão de data e hora específicas da região.|  
|**Nome**|Digite um nome descritivo para o componente.|  
|**ValidateExternalMetadata**|Indique se a transformação Scripts deve validar coluna de metadados contra fontes de dados externas em tempo de design. Um valor de `false` retarda a validação até o tempo de execução.|  
|**ReadOnlyVariables**|Digite uma lista de variáveis separada por vírgulas a ser acessada em modo somente leitura pela transformação Scripts.<br /><br /> Observação: nomes de variáveis fazem diferenciação de maiúsculas e minúsculas.|  
|**ReadWriteVariables**|Digite uma lista de variáveis separada por vírgulas a ser acessada em modo leitura/gravação pela transformação Scripts.<br /><br /> Observação: nomes de variáveis fazem diferenciação de maiúsculas e minúsculas.|  
|**ScriptLanguage**|Selecione a linguagem de script a ser usada pelo componente de Script.<br /><br /> Para definir a linguagem de script padrão para componentes e tarefas de Script, use a opção **Linguagem de script** na página **Geral** da caixa de diálogo **Opções** . Para obter mais informações, consulte [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Especifica a classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> e o `Microsoft.SqlServer.TxScript` assembly que aceitam a infraestrutura do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
 **Editar Script**  
 Use o VSTA [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (Tools for Applications) para criar ou modificar um script.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de mensagens e erros do Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Selecione o tipo de componente Script](../../2014/integration-services/select-script-component-type.md)   
 [Editor de transformação scripts &#40;página de colunas de entrada&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Editor de transformação scripts &#40;entradas e saídas de página&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Editor de transformação scripts &#40;página de gerenciadores de Conexão&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Exemplos de componentes de Script adicionais](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
