---
title: Configurar a opção de configuração de servidor remote data archive | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6465c5ccfc10847ac011274ed4b25cdb7f52b978
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625644"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Configure a Opção de Configuração do Servidor de arquivo de dados remotos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Use a opção **remote data archive** para especificar se os bancos de dados e as tabelas no servidor podem ser habilitados para Stretch. Para obter mais informações, consulte [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 A opção **remote data archive** pode ter os valores a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Bancos de dados e tabelas no servidor não podem ser habilitados para Ampliação.|  
|1|Bancos de dados e tabelas no servidor podem ser habilitados para Ampliação.|  
  
 Executar **sp_configure** para definir o valor da opção **remote data archive** exige permissões sysadmin ou serveradmin.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe primeiro a definição atual da opção **remote data archive** . O exemplo a seguir habilita a opção **remote data archive** definindo seu valor para 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Para desabilitar a opção, defina o valor para 0.  
  
## <a name="see-also"></a>Consulte Também  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
