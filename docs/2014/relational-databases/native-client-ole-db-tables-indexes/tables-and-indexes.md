---
title: Tabelas e índices | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 14e7c96e5157853ae3ae93f3ac276d566ed18ae2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36130553"
---
# <a name="tables-and-indexes"></a>Tabelas e índices
  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor do OLE DB Native Client expõe a **IIndexDefinition** e **ITableDefinition** interfaces, permitindo que os consumidores criar, alterar e descartar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelas e índices. As definições válidas de tabela e de índice dependem da versão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 A capacidade de criar ou descartar tabelas e índices depende dos direitos de acesso do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do usuário do aplicativo de consumidor. Descartar uma tabela pode ser uma operação ainda mais restrita pela presença de restrições de integridade referencial declarativas ou outros fatores.  
  
 A maioria dos aplicativos voltados para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usar SQL-DMO em vez dessas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces do provedor OLE DB Native Client. SQL-DMO é uma coleção de objetos de automação OLE que dão suporte a todas as funções administrativas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Os aplicativos destinados a vários provedores OLE DB usam essas interfaces OLE DB genéricas suportadas pelos vários provedores OLE DB.  
  
 No conjunto de propriedades específico de provedor DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] define a propriedade a seguir.  
  
|ID da propriedade|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Tipo: VT_BSTR<br /><br /> Leitura/gravação: gravação<br /><br /> Padrão: Null<br /><br /> Descrição: Esta propriedade é usada somente em **ITableDefinition**. A cadeia de caracteres especificada por esta propriedade é usada ao criar um [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)<br /><br /> .|  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Criando tabelas do SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Adicionando uma coluna a uma tabela do SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Removendo uma coluna de uma tabela do SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Descartando uma tabela do SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Criando índices do SQL Server](../../relational-databases/indexes/indexes.md)  
  
-   [Descartando um índice do SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  