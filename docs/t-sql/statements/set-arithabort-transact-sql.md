---
title: SET ARITHABORT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ARITHABORT_TSQL
- ARITHABORT
- SET ARITHABORT
- SET_ARITHABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- terminating queries
- queries [SQL Server], terminating
- overflow errors [SQL Server]
- ARITHABORT option
- divide-by-zero errors
- SET ARITHABORT statement
- ending queries [SQL Server]
- stopping queries
ms.assetid: f938a666-fdd1-4233-b97f-719f27b1a0e6
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c00302049a1831a7126484e953fc2ce384724bf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841484"
---
# <a name="set-arithabort-transact-sql"></a>SET ARITHABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Encerra uma consulta quando ocorre estouro ou erro de divisão por zero durante a execução da consulta.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```
-- Syntax for SQL Server and Azure SQL Database
  
SET ARITHABORT { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ARITHABORT ON
```
  
## <a name="remarks"></a>Remarks  
 Você sempre deve definir ARITHABORT como ON nas sessões de logon. A definição de ARITHABORT como OFF pode afetar negativamente a otimização de consulta, levando a problemas de desempenho.  
  
> [!WARNING]  
>  A configuração padrão ARITHABORT de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] é ON. Os aplicativos cliente que definem ARITHABORT como OFF podem receber planos de consulta diferentes, dificultando a solução de problemas de consultas executadas insatisfatoriamente. Ou seja, a mesma consulta pode ser executada rapidamente no Management Studio, mas lentamente no aplicativo. Ao solucionar problemas de consultas com [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], sempre faça a correspondência com a configuração ARITHABORT do cliente.  
  
 Se SET ARITHABORT for ON e SET ANSI WARNINGS for ON, essas condições de erro provocam o encerramento da consulta.  
  
 Se SET ARITHABORT for ON e SET ANSI WARNINGS for OFF, essas condições de erro provocam o encerramento do lote. Se ocorrer erro em uma transação, a transação será revertida. Se SET ARITHABORT for OFF e ocorrer um desses erros, será exibida uma mensagem de aviso e NULL será atribuído ao resultado da operação aritmética.  
  
 Se SET ARITHABORT for OFF e SET ANSI WARNINGS for OFF, e um desses erros ocorrer, será exibida uma mensagem de aviso, e NULL será atribuído ao resultado da operação aritmética.  
  
> [!NOTE]  
>  Se nem a propriedade SET ARITHABORT e nem SET ARITHIGNORE forem definidas, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retornará NULL e uma mensagem de aviso após a execução da consulta.  
  
 A definição de ANSI_WARNINGS como ON definirá ARITHABORT implicitamente como ON quando o nível de compatibilidade do banco de dados estiver definido como 90 ou mais. Se o nível de compatibilidade do banco de dados for definido como 80 ou menos, a opção ARITHABORT deverá ser definida explicitamente como ON.  
  
 Durante a avaliação da expressão, se SET ARITHABORT for OFF e se uma instrução INSERT, DELETE ou UPDATE encontrar um erro aritmético, de estouro, de divisão por zero ou de domínio, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inserirá ou atualizará um valor NULL. Se a coluna de destino não for anulável, a ação de inserção ou atualização falhará e o usuário receberá uma mensagem de erro.  
  
 Se SET ARITHABORT ou SET ARITHIGNORE estiver definida como OFF e SET ANSI_WARNINGS como ON, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ainda retornará uma mensagem de erro quando encontrar erros de divisão por zero ou de estouro.  
  
 Se SET ARITHABORT for definido como OFF e ocorrer um erro de anulação durante a avaliação da condição booliana de uma instrução IF, o branch FALSE será executado.
  
 SET ARITHABORT deve ser ON quando você estiver criando ou alterando índices em colunas computadas ou modos de exibição indexados. Se SET ARITHABORT for OFF, toda instrução CREATE, UPDATE, INSERT e DELETE das tabelas com índices em colunas computadas ou modos de exibição indexados falhará.
  
 A configuração de SET ARITHABORT é definida no momento da execução e não no momento da análise.  
  
 Para exibir a configuração atual dessa configuração, execute a seguinte consulta:
  
```  
DECLARE @ARITHABORT VARCHAR(3) = 'OFF';  
IF ( (64 & @@OPTIONS) = 64 ) SET @ARITHABORT = 'ON';  
SELECT @ARITHABORT AS ARITHABORT;  
  
```  
  
## <a name="permissions"></a>Permissões  
 Requer associação à função **pública** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo seguinte demonstra erros de divisão por zero e de estouro com as duas configurações de `SET ARITHABORT`.  
  
```  
-- SET ARITHABORT  
-------------------------------------------------------------------------------  
-- Create tables t1 and t2 and insert data values.  
CREATE TABLE t1 (  
   a TINYINT,   
   b TINYINT  
);  
CREATE TABLE t2 (  
   a TINYINT  
);  
GO  
INSERT INTO t1   
VALUES (1, 0);  
INSERT INTO t1   
VALUES (255, 1);  
GO  
  
PRINT '*** SET ARITHABORT ON';  
GO  
-- SET ARITHABORT ON and testing.  
SET ARITHABORT ON;  
GO  
  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab   
FROM t1;  
GO  
  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be no data';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Truncate table t2.  
TRUNCATE TABLE t2;  
GO  
  
-- SET ARITHABORT OFF and testing.  
PRINT '*** SET ARITHABORT OFF';  
GO  
SET ARITHABORT OFF;  
GO  
  
-- This works properly.  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab    
FROM t1;  
GO  
  
-- This works as if SET ARITHABORT was ON.  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be 0 rows';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Drop tables t1 and t2.  
DROP TABLE t1;  
DROP TABLE t2;  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Instruções SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHIGNORE &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithignore-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
