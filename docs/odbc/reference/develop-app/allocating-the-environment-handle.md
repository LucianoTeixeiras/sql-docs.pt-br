---
title: Alocando o identificador de ambiente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a8eefe5bc6678462099afda8381d6b16bd076dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602974"
---
# <a name="allocating-the-environment-handle"></a>Alocar o identificador de ambiente
A primeira tarefa para qualquer aplicativo ODBC é carregar o Gerenciador do Driver. como isso é feito depende do sistema operacional. Por exemplo, em um computador executando o Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT da estação de trabalho/Windows 2000 Professional ou Microsoft Windows® 95/98, o aplicativo ou links para a biblioteca do Gerenciador de Driver ou chamadas  **LoadLibrary** carregar a DLL do Gerenciador de Driver.  
  
 A próxima tarefa, que deve ser feita antes de um aplicativo pode chamar qualquer outra função ODBC, é inicializar o ambiente de ODBC e alocar um identificador de ambiente, da seguinte maneira:  
  
1.  O aplicativo declara uma variável do tipo SQLHENV. Em seguida, ele chama **SQLAllocHandle** e passa o endereço dessa variável e a opção de SQL_HANDLE_ENV. Por exemplo:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  O Gerenciador de Driver aloca uma estrutura na qual armazenar informações sobre o ambiente e retorna o identificador de ambiente na variável.  
  
 O Gerenciador de Driver não chama **SQLAllocHandle** no driver isso porque ele não sabe qual driver a ser chamada de tempo. Atrasa a chamada **SQLAllocHandle** no driver até que o aplicativo chama uma função para se conectar a uma fonte de dados. Para obter mais informações, consulte [do Gerenciador de Driver de função no processo de Conexão](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), mais adiante nesta seção.  
  
 Quando o aplicativo tiver terminado de usar o ODBC, ela libera o identificador de ambiente com **SQLFreeHandle**. Depois de liberar o ambiente, ele é um erro de programação de aplicativo para usar o identificador do ambiente em uma chamada para uma função ODBC; Isso traz consequências indefinidas, mas provavelmente fatais.  
  
 Quando **SQLFreeHandle** é chamado, as versões de driver a estrutura usada para armazenar informações sobre o ambiente. Observe que **SQLFreeHandle** não pode ser chamado para um identificador de ambiente até depois que todos os identificadores de conexão no identificador de ambiente que tenham sido liberados.  
  
 Para obter mais informações sobre o identificador de ambiente, consulte [lida com ambiente](../../../odbc/reference/develop-app/environment-handles.md).
