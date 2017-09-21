---
title: UNION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UNION
- UNION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UNION queries
- combining query results
- UNION operator [SQL Server]
ms.assetid: 607c296f-8a6a-49bc-975a-b8d0c0914df7
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 29f86913fd2fb6bf04c4c00d95427d34128c8fee
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="set-operators---union-transact-sql"></a>Definir operadores - UNION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combina os resultados de duas ou mais consultas em um único conjunto de resultados, que inclui todas as linhas pertencentes a todas as consultas da união. A operação UNION é diferente de usar junções que combinam colunas de duas tabelas.  
  
 A seguir são apresentadas as regras básicas de combinação dos conjuntos de resultados de duas consultas usando UNION:  
  
-   O número e a ordem das colunas devem ser iguais em todas as consultas.  
  
-   Os tipos de dados devem ser compatíveis.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
    { <query_specification> | ( <query_expression> ) }   
  UNION [ ALL ]   
  <query_specification | ( <query_expression> )   
 [ UNION [ ALL ] <query_specification> | ( <query_expression> )   
    [ ...n ] ]   
```  
  
## <a name="arguments"></a>Argumentos  
\<query_specification > | ( \<query_expression >) é uma especificação de consulta ou uma expressão de consulta que retorna dados a serem combinados com os dados de outra expressão de consulta ou especificação de consulta. As definições das colunas que fazem parte de uma operação UNION não precisam ser iguais, mas devem ser compatíveis por meio de conversão implícita. Quando tipos de dados diferem, o tipo de dados resultante é determinado com base nas regras de [precedência de tipo de dados](../../t-sql/data-types/data-type-precedence-transact-sql.md). Quando os tipos são iguais mas diferem em precisão, escala ou extensão, o resultado é determinado com base nas mesmas regras para expressões de combinação. Para obter mais informações, consulte [Precisão, escala e comprimento &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 Colunas da **xml** tipo de dados deve ser equivalente. Todas as colunas devem ter tipo para um esquema XML ou sem-tipo. Se tiverem tipo, elas deverão ter o tipo igual ao da coleção de esquema XML.  
  
 UNION  
 Especifica que vários conjuntos de resultados serão combinados e retornados como um único conjunto de resultados.  
  
 ALL  
 Incorpora todas as linhas nos resultados. Isso inclui duplicatas. Se não for especificado, as linhas duplicadas serão removidas.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-a-simple-union"></a>A. Usando uma UNION simples  
 No exemplo a seguir, o conjunto de resultados inclui o conteúdo das colunas `ProductModelID` e `Name` das tabelas `ProductModel` e `Gloves`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Here is the simple union.  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
```  
  
### <a name="b-using-select-into-with-union"></a>B. Usando SELECT INTO com UNION  
 No exemplo a seguir, a cláusula `INTO` da segunda instrução `SELECT` especifica que a tabela denominada `ProductResults` contenha o conjunto de resultados final da união das colunas designadas das tabelas `ProductModel` e `Gloves`. Observe que a tabela `Gloves` é criada na primeira instrução `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.ProductResults', 'U') IS NOT NULL  
DROP TABLE dbo.ProductResults;  
GO  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
INTO dbo.ProductResults  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
SELECT ProductModelID, Name   
FROM dbo.ProductResults;  
  
```  
  
### <a name="c-using-union-of-two-select-statements-with-order-by"></a>C. Usando UNION de duas instruções SELECT com ORDER BY  
 A ordem de determinados parâmetros usados com a cláusula UNION é importante. O exemplo a seguir mostra o uso incorreto e correto de `UNION` em duas instruções `SELECT` nas quais uma coluna deve ser renomeada na saída.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
/* INCORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
ORDER BY Name  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
/* CORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
  
```  
  
### <a name="d-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>D. Usando UNION de três instruções SELECT para mostrar os efeitos de ALL e parênteses  
 Os exemplos a seguir usam `UNION` para combinar os resultados de três tabelas que têm as mesmas 5 linhas de dados. O primeiro exemplo usa `UNION ALL` para mostrar os registros duplicados e retorna todas as 15 linhas. O segundo exemplo usa `UNION` sem `ALL` para eliminar as linhas duplicadas dos resultados combinados das três instruções `SELECT` e retorna 5 linhas.  
  
 O terceiro exemplo usa `ALL` com a primeira `UNION` e parênteses cercam a segunda `UNION` que não está usando `ALL`. A segunda `UNION` é processada em primeiro lugar porque está entre parênteses e retorna 5 linhas porque a opção `ALL` não é usada e as linhas duplicadas são removidas. Essas 5 linhas são combinadas com os resultados do primeiro `SELECT` usando as palavras-chave `UNION ALL`. Isso não remove as duplicatas entre os dois conjuntos de cinco linhas. O resultado final tem 10 linhas.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.EmployeeOne', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeOne;  
GO  
IF OBJECT_ID ('dbo.EmployeeTwo', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeTwo;  
GO  
IF OBJECT_ID ('dbo.EmployeeThree', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeThree;  
GO  
  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeOne  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeTwo  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeThree  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
-- Union ALL  
SELECT LastName, FirstName, JobTitle  
FROM dbo.EmployeeOne  
UNION ALL  
SELECT LastName, FirstName ,JobTitle  
FROM dbo.EmployeeTwo  
UNION ALL  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle  
FROM dbo.EmployeeOne  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeOne  
UNION ALL  
(  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree  
);  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-simple-union"></a>E. Usando uma UNION simples  
 No exemplo a seguir, o conjunto de resultados inclui o conteúdo do `CustomerKey` colunas de ambos os `FactInternetSales` e `DimCustomer` tabelas. Desde que a palavra-chave ALL não for usado, as duplicatas são excluídas dos resultados.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="f-using-union-of-two-select-statements-with-order-by"></a>F. Usando UNION de duas instruções SELECT com ORDER BY  
 Quando qualquer instrução SELECT em uma instrução UNION inclui uma cláusula ORDER BY, essa cláusula deve ser colocada após todas as instruções SELECT. O exemplo a seguir mostra o uso incorreto e correto de `UNION` em dois `SELECT` instruções no qual uma coluna é ordenada com ORDER BY.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT  
SELECT CustomerKey   
FROM FactInternetSales    
ORDER BY CustomerKey  
UNION   
SELECT CustomerKey   
FROM DimCustomer  
ORDER BY CustomerKey;  
  
-- CORRECT   
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="g-using-union-of-two-select-statements-with-where-and-order-by"></a>G. Usando UNION de duas instruções SELECT com WHERE e ORDER BY  
 O exemplo a seguir mostra o uso incorreto e correto de `UNION` em dois `SELECT` instruções onde onde e ORDER BY é necessária.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT   
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
ORDER BY CustomerKey   
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
  
-- CORRECT  
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="h-using-union-of-three-select-statements-to-show-effects-of-all-and-parentheses"></a>H. Usando UNION de três instruções SELECT para mostrar os efeitos de ALL e parênteses  
 Os exemplos seguintes usam `UNION` para combinar os resultados de **a mesma tabela** para demonstrar os efeitos de ALL e parênteses ao usar `UNION`.  
  
 O primeiro exemplo usa `UNION ALL` para mostrar duplicado registros e retorna cada linha na tabela de origem três vezes. O segundo exemplo usa `UNION` sem `ALL` para eliminar as linhas duplicadas dos resultados combinados das três `SELECT` instruções e retorna somente as linhas unduplicated da tabela de origem.  
  
 O terceiro exemplo usa `ALL` com a primeira `UNION` e parênteses delimitando a segunda `UNION` que não está usando `ALL`. O segundo `UNION` é processado primeiro porque ele está entre parênteses. Retorna somente as linhas unduplicated da tabela, pois o `ALL` opção não for usada e duplicatas forem removidas. Essas linhas são combinadas com os resultados da primeira `SELECT` usando o `UNION ALL` palavras-chave. Isso não remove as duplicatas entre os dois conjuntos.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL  
(  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
);  
```  
  
## <a name="see-also"></a>Consulte também  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Exemplos SELECT &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
  
  

