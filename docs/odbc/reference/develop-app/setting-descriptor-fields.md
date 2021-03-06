---
title: Configurando campos de descritor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14724a5cc863074344cfbb02615f0ccff228f04c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628414"
---
# <a name="setting-descriptor-fields"></a>Configurar campos de descritor
Para modificar os campos de um descritor de, um aplicativo pode chamar **SQLSetDescField**. Alguns campos são somente leitura e não podem ser definidos. (Consulte a [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) descrição da função.)  
  
 Campos de registro do descritor são definidos com um número de registro (*RecNumber*) de tempo de 1 ou posterior, os campos de cabeçalho do descritor são definidos com um número de registro de 0. Um número de registro de 0 também é usado para definir campos de indicador, acordo com a convenção de que os indicadores estão contidos na coluna 0. Isso pode deixar a impressão de que os campos de indicador estão contidos dentro do cabeçalho do descritor, mas isso não for o caso. Campos de marcador são diferentes de campos de cabeçalho.  
  
 Ao definir os campos individualmente, o aplicativo deve seguir a sequência definida em [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Definir alguns campos faz com que o driver definir outros campos. Isso garante que o descritor sempre está pronto para ser usado depois que o aplicativo tiver especificado um tipo de dados. Quando o aplicativo define o campo SQL_DESC_TYPE, o driver verifica que os outros campos que especificam o tipo são válidos e consistentes.  
  
 Se uma chamada de função que seria definir um campo de descritor falhar, o conteúdo do campo de descritor é indefinido após a chamada de função com falha.
