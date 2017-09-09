---
title: NEWID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWID
- NEWID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- NEWID function
ms.assetid: f7014e60-96d5-457e-afc3-72b60ba20c0f
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6f9b19f1af5bc0b9c3bde1dfd7bddabd420f40d
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="newid-transact-sql"></a>NEWID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Cria um valor exclusivo do tipo **uniqueidentifier**.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
NEWID ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Comentários  
 `NEWID()` é compatível com RFC4122.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-the-newid-function-with-a-variable"></a>A. Usando uma função NEWID com uma variável  
 O exemplo a seguir usa `NEWID()` para atribuir um valor a uma variável declarada como o **uniqueidentifier** tipo de dados. O valor de **uniqueidentifier** variável de tipo de dados é impresso antes do valor ser testado.  
  
```  
-- Creating a local variable with DECLARE/SET syntax.  
DECLARE @myid uniqueidentifier  
SET @myid = NEWID()  
PRINT 'Value of @myid is: '+ CONVERT(varchar(255), @myid)  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Value of @myid is: 6F9619FF-8B86-D011-B42D-00C04FC964FF  
```  
  
> [!NOTE]  
>  O valor retornado por NEWID é diferente para cada computador. O número mostrado é meramente ilustrativo.  
  
### <a name="b-using-newid-in-a-create-table-statement"></a>B. Usando NEWID em uma instrução CREATE TABLE  
  
**Aplica-se a**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
 O exemplo a seguir cria o `cust` de tabela com um **uniqueidentifier** tipo de dados e usa NEWID para preencher a tabela com um valor padrão. Ao atribuir o valor padrão de `NEWID()`, cada linha existente e nova possui um valor exclusivo para a coluna `CustomerID`.  
  
```  
-- Creating a table using NEWID for uniqueidentifier data type.  
CREATE TABLE cust  
(  
 CustomerID uniqueidentifier NOT NULL  
   DEFAULT newid(),  
 Company varchar(30) NOT NULL,  
 ContactName varchar(60) NOT NULL,   
 Address varchar(30) NOT NULL,   
 City varchar(30) NOT NULL,  
 StateProvince varchar(10) NULL,  
 PostalCode varchar(10) NOT NULL,   
 CountryRegion varchar(20) NOT NULL,   
 Telephone varchar(15) NOT NULL,  
 Fax varchar(15) NULL  
);  
GO  
-- Inserting 5 rows into cust table.  
INSERT cust  
(CustomerID, Company, ContactName, Address, City, StateProvince,   
 PostalCode, CountryRegion, Telephone, Fax)  
VALUES  
 (NEWID(), 'Wartian Herkku', 'Pirkko Koskitalo', 'Torikatu 38', 'Oulu', NULL,  
 '90110', 'Finland', '981-443655', '981-443655')  
,(NEWID(), 'Wellington Importadora', 'Paula Parente', 'Rua do Mercado, 12', 'Resende', 'SP',  
 '08737-363', 'Brasil', '(14) 555-8122', '')  
,(NEWID(), 'Cactus Comidas para Ilevar', 'Patricio Simpson', 'Cerrito 333', 'Buenos Aires', NULL,   
 '1010', 'Argentina', '(1) 135-5555', '(1) 135-4892')  
,(NEWID(), 'Ernst Handel', 'Roland Mendel', 'Kirchgasse 6', 'Graz', NULL,  
 '8010', 'Austria', '7675-3425', '7675-3426')  
,(NEWID(), 'Maison Dewey', 'Catherine Dewey', 'Rue Joseph-Bens 532', 'Bruxelles', NULL,  
 'B-1180', 'Belgium', '(02) 201 24 67', '(02) 201 24 68');  
GO  
```  
  
### <a name="c-using-uniqueidentifier-and-variable-assignment"></a>C. Usando uniqueidentifier e atribuição de variável  
 O exemplo a seguir declara uma variável local chamada `@myid` como uma variável do **uniqueidentifier** tipo de dados. Em seguida, é atribuído um valor à variável usando-se a instrução `SET`.  
  
```  
DECLARE @myid uniqueidentifier ;  
SET @myid = 'A972C577-DFB0-064E-1189-0154C99310DAAC12';  
SELECT @myid;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [NEWSEQUENTIALID &#40; Transact-SQL &#41;](../../t-sql/functions/newsequentialid-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funções de sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [uniqueidentifier &#40; Transact-SQL &#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)   
 [Números de sequência](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  