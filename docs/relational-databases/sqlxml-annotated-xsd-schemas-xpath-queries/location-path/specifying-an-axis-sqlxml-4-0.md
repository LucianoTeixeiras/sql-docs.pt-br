---
title: Especificando um eixo (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 633298907d13b1d499522a0f1f37eb7671dc9074
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779434"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Especificando um eixo (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   O eixo especifica a relação de árvore entre os nós selecionados pela etapa de local e o nó de contexto. Há suporte para os seguintes eixos: **filho**  
  
     Contém o filho do nó de contexto.  
  
     A seguinte expressão XPath (caminho do local) seleciona do nó de contexto atual todos os  **\<cliente >** filhos:  
  
    ```  
    child::Customer  
    ```  
  
     Na consulta XPath a seguir, `child` é o eixo. `Customer` é o teste de nó.  
  
-   **parent**  
  
     Contém o pai do nó de contexto.  
  
     A seguinte expressão XPath seleciona todos os  **\<cliente >** pais da  **\<ordem >** filhos:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Isso corresponde à especificação de `child::Customer`. Nesta consulta XPath, `child` e `parent` são os eixos. `Customer` e `Order` são os testes de nó.  
  
-   **attribute**  
  
     Contém o atributo do nó de contexto.  
  
     A seguinte expressão XPath seleciona os **CustomerID** atributo do nó de contexto:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **self**  
  
     Contém o próprio nó de contexto.  
  
     A seguinte expressão XPath seleciona o nó atual se ele for o  **\<ordem >** nó:  
  
    ```  
    self::Order  
    ```  
  
     Nesta consulta XPath, `self` é o eixo e `Order` é o teste de nó.  
  
  
