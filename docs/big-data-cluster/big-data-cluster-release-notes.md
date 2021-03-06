---
title: Notas de versão
titleSuffix: SQL Server 2019 big data clusters
description: Este artigo descreve as últimas atualizações e problemas conhecidos para clusters de big data de 2019 do SQL Server (versão prévia).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4f16ee38b09198c036941085c9d7a5a1ee35f01b
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54242067"
---
# <a name="release-notes-for-sql-server-2019-big-data-clusters"></a>Notas de versão do SQL Server 2019 clusters de big data

Este artigo fornece as últimas atualizações e problemas conhecidos para a versão mais recente dos clusters de grandes dados do SQL Server. Tabela a seguir redireciona você à seção para as versões abordadas neste artigo.

| Versão | data |
|---|---|
| [CTP 2.2](#ctp22) | Dezembro de 2018 |
| [CTP 2.1](#ctp21) | Novembro de 2018 |
| [CTP 2.0](#ctp20) | Outubro de 2018 |

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp22"></a> CTP 2.2 (dezembro de 2018)

As seções a seguir descrevem os novos recursos e problemas conhecidos para clusters de grandes dados no SQL Server de 2019 CTP 2.2.

### <a name="whats-in-the-ctp-22-release"></a>Novidades na versão CTP 2.2

- Portal de administração de cluster é acessado com `/portal` (**https://\<endereço ip\>: 30777/portal**).
- Nome do serviço mestre do pool é alterado de `service-master-pool-lb` e `service-master-pool-nodeport` para `endpoint-master-pool`.
- Nova versão do **mssqlctl** e atualizada de imagens.
- Diversas correções de bugs e melhorias.

### <a name="known-issues"></a>Problemas conhecidos

As seções a seguir fornecem os problemas conhecidos para clusters de grandes dados do SQL Server no CTP 2.2.

#### <a name="deployment"></a>Implantação

- Não há suporte para atualizar um cluster de dados de grandes dados de uma versão anterior. Você deve fazer backup e excluir qualquer cluster de big data existente antes de implantar a versão mais recente. Para obter mais informações, consulte [atualizar para uma nova versão](deployment-guidance.md#upgrade).

- Depois de implantar no AKS, você poderá ver os seguintes dois eventos de aviso da implantação. Os dois eventos são problemas conhecidos, mas eles não evitam que você implantar com êxito o cluster de big data no AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Se uma implantação de cluster de big data falhar, o namespace associado não é removido. Isso pode resultar em um namespace órfão no cluster. Uma solução alternativa é excluir o namespace manualmente antes de implantar um cluster com o mesmo nome.

#### <a name="cluster-administration-portal"></a>Portal de administração de cluster

O portal de administração de cluster não exibe o ponto de extremidade para a instância mestre do SQL Server. Para localizar o endereço IP e porta para a instância mestre, use o seguinte **kubectl** comando:

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
```

#### <a name="external-tables"></a>Tabelas externas

- É possível criar uma tabela externa do pool de dados para uma tabela que tem sem suporte a tipos de coluna. Se você consultar a tabela externa, você receberá uma mensagem semelhante à seguinte:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Se você consultar uma tabela externa do pool de armazenamento, você poderá receber um erro se o arquivo subjacente está sendo copiado no HDFS ao mesmo tempo.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark e notebooks

- Endereços IP de POD podem mudar no ambiente do Kubernetes como reinicializações de PODs. No cenário em que o pod de mestre é reiniciado, a sessão do Spark pode falhar com `NoRoteToHostException`. Isso é causado por caches JVM que não são atualizados com o novo IP endereços.

- Se você tiver o Jupyter já instalado e um Python separado no Windows, os blocos de anotações do Spark podem falhar. Para contornar esse problema, atualize o Jupyter para a versão mais recente.

- Em um bloco de anotações, se você clicar na **adicionar texto** de comando, a célula de texto for adicionada no modo de visualização, em vez de modo de edição. Você pode clicar no ícone de visualização para alternar para modo de edição e editar a célula.

#### <a name="hdfs"></a>HDFS

- Se o botão direito do mouse em um arquivo no HDFS para visualizá-lo, você poderá ver o seguinte erro:

   `Error previewing file: File exceeds max size of 30MB`

   Atualmente não há nenhuma maneira de visualizar arquivos maiores do que 30 MB no estúdio de dados do Azure.

- Não há suporte para alterações de configuração para o HDFS que envolvem alterações para o hdfs-site. XML.

#### <a name="security"></a>Segurança

- O SA_PASSWORD faz parte do ambiente e detectáveis (por exemplo, em um arquivo de despejo de cabo). Você deve redefinir o SA_PASSWORD na instância mestre após a implantação. Isso não é um bug, mas uma etapa de segurança. Para obter mais informações sobre como alterar o SA_PASSWORD em um contêiner do Linux, consulte [alterar a senha SA](../linux/quickstart-install-connect-docker.md#sapassword).

- Logs AKS podem conter a senha SA para implantações de cluster de big data.

## <a id="ctp21"></a> CTP 2.1 (novembro de 2018)

As seções a seguir descrevem os novos recursos e problemas conhecidos para clusters de grandes dados no SQL Server de 2019 CTP 2.1.

### <a name="whats-in-the-ctp-21-release"></a>Novidades na versão CTP 2.1

- [Implantar aplicativos de Python e R](big-data-cluster-create-apps.md) em um cluster de big data.
- Nova versão do **mssqlctl** e atualizada de imagens. 
- Diversas correções de bugs e melhorias.

### <a name="known-issues"></a>Problemas conhecidos

As seções a seguir fornecem os problemas conhecidos para clusters de grandes dados do SQL Server no CTP 2.1.

#### <a name="deployment"></a>Implantação

- Não há suporte para atualizar um cluster de dados de grandes dados de uma versão anterior. Você deve fazer backup e excluir qualquer cluster de big data existente antes de implantar a versão mais recente. Para obter mais informações, consulte [atualizar para uma nova versão](deployment-guidance.md#upgrade).

- Depois de implantar no AKS, você poderá ver os seguintes dois eventos de aviso da implantação. Os dois eventos são problemas conhecidos, mas eles não evitam que você implantar com êxito o cluster de big data no AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Se uma implantação de cluster de big data falhar, o namespace associado não é removido. Isso pode resultar em um namespace órfão no cluster. Uma solução alternativa é excluir o namespace manualmente antes de implantar um cluster com o mesmo nome.

#### <a name="admin-portal"></a>Portal de administração

- Quando você [criar um aplicativo usando o comando msqlctl ctp](big-data-cluster-create-apps.md) e implantá-lo em um cluster de big data, o Portal de administração de Cluster mostra os pods em que o aplicativo foi implantado como "Desconhecido" na seção de controlador da parte do administrador do SQL Server.

#### <a name="external-tables"></a>Tabelas externas

- É possível criar uma tabela externa do pool de dados para uma tabela que tem sem suporte a tipos de coluna. Se você consultar a tabela externa, você receberá uma mensagem semelhante à seguinte:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Se você consultar uma tabela externa do pool de armazenamento, você poderá receber um erro se o arquivo subjacente está sendo copiado no HDFS ao mesmo tempo.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark e notebooks

- Endereços IP de POD podem mudar no ambiente do Kubernetes como reinicializações de PODs. No cenário em que o pod de mestre é reiniciado, a sessão do Spark pode falhar com `NoRoteToHostException`. Isso é causado por caches JVM que não são atualizados com o novo IP endereços.

- Se você tiver o Jupyter já instalado e um Python separado no Windows, os blocos de anotações do Spark podem falhar. Para contornar esse problema, atualize o Jupyter para a versão mais recente.

- Em um bloco de anotações, se você clicar na **adicionar texto** de comando, a célula de texto for adicionada no modo de visualização, em vez de modo de edição. Você pode clicar no ícone de visualização para alternar para modo de edição e editar a célula.

#### <a name="hdfs"></a>HDFS

- Se o botão direito do mouse em um arquivo no HDFS para visualizá-lo, você poderá ver o seguinte erro:

   `Error previewing file: File exceeds max size of 30MB`

   Atualmente não há nenhuma maneira de visualizar arquivos maiores do que 30 MB no estúdio de dados do Azure.

- Não há suporte para alterações de configuração para o HDFS que envolvem alterações para o hdfs-site. XML.

#### <a name="security"></a>Segurança

- O SA_PASSWORD faz parte do ambiente e detectáveis (por exemplo, em um arquivo de despejo de cabo). Você deve redefinir o SA_PASSWORD na instância mestre após a implantação. Isso não é um bug, mas uma etapa de segurança. Para obter mais informações sobre como alterar o SA_PASSWORD em um contêiner do Linux, consulte [alterar a senha SA](../linux/quickstart-install-connect-docker.md#sapassword).

- Logs AKS podem conter a senha SA para implantações de cluster de big data.

## <a id="ctp20"></a> CTP 2.0 (outubro de 2018)

As seções a seguir descrevem os novos recursos e problemas conhecidos para clusters de grandes dados no SQL Server de 2019 CTP 2.0.

### <a name="whats-in-the-ctp-20-release"></a>Novidades na versão CTP 2.0

- Experiência de implantação simples usando a ferramenta de gerenciamento mssqlctl
- Experiência de notebook nativo no estúdio de dados do Azure
- Arquivos HDFS de consulta por meio do armazenamento de instância do SQL Server
- Virtualização de dados por meio do mestre do SQL Server, Oracle, MongoDB e HDFS
- Assistente de virtualização de dados do SQL Server e Oracle no estúdio de dados do Azure
- Serviços de ML no mestre
- Portal de administração de cluster que você pode usar para monitoramento e solução de problemas
- Envio de trabalho do Spark no estúdio de dados do Azure 
- Interface do usuário do Spark no portal de administração do cluster
- Volume de montagem para classes de armazenamento
- Consultas em pools de dados do mestre
- Mostrar plano para consultas distribuídas no SSMS
- Pacote de PIP para a ferramenta de gerenciamento mssqlctl
- Mecanismo de implantação interna por meio do serviço de controlador

### <a name="known-issues"></a>Problemas conhecidos

As seções a seguir fornecem os problemas conhecidos para clusters de grandes dados do SQL Server no CTP 2.0.

#### <a name="deployment"></a>Implantação

- Se você estiver usando o serviço de Kubernetes do Azure (AKS), a versão recomendada do Kubernetes é 1.10. *, que não oferece suporte a redimensionamento de disco. Você deve verificar se você está dimensionando o armazenamento de forma adequada no momento da implantação. Para obter mais informações sobre como ajustar os tamanhos de armazenamento, consulte o [persistência de dados](concept-data-persistence.md) artigo. Para o Kubernetes implantado em VMs, a versão recomendada é 1.11.

- Depois de implantar no AKS, você poderá ver os seguintes dois eventos de aviso da implantação. Os dois eventos são problemas conhecidos, mas eles não evitam que você implantar com êxito o cluster de big data no AKS.

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- Se uma implantação de cluster de big data falhar, o namespace associado não é removido. Isso pode resultar em um namespace órfão no cluster. Uma solução alternativa é excluir o namespace manualmente antes de implantar um cluster com o mesmo nome.

#### <a name="external-tables"></a>Tabelas externas

- É possível criar uma tabela externa do pool de dados para uma tabela que tem sem suporte a tipos de coluna. Se você consultar a tabela externa, você receberá uma mensagem semelhante à seguinte:

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- Se você consultar uma tabela externa do pool de armazenamento, você poderá receber um erro se o arquivo subjacente está sendo copiado no HDFS ao mesmo tempo.

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark e notebooks

- Endereços IP de POD podem mudar no ambiente do Kubernetes como reinicializações de PODs. No cenário em que o pod de mestre é reiniciado, a sessão do Spark pode falhar com `NoRoteToHostException`. Isso é causado por caches JVM que não são atualizados com o novo IP endereços.

- Se você tiver o Jupyter já instalado e um Python separado no Windows, os blocos de anotações do Spark podem falhar. Para contornar esse problema, atualize o Jupyter para a versão mais recente.

- Em um bloco de anotações, se você clicar na **adicionar texto** de comando, a célula de texto for adicionada no modo de visualização, em vez de modo de edição. Você pode clicar no ícone de visualização para alternar para modo de edição e editar a célula.

#### <a name="hdfs"></a>HDFS

- Se o botão direito do mouse em um arquivo no HDFS para visualizá-lo, você poderá ver o seguinte erro:

   `Error previewing file: File exceeds max size of 30MB`

   Atualmente não há nenhuma maneira de visualizar arquivos maiores do que 30 MB no estúdio de dados do Azure.

- Não há suporte para alterações de configuração para o HDFS que envolvem alterações para o hdfs-site. XML.

#### <a name="security"></a>Segurança

- O SA_PASSWORD faz parte do ambiente e detectáveis (por exemplo, em um arquivo de despejo de cabo). Você deve redefinir o SA_PASSWORD na instância mestre após a implantação. Isso não é um bug, mas uma etapa de segurança. Para obter mais informações sobre como alterar o SA_PASSWORD em um contêiner do Linux, consulte [alterar a senha SA](../linux/quickstart-install-connect-docker.md#sapassword).

- Logs AKS podem conter a senha SA para implantações de cluster de big data.

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre clusters de grandes dados do SQL Server, consulte [quais são os clusters do SQL Server 2019 big data?](big-data-cluster-overview.md).
