---
title: Lendo exemplo de dados grandes | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b2e91f5587751ca7a6d6bb7e91ab3509152b1d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645394"
---
# <a name="reading-large-data-sample"></a>Lendo exemplo de dados grande

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Este aplicativo de exemplo do [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] demonstra como recuperar um valor grande de coluna única de um banco de dados do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando o método [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

O arquivo de código desta amostra chama-se ReadLargeData.java e pode ser encontrado no seguinte local:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Requisitos

Para executar este aplicativo de exemplo, você precisará ter acesso ao banco de dados de exemplo [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Defina também o classpath para incluir o arquivo mssql-jdbc.jar. Para obter mais informações sobre como definir o classpath, consulte [usando o Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> O [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornece os arquivos de biblioteca de classes mssql-jdbc a serem usados de acordo com suas configurações preferenciais do JRE (Java Runtime Environment). Para obter mais informações sobre qual arquivo JAR escolher, consulte [requisitos do sistema para o Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Exemplo

No exemplo a seguir, o código de exemplo faz uma conexão com o banco de dados [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Em seguida, o código de exemplo cria dados de exemplo e atualiza a tabela Production.Document usando uma consulta parametrizada.

Além disso, o código de exemplo demonstra como obter o modo de buffer adaptável usando o método [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) da classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Observe que, a partir da versão 2.0 do driver JDBC, a propriedade de conexão responseBuffering é definida por padrão como "adaptável".

Em seguida, usando uma instrução SQL com o objeto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), o código de exemplo executa a instrução SQL e coloca os dados retornados em um objeto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).

Por fim, o código de exemplo itera pelas linhas de dados do conjunto de resultados e usa o método [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) para acessar alguns dos dados.

[!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]

## <a name="see-also"></a>Consulte Também

[Manipular dados grandes](../../../connect/jdbc/code-samples/working-with-large-data.md)
