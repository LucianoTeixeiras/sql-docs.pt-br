---
title: Configurar o acesso somente leitura em uma réplica de disponibilidade (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aaed1030d35fffb1b539339dc882cfb2d6676229
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358958"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a>Configurar o acesso somente leitura em uma réplica de disponibilidade (SQL Server)
  Por padrão, tanto o acesso de leitura-gravação quanto o acesso de tentativa de leitura são permitidos para a réplica primária e nenhuma conexão direta é permitida com as réplicas secundárias de um grupo de disponibilidade AlwaysOn. Este tópico descreve como configurar o acesso de conexão em uma réplica de disponibilidade de um grupo de disponibilidade AlwaysOn no [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou PowerShell.  
  
 Para obter informações sobre as implicações de permitir o acesso somente leitura para uma réplica secundária e para uma introdução ao acesso de conexão, consulte [sobre Conexão acesso cliente a réplicas de disponibilidade &#40;SQL Server&#41; ](about-client-connection-access-to-availability-replicas-sql-server.md) e [secundárias ativas: Réplicas secundárias legíveis &#40;grupos de disponibilidade AlwaysOn&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos e restrições  
  
-   Para configurar um acesso de conexão diferente, deverá estar conectado à instância de servidor que hospeda a réplica primária.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
  
|Tarefa|Permissões|  
|----------|-----------------|  
|Para configurar réplicas ao criar um grupo de disponibilidade|Requer a associação na função de servidor fixa **sysadmin** e a permissão de servidor CREATE AVAILABILITY GROUP, a permissão ALTER ANY AVAILABILITY GROUP ou a permissão CONTROL SERVER.|  
|Para modificar uma réplica de disponibilidade|Requer a permissão ALTER AVAILABILITY GROUP no grupo de disponibilidade, a permissão CONTROL AVAILABILITY GROUP, a permissão ALTER ANY AVAILABILITY GROUP ou a permissão CONTROL SERVER.|  
  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
 **Para configurar o acesso em uma réplica de disponibilidade**  
  
1.  No Pesquisador de Objetos, conecte-se à instância de servidor que hospeda a réplica primária e expanda a árvore de servidores.  
  
2.  Expanda os nós **Alta Disponibilidade AlwaysOn** e **Grupos de Disponibilidade** .  
  
3.  Clique no grupo de disponibilidade cuja réplica você deseja alterar.  
  
4.  Clique com o botão direito do mouse na réplica de disponibilidade e clique em **Propriedades**.  
  
5.  Na caixa de diálogo **Propriedades de Réplica de disponibilidade** , você pode alterar o acesso de conexão para as funções primária e secundária, da seguinte forma:  
  
    -   Para a função secundária, selecione um novo valor na lista suspensa **Secundária de Leitura** , da seguinte forma:  
  
         **Não**  
         Nenhuma conexão de usuário é permitida para bancos de dados secundários desta réplica. Eles não estão disponíveis para acesso de leitura. Essa é a configuração padrão.  
  
         **Tentativa de leitura somente**  
         Somente conexões somente leitura são permitidas para bancos de dados secundários desta réplica. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
         **Sim**  
         Todas as conexões são permitidas para os bancos de dados secundários desta réplica, mas somente para acesso de leitura. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
    -   Para a função primária, selecione um novo valor na lista suspensa **Conexões na função primária** , da seguinte forma:  
  
         **Permitir todas as conexões**  
         Todas as conexões são permitidas com os bancos de dados na réplica primária. Essa é a configuração padrão.  
  
         **Permitir conexões de leitura/gravação**  
         Quando a propriedade Application Intent está definida como **ReadWrite** ou não está definida, a conexão é permitida. Conexões em que a propriedade de conexão Application Intent é definida como **ReadOnly** não são permitidas. Isto pode ajudar a impedir os clientes de conectarem uma carga de trabalho com intenção de leitura à réplica primária por engano. Para obter mais informações sobre a propriedade de conexão Tentativa de Aplicativo, consulte [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
 **Para configurar o acesso em uma réplica de disponibilidade**  
  
> [!NOTE]  
>  Para obter um exemplo desse procedimento, veja [Exemplo (Transact-SQL)](#TsqlExample), mais adiante nesta seção.  
  
1.  Conecte-se à instância de servidor que hospeda a réplica primária.  
  
2.  Se você estiver especificando uma réplica para um novo grupo de disponibilidade, use a instrução [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Se você estiver adicionando ou modificando uma réplica de um grupo de disponibilidade existente, use a instrução [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Para configurar o acesso de conexão para a função secundária, na cláusula ADD REPLICA ou MODIFY REPLICA WITH, especifique a opção SECONDARY_ROLE, da seguinte forma:  
  
         SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**  
  
         onde:  
  
         Não  
         Nenhuma conexão direta é permitida para bancos de dados secundários desta réplica. Eles não estão disponíveis para acesso de leitura. Essa é a configuração padrão.  
  
         READ_ONLY  
         Somente conexões somente leitura são permitidas para bancos de dados secundários desta réplica. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
         ALL  
         Todas as conexões são permitidas para os bancos de dados secundários desta réplica, mas somente para acesso de leitura. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
3.  Para configurar o acesso de conexão para a função primária, na cláusula ADD REPLICA ou MODIFY REPLICA WITH, especifique a opção PRIMARY_ROLE, da seguinte forma:  
  
     PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**  
  
     onde:  
  
     READ_WRITE  
     Conexões em que a propriedade de conexão Application Intent é definida como **ReadOnly** não são permitidas.  Quando a propriedade Application Intent está definida como **ReadWrite** ou não está definida, a conexão é permitida. Para obter mais informações sobre a propriedade de conexão Tentativa de Aplicativo, consulte [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
     ALL  
     Todas as conexões são permitidas com os bancos de dados na réplica primária. Essa é a configuração padrão.  
  
###  <a name="TsqlExample"></a> Exemplo (Transact-SQL)  
 O exemplo a seguir adiciona uma réplica secundária a um grupo de disponibilidade denominado *AG2*. Uma instância de servidor autônoma *COMPUTER03\HADR_INSTANCE*, é especificada para hospedar a nova réplica de disponibilidade. Essa réplica foi configurada para permitir apenas conexões de leitura-gravação para a função primária e para permitir apenas conexões de tentativa de leitura para uma função secundária.  
  
```  
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="PowerShellProcedure"></a> Usando o PowerShell  
 **Para configurar o acesso em uma réplica de disponibilidade**  
  
> [!NOTE]  
>  Para obter um exemplo de código, consulte [Exemplo (PowerShell)](#PSExample), posteriormente nesta seção.  
  
1.  Altere o diretório (`cd`) para a instância do servidor que hospeda a réplica primária.  
  
2.  Ao adicionar uma réplica de disponibilidade a um grupo de disponibilidade, use o cmdlet `New-SqlAvailabilityReplica`. Ao modificar uma réplica de disponibilidade existente, use o cmdlet `Set-SqlAvailabilityReplica`. Os parâmetros relevantes são os seguintes:  
  
    -   Para configurar o acesso de conexão para a função secundária, especifique o `ConnectionModeInSecondaryRole` *secondary_role_keyword* parâmetro, onde *secondary_role_keyword* é igual a um dos seguintes valores:  
  
         `AllowNoConnections`  
         Nenhuma conexão direta é permitida com os bancos de dados na réplica secundária e os bancos de dados não estão disponíveis para acesso de leitura. Essa é a configuração padrão.  
  
         `AllowReadIntentConnectionsOnly`  
         Conexões são permitidas somente com os bancos de dados na réplica secundária em que a propriedade Application Intent está definida como **ReadOnly**. Para obter mais informações sobre essa propriedade, consulte [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
         `AllowAllConnections`  
         Todas as conexões são permitidas com os bancos de dados na réplica secundária para acesso somente leitura.  
  
    -   Para configurar o acesso de conexão para a função primária, especifique `ConnectionModeInPrimaryRole` *primary_role_keyword*, onde *primary_role_keyword* é igual a um dos seguintes valores:  
  
         `AllowReadWriteConnections`  
         Conexões em que a propriedade de conexão Application Intent é definida como ReadOnly não são permitidas. Quando a propriedade Application Intent está definida como ReadWrite ou não está definida, a conexão é permitida. Para obter mais informações sobre a propriedade de conexão Tentativa de Aplicativo, consulte [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
         `AllowAllConnections`  
         Todas as conexões são permitidas com os bancos de dados na réplica primária. Essa é a configuração padrão.  
  
    > [!NOTE]  
    >  Para exibir a sintaxe de um cmdlet, use o cmdlet `Get-Help` no ambiente do [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell. Para obter mais informações, consulte [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Para configurar e usar o provedor do SQL Server PowerShell**  
  
-   [Provedor do SQL Server PowerShell](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="PSExample"></a> Exemplo (PowerShell)  
 O exemplo a seguir define os parâmetros `ConnectionModeInSecondaryRole` e `ConnectionModeInPrimaryRole` para `AllowAllConnections`.  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `   
-InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `   
-InputObject $primaryReplica  
  
```  
  
  
##  <a name="FollowUp"></a> Acompanhar: Depois de configurar o acesso somente leitura para uma réplica de disponibilidade  
 **Acesso somente leitura para uma réplica secundária legível**  
  
-   Ao usar o [utilitário bcp](../../../tools/bcp-utility.md) ou [utilitário sqlcmd](../../../tools/sqlcmd-utility.md), você pode especificar acesso somente leitura a qualquer réplica secundária que está habilitado para acesso somente leitura especificando a `-K ReadOnly` alternar.  
  
-   Para permitir que aplicativos clientes conectem-se a réplicas secundárias legíveis:  
  
    ||Pré-requisito|Link|  
    |-|------------------|----------|  
    |![Caixa de seleção](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Verifique se o grupo de disponibilidade tem um ouvinte.|[Criar ou configurar um ouvinte do grupo de disponibilidade &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |![Caixa de seleção](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Configurar o roteamento somente leitura para o grupo de disponibilidade.|[Configurar o roteamento somente leitura para um grupo de disponibilidade &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 **Fatores que podem afetar gatilhos e trabalhos depois de um failover**  
  
 Se você tem gatilhos e trabalhos que podem falhar ao executar um banco de dados secundário não legível ou em um banco de dados secundário legível, você precisa executar o script dos gatilhos e dos trabalhos para verificar em uma réplica determinada se o banco de dados é primário ou secundário legível. Para obter estas informações, use a função [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) para retornar a propriedade **Updatability** do banco de dados. Para identificar um banco de dados somente leitura, especifique READ_ONLY como o valor, da seguinte maneira:  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 Para identificar um banco de dados leitura/gravação, especifique READ_WRITE como o valor.  
  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
  
-   [Configurar o roteamento somente leitura para um grupo de disponibilidade &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Criar ou configurar um ouvinte do grupo de disponibilidade &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="RelatedContent"></a> Conteúdo relacionado  
  
-   [AlwaysOn: Proposta de valor da secundária legível](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-value-proposition-of-readable-secondary.aspx)  
  
-   [AlwaysOn: Por isso que há duas opções para habilitar uma réplica secundária para a carga de trabalho de leitura?](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload.aspx)  
  
-   [AlwaysOn: Configurando a réplica secundária legível](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-setting-up-readable-seconary-replica.aspx)  
  
-   [AlwaysOn: Eu acabei de habilitar secundária legível, mas minha consulta está bloqueada?](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-i-just-enabled-readble-secondary-but-my-query-is-blocked.aspx)  
  
-   [AlwaysOn: Disponibilizando as estatísticas mais recentes na réplica secundária legível, banco de dados somente leitura e de instantâneo de banco de dados](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-making-upto-date-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot.aspx)  
  
-   [AlwaysOn: Desafios com estatísticas no banco de dados somente leitura, o instantâneo de banco de dados e a réplica secundária](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica.aspx)  
  
-   [AlwaysOn: Impacto na carga de trabalho primária quando você executa o relatório de carga de trabalho na réplica secundária](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica.aspx)  
  
-   [AlwaysOn: Impacto do mapeamento de carga de trabalho de relatório na réplica secundária legível para o isolamento de instantâneo](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-impact-of-mapping-reporting-workload-to-snapshot-isolation-on-readable-secondary.aspx)  
  
-   [AlwaysOn: Minimizando o bloqueio de thread REDO ao executar relatórios de carga de trabalho na réplica secundária](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica.aspx)  
  
-   [AlwaysOn: Latência de dados e o secundário legível](https://blogs.msdn.com/b/sqlserverstorageengine/archive/2011/12/22/alwayson.aspx)  
  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Secundárias ativas: Réplicas secundárias legíveis &#40;grupos de disponibilidade AlwaysOn&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [Sobre o acesso de conexão de cliente a réplicas de disponibilidade &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)  
  
  
