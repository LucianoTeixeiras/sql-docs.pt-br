---
title: Método setTrustStore (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8deaaf006698018764eb67dc27e3f7cdb372e04a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687756"
---
# <a name="settruststore-method-sqlserverdatasource"></a>Método setTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o caminho (inclusive o nome de arquivo) para o arquivo trustStore do certificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *trustStore*  
  
 Uma **Cadeia de Caracteres** que contém o caminho (inclusive o nome de arquivo) para o arquivo trustStore do certificado.  
  
## <a name="remarks"></a>Remarks  
 Se a propriedade trustStore não for especificada ou for definida como nula, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] dependerá das regras de pesquisa de fábrica do gerenciador de confiança para determinar o repositório de certificados a ser usado. O SunX509 TrustManagerFactory padrão tenta localizar o material confiável nas seguintes localidades nessa ordem:  
  
-   1. Um arquivo especificado pela propriedade do sistema JVM (Máquina Virtual Java) "javax.net.ssl.trustStore".  
  
-   2. "\<java-home >/lib/security/jssecacerts" arquivo.  
  
-   3. "\<java-home >/lib/security/cacerts" arquivo.  
  
 Para obter mais informações, consulte a documentação da interface do SunX509 TrustManager no site da Sun Microsystems.  
  
 Se a propriedade trustStore for definida como uma cadeia de caracteres ou uma cadeia de caracteres vazia "", o driver usará esse valor para localizar o arquivo trustStore para validar o certificado SSL do servidor.  
  
 Uma propriedade trustStorePassword pode ser especificada junto com a propriedade trustStore e seu valor é usado para abrir o arquivo trustStore. Para obter mais informações, veja [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
