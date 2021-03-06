---
title: Backup e restauração de pacotes (serviço SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 586ab104ed802c0d78465d600fccd5f65e213b39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139893"
---
# <a name="package-backup-and-restore-ssis-service"></a>Backup e restauração de pacotes (serviço SSIS)
    
> [!IMPORTANT]  
>  Esse tópico discute o serviço [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , um serviço do Windows para o gerenciamento de pacotes do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . O [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] dá suporte ao serviço para compatibilidade de versões anteriores com versões anteriores do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. A partir do [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], você pode gerenciar objetos como pacotes no servidor do Integration Services.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pacotes podem ser salvos no sistema de arquivos ou no msdb, um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] banco de dados do sistema. Os pacotes salvos no msdb podem ter backup e serem restaurados usando recursos de backup e restauração do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Para obter mais informações sobre como fazer backups e restauração do banco de dados msdb, clique em um dos seguintes tópicos:  
  
-   [Fazer backup e restaurar bancos de dados do SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [Fazer backup e restaurar bancos de dados do sistema &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclui o **dtutil** utilitário (dtutil), que você pode usar para gerenciar os pacotes de prompt de comando. Para obter mais informações, consulte [dtutil Utility](dtutil-utility.md).  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Qualquer arquivo de configuração incluído nos pacotes é armazenado no sistema de arquivos. Esses arquivos não são salvos ao fazer o backup do banco de dados msdb; portanto, você deve verificar se o backup é realizado regularmente em todos os arquivos de configuração como parte de seu plano para proteger os pacotes salvos no msdb. Para incluir as configurações no backup do banco de dados msdb, você deve considerar o uso do tipo de configuração do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , em vez das configurações baseadas em arquivos.  
  
## <a name="packages-stored-in-the-file-system"></a>Pacotes armazenados no sistema de arquivos  
 O backup de pacotes salvos no sistema de arquivos deveria ser incluído no plano de backup do sistema de arquivos do servidor. O arquivo de configuração do serviço [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , com o nome padrão de MsDtsSrvr.ini.xml, lista no servidor as pastas monitoradas pelo serviço. Você deve verificar se essas pastas têm backup. Além disso, os pacotes podem ser armazenados em outras pastas no servidor e você deve verificar se essas pastas estão incluídas no backup.  
  
  
