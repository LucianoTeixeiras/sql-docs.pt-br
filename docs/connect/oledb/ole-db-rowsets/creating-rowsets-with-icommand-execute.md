---
title: 'Criando conjuntos de linhas com ICommand:: execute | Microsoft Docs'
description: Criando conjuntos de linhas com ICommand::Execute
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 86de5c5e985d038ec4e2640fcd9d4d87b56546d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773814"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Criando conjuntos de linhas com ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Para conjuntos de linhas criados usando o método **ICommand::Execute**, as propriedades que você deseja obter no conjunto de linhas resultante podem restringir o texto do comando. Isto é especialmente crítico para consumidores que dão suporte a texto de comando dinâmico.  
  
 O OLE DB Driver for SQL Server não pode usar cursores do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para dar suporte a vários resultados do conjunto de linhas gerados por muitos comandos. Se um consumidor solicitar um conjunto de linhas que exigir suporte de cursor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ocorrerá um erro se o texto do comando gerar mais de um só conjunto de linhas como seu resultado. Para obter mais informações, consulte [resultados de vários conjuntos de linhas de geração de comandos](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Rolável Driver do OLE DB para conjuntos de linhas do SQL Server são compatíveis com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursores. O [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] indica limitações sobre cursores que são sensíveis às alterações feitas por outros usuários do banco de dados. Especificamente, as linhas em alguns cursores não podem ser ordenadas e a tentativa de criar um conjunto de linhas usando um comando que contenha uma cláusula SQL ORDER BY pode falhar. Para obter mais informações, confira [Conjuntos de linha e cursores do SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Conjuntos de linhas](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
