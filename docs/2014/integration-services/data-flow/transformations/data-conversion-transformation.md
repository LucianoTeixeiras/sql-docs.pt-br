---
title: Transformação Conversão de Dados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 344b9a24e78960b9eb9f4fece56924b2eb941c0f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358588"
---
# <a name="data-conversion-transformation"></a>transformação Conversão de Dados
  A transformação Conversão de Dados converte os dados de uma coluna de entrada em um tipo diferente de dados e os copia em uma nova coluna de saída. Por exemplo, um pacote pode extrair dados de várias fontes e usar essa transformação para converter colunas em tipos de dados exigidos pelo armazenamento dos dados de destino. Você pode aplicar várias conversões em uma única coluna de entrada.  
  
 Usando essa transformação, um pacote pode executar os seguintes tipos de conversão de dados:  
  
-   Alterar o tipo de dados. Para obter mais informações, consulte [Integration Services Data Types](../integration-services-data-types.md).  
  
    > [!NOTE]  
    >  Se você estiver convertendo dados em um tipo de dados de data ou data/hora, a data na coluna de saída estará no formato ISO, embora a preferência de localidade possa especificar um formato diferente.  
  
-   Defina o comprimento da coluna dos dados da cadeia de caracteres e a precisão e a escala em dados numéricos. Para obter mais informações, consulte [Precisão, escala e comprimento &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).  
  
-   Especifique uma página de código. Para obter mais informações, consulte [Comparing String Data](../comparing-string-data.md).  
  
    > [!NOTE]  
    >  Ao copiar entre colunas com um tipo de dados de cadeia de caracteres, as duas colunas devem usar a mesma página de código.  
  
 Se o comprimento de uma coluna de saída de dados de cadeia de caracteres for menor do que o comprimento de sua coluna de entrada correspondente, os dados de saída serão truncados. Para obter mais informações, consulte [Tratamento de erros em dados](../error-handling-in-data.md).  
  
 Essa transformação tem uma entrada, uma saída e uma saída de erro.  
  
## <a name="related-tasks"></a>Related Tasks  
 Você pode definir propriedades por meio do [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer ou programaticamente. Para obter informações sobre como usar a transformação Conversão de Dados no Designer SSIS, consulte [Converter dados em um tipo de dados diferente por meio da transformação Conversão de Dados](data-conversion-transformation.md) e [Editor de Transformação Conversão de Dados](../../data-conversion-transformation-editor.md). Para obter informações sobre como definir as propriedades dessa transformação programaticamente, consulte [Propriedades comuns](../../common-properties.md) e [Propriedades personalizadas de Transformação](transformation-custom-properties.md).  
  
## <a name="related-content"></a>Conteúdo relacionado  
 Entrada de blog, [Comparação de desempenho entre as técnicas de conversão de tipo de dados no SSIS 2008](https://go.microsoft.com/fwlink/?LinkId=220823), em blogs.msdn.com.  
  
## <a name="see-also"></a>Consulte também  
 [Análise rápida](../../fast-parse.md)   
 [Fluxo de Dados](../data-flow.md)   
 [Transformações do Integration Services](integration-services-transformations.md)  
  
  
