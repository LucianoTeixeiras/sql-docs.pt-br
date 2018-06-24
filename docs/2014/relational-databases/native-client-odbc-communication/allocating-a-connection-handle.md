---
title: Alocando um identificador de Conexão | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d362fcc43a2b900cab4633d154c985a50830718c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36117878"
---
# <a name="allocating-a-connection-handle"></a>Alocando um identificador de conexão
  Antes de o aplicativo poder se conectar a uma fonte de dados ou driver, ele deve alocar um identificador de conexão. Isso é feito chamando **SQLAllocHandle** com o *HandleType* parâmetro definido como SQL_HANDLE_DBC e *InputHandle* apontando para um identificador de ambiente inicializado.  
  
 As características da conexão são controladas pela definição dos atributos de conexão. Por exemplo, pelo fato de as transações ocorrerem no nível da conexão, o nível de isolamento da transação é um atributo de conexão. De modo semelhante, o tempo limite de logon, ou número de segundos para esperar durante uma tentativa de conexão antes de atingir o tempo limite, é um atributo de conexão.  
  
 Atributos de Conexão são definidos com [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md), e suas configurações atuais são recuperadas com [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md). Se **SQLSetConnectAttr** é chamado antes de tentar uma conexão, o Gerenciador de Driver ODBC armazenará os atributos em sua estrutura de conexão e os definirá no driver como parte do processo de conexão. Alguns atributos de conexão devem ser definidos antes da tentativa de conexão do aplicativo; outros podem ser definidos depois de estabelecida a conexão. Por exemplo, SQL_ATTR_ODBC_CURSORS deve ser definido antes de se estabelecer a conexão, mas SQL_ATTR_AUTOCOMMIT pode ser definido após o estabelecimento da conexão.  
  
 Os aplicativos executados no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versão 7.0 ou posterior, às vezes, podem melhorar seu desempenho com a redefinição do tamanho do pacote de rede de protocolo TDS (tabular data stream). O tamanho de pacote padrão é definido no servidor como 4 KB. Um tamanho de pacote de 4 KB a 8 KB geralmente oferece um desempenho melhor. Se, na prática, constatar-se que o desempenho melhora com um tamanho de pacote diferente, o aplicativo poderá redefinir o tamanho do pacote. Aplicativos ODBC podem fazer isso antes de se conectar ao chamar **SQLSetConnectAttr** com a opção SQL_ATTR_PACKET_SIZE. Alguns aplicativos apresentam um desempenho melhor com um tamanho de pacote maior, mas, em geral, os aprimoramentos de desempenho são mínimos em se tratando de tamanhos de pacote maiores que 8 KB.  
  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client tem um número de atributos de conexão estendida que um aplicativo pode usar para aumentar sua funcionalidade. Alguns desses atributos controlam as mesmas opções que podem ser especificadas em fontes de dados e usadas para substituir qualquer opção definida em uma fonte de dados. Por exemplo, se um aplicativo usa identificadores entre aspas, ele pode definir o atributo específico de driver SQL_COPT_SS_QUOTED_IDENT como SQL_QI_ON para garantir que essa opção seja sempre definida independentemente da definição de qualquer fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Comunicação com o SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  