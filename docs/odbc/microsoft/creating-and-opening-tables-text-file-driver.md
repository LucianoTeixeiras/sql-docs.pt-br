---
title: Criando e abrindo tabelas (Driver de arquivo de texto) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769094"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Criar e abrir tabelas (Driver de Arquivo de texto)
Quando o driver de texto é usado, uma nova tabela é criada usando o formato especificado no Odbcinst. ini. Se não for especificado, as tabelas são criadas no formato CSVDELIMITED. Por padrão, o padrão de colunas de INTEIROS a 11 caracteres e colunas FLOAT padrão 22 caracteres. Colunas de data e usam o formato AAAA-MM-DD. CHAR e colunas LONGCHAR são a largura especificada na instrução CREATE.
