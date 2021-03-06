---
title: Método getEncrypt (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 328bf9921bc4d70ef77862edd1476e2f8f629720
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637094"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Método getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retorna um valor **booliano** que indica se a propriedade de criptografia está habilitada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Valor retornado  
 **True** se criptografar está habilitado. Caso contrário, **false**.  
  
## <a name="remarks"></a>Remarks  
 Se a propriedade de criptografia estiver definida como **true**, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] garantirá que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use a criptografia SSL para todos os dados enviados entre o cliente e o servidor se o servidor tiver um certificado instalado.  
  
 Se a propriedade de criptografia não for especificada nem estiver definida como **false**, o driver não exigirá que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dê suporte à criptografia SSL. Se a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não for configurada para forçar a criptografia SSL, será estabelecida uma conexão sem criptografia. Se a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] estiver configurada para forçar a criptografia SSL, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] habilitará a criptografia SSL automaticamente quando for executado em Máquina Virtual Java (JVM) configurada adequadamente. Caso contrário, a conexão será encerrada e o driver gerará um erro. Se a propriedade de criptografia não for definida, o método [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) retornará o valor padrão **false**.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
