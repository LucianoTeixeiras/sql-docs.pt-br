---
title: Método setTrustStorePassword (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStorePassword Method (SQLServerDataSource)
apilocation:
- setTrustStorePassword Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: fa87cbde-71cc-4f21-bc07-f8ba2b6a0a3f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ca07fcfe446b2bb4cb841ae0f0275fd7073c6e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658654"
---
# <a name="settruststorepassword-method-sqlserverdatasource"></a>Método setTrustStorePassword (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define a senha usada para verificar a integridade dos dados de trustStore.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setTrustStorePassword(java.lang.String trustStorePassword)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *trustStorePassword*  
  
 Uma **cadeia de caracteres** que contém a senha usada para verificar a integridade dos dados de trustStore.  
  
## <a name="remarks"></a>Remarks  
 Uma propriedade trustStorePassword pode ser especificada juntamente com a propriedade trustStore e seu valor é usado para verificar a integridade do arquivo trustStore.  
  
 Se a propriedade trustStore for definida, mas a propriedade trustStorePassword não for definida, a integridade de trustStore não será verificada.  
  
 Quando as propriedades trustStore e trustStorePassword não forem especificadas, o driver usará as propriedades do sistema JVM (Máquina Virtual Java), “javax.net.ssl.trustStore” e “javax.net.ssl.trustStorePassword”. Se a propriedade do sistema "javax.net.ssl.trustStorePassword" não for especificada, a integridade de trustStore não será verificada.  
  
 Se a propriedade trustStore não estiver definida, mas a propriedade trustStorePassword estiver, o driver JDBC usará o arquivo especificado por "javax.net.ssl.trustStore" como um repositório confiável e a integridade dele será verificada com trustStorePassword. Isso pode ser necessário quando o aplicativo cliente não quiser armazenar a senha na propriedade do sistema JVM.  
  
 Para obter mais informações, veja [Configuração das propriedades de conexão](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 A partir do JDBC Driver 3.0, ao definir SQLServerDataSource.setTrustStorePassword antes de associar as propriedades da fonte de dados, você deverá chamar SQLServerDataSource.setTrustStorePassword antes de estabelecer a conexão. Para obter mais informações, confira [SQLServerDataSource.getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
