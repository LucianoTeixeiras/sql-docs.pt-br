---
title: "Criar tabela instrução limitações | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f7cec23f3ec8103b2805e0ee3c0f04d20011cb6
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="create-table-statement-limitations"></a>Criar tabela limitações de instrução
Quando o Microsoft Access, Microsoft Excel ou Paradoxdriver é usado e o comprimento de uma coluna de texto ou binário não for especificado (ou for especificado como 0), o comprimento da coluna será definido como 255.  
  
 Quando o driver dBASE é usado e o comprimento de uma coluna de texto ou binário não for especificado (ou for especificado como 0), o comprimento da coluna será definido como 254.  
  
 Há suporte para um máximo de 255 colunas.  
  
 Quando o driver do Microsoft Excel é usado em um Microsoft Excel 5.0, 7.0, ou a fonte de 97 dados, uma planilha não pode ser criado com o mesmo nome de uma planilha que foi descartado anteriormente. Quando o driver do Microsoft Excel é usado para acessar uma planilha de versão 5.0, 7.0 ou 97, uma instrução DROP TABLE limpa a planilha, mas não exclui o nome da planilha.  
  
 Quando o driver do Paradox é usado, não é possível adicionar colunas depois que um índice foi definido em uma tabela. Se a primeira coluna da lista de argumentos de uma instrução CREATE TABLE cria um índice, uma segunda coluna não pode ser incluída na lista de argumentos.