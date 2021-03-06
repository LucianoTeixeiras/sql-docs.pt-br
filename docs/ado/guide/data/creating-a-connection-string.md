---
title: Criando uma cadeia de Conexão | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41732b25c7b2c02f5b6b8a319e057d204a3a3384
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611375"
---
# <a name="creating-a-connection-string"></a>Criando uma cadeia de conexão
Uma cadeia de caracteres de conexão consiste em uma lista de pares de valor do argumento (ou seja, parâmetros), separada por ponto e vírgula. Por exemplo:  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Todos os parâmetros devem ser reconhecidos pelo ADO ou o provedor especificado.  
  
 ADO reconhece os seguintes cinco argumentos em uma cadeia de conexão.  
  
|Argumento|Description|  
|--------------|-----------------|  
|*Provedor*|Especifica o nome de um provedor a ser usado para a conexão.|  
|*Nome do Arquivo*|Especifica o nome de um arquivo específico do provedor (por exemplo, um objeto de fonte de dados persistentes) que contém informações de conexão predefinidos.|  
|*URL*|Especifica a cadeia de caracteres de conexão como uma URL absoluta que identifica um recurso, como um arquivo ou diretório.|  
|*Provedor remoto*|Especifica o nome de um provedor a ser usado ao abrir uma conexão de cliente. (Apenas serviço de dados remotos.)|  
|*Servidor remoto*|Especifica o nome do caminho do servidor a ser usado ao abrir uma conexão de cliente. (Apenas serviço de dados remotos.)|  
  
 Outros argumentos são passados para o provedor nomeado na *provedor* argumento, sem nenhum processamento pelo ADO.  
  
 O aplicativo HelloData no [HelloData: um simples aplicativo de ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) usada a seguinte cadeia de conexão:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 Nessa cadeia de caracteres de conexão, o ADO reconhece somente o `"Provider=SQLOLEDB"` parâmetro, que especifica o provedor Microsoft OLE DB para SQL Server como a fonte de dados do ADO. O restante dos pares de valor do argumento, `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, são passados textuais para esse provedor. O tipo e a validade de tais parâmetros são específicas do provedor. Para obter informações sobre os parâmetros válidos que podem ser passados na cadeia de conexão, consulte a documentação do provedor individuais.  
  
 Acordo com o OLE DB Provider para SQL Server, você pode substituir "Server" para o *fonte de dados* parâmetro e "Banco de dados" para o *catálogo inicial* parâmetro. Assim, a cadeia de conexão a seguir geraria resultados idênticos àquele acima:  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
