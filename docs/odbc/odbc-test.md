---
title: Teste ODBC | Microsoft Docs
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
- ODBC test [ODBC]
- ODBC drivers [ODBC], testing
- gtrtst32.dll
- gtrts32w.dll [ODBC]
- odbct32w.exe [ODBC]
- odbcte32.exe [ODBC]
- testing ODBC drivers [ODBC]
ms.assetid: 7f13894c-5697-436c-be3d-fe16e1a02325
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c5396150d9b3ae7e3c79fa3568c1468f775cb8e
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-test"></a>Teste ODBC
Teste do Microsoft® ODBC é um aplicativo habilitado para ODBC que você pode usar para testar o Gerenciador de Driver ODBC e drivers ODBC. ODBC 3.51 inclui ANSI e habilitado para Unicode versões de teste do ODBC. Os arquivos correspondentes são os seguintes:  
  
-   Odbcte32.exe e Gtrtst32.dll, para a versão ANSI.  
  
-   Odbct32w.exe e Gtrts32w.dll, para a versão Unicode.  
  
 Para usar o teste de ODBC, você deve entender a API de ODBC, a linguagem C e SQL. Para obter mais informações sobre a API de ODBC, consulte o [referência do programador de ODBC](../odbc/reference/odbc-programmer-s-reference.md).  
  
 Tópicos de Ajuda que foram incluídos anteriormente nesta seção da documentação agora estão contidos dentro do programa de teste do ODBC. Abra Odbcte32.exe ou Odbct32w.exe, abra o **ajuda** menu e clique **tópicos da Ajuda**.  
  
 Observe que as versões de 64 bits desses aplicativos, destinam-se para sistemas de operacionais do Microsoft Windows de 64 bits, têm os mesmos nomes que as versões de 32 bits, mesmo que eles sejam arquivos separados. ou seja, o nome para a versão Unicode da versão de 64 bits do teste de ODBC é odbct32w.exe.