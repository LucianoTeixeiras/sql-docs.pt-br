---
title: Editor de transformação de coluna copiar | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 361e0426e4101a281bfb302dad8f4b9d4cc5ded9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36007094"
---
# <a name="copy-column-transformation-editor"></a>Editor de Transformação Copiar Coluna
  Use a caixa de diálogo **Editor de Transformação Copiar Coluna** para selecionar colunas para copiar e nomear as novas colunas de saída.  
  
 Para saber mais sobre a transformação Copiar Colunas, consulte [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).  
  
> [!NOTE]  
>  Ao copiar apenas todos os dados de origem para um destino, poderá não ser necessário usar a transformação Copiar Coluna. Em alguns cenários, você pode conectar uma origem diretamente para um destino, quando nenhuma transformação de dados é requerida. Nestas circunstâncias é frequentemente preferível usar o Assistente de Importação e Exportação do SQL Server para criar o pacote para você. Depois você pode aprimorar e reconfigurar o pacote conforme a necessidade. Para obter mais informações, consulte [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
## <a name="options"></a>Opções  
 **Colunas de Entrada Disponíveis**  
 Selecione as colunas para copiar, usando as caixas de seleção. as seleções adicionam colunas de entrada à tabela abaixo.  
  
 **Coluna de Entrada**  
 Selecione colunas para copiar na lista de colunas de entrada disponíveis. As seleções se refletem naquelas da caixa de seleção da tabela **Colunas de Entrada Disponíveis** .  
  
 **Alias de Saída**  
 Digite um alias para cada nova coluna de saída. O padrão é **Copiar de**, seguido do nome da coluna de entrada; no entanto, é possível escolher qualquer nome descritivo exclusivo.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de mensagens e erros do Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  