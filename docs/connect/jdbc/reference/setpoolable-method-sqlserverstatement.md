---
title: Método setPoolable (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 809e16fce7cac83b6ba09fcef676c8da920b0dc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759674"
---
# <a name="setpoolable-method-sqlserverstatement"></a>Método setPoolable (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Solicita que uma instrução seja colocada ou não em pool.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *em um pool*  
  
 Se **true**, solicita que a instrução seja colocada em pool. Se **false**, solicita que a instrução não seja colocada em pool.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 O valor especificado no parâmetro *poolable* é uma dica para a implementação do pool de instrução que indica se o aplicativo deseja que a instrução seja colocada em pool. O gerenciador de pools de instrução decidirá se usará a dica.  
  
 O valor do pool de uma instrução aplica-se aos caches de instrução internos implementados pelo driver e aos caches de instrução externos implementados por servidores de aplicativos e outros aplicativos.  
  
 Por padrão, um objeto SQLServerStatement não está em um pool quando criado. Objetos SQLServerPreparedStatement e SQLServerCallableStatement estão em um pool quando criado.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) será lançada se esse método é chamado em uma instrução fechada.  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) retorna um valor que indica se o objeto está em um pool.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
