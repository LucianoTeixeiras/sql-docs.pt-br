---
title: '@@VERSION (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b8367bb24a37996b2956e3107113812a32086fed
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-configuration-functions"></a>Versão - Transact SQL funções de configuração
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna informações de compilação e sistema para a instalação atual do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@VERSION  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **nvarchar**  
  
## <a name="remarks"></a>Comentários  
 O @@VERSION resultados são apresentados como uma cadeia de caracteres nvarchar. Você pode usar o [SERVERPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/serverproperty-transact-sql.md) função para recuperar os valores de propriedade individuais.  
  
 Para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as informações a seguir são retornadas.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Versão  
  
-   Arquitetura do processador  
  
-   Data de compilação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Instrução de direitos autorais  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edição  
  
-   Versão do sistema operacional  
  
 Para o [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], as informações a seguir são retornadas.  
  
-   Edição - "Banco de Dados SQL do Windows Azure"  
  
-   Nível de produto - "(CTP)" ou "(RTM)"  
  
-   Versão do produto  
  
-   Data de compilação  
  
-   Instrução de direitos autorais  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>R: retornar a versão atual do[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 O exemplo a seguir mostra o retorno das informações de versão da instalação atual.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>B. Retornar a versão atual do[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>Consulte também  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

