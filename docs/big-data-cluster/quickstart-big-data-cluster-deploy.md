---
title: Início rápido da implantação
titleSuffix: SQL Server 2019 big data clusters
description: Passo a passo uma implantação de clusters de big data 2019 do SQL Server (versão prévia) no serviço de Kubernetes do Azure (AKS).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/17/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 3495d41028f72093b58f546d3da2139ff02b848d
ms.sourcegitcommit: 299b63e04498eba22659970cd077f247c1657931
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54898981"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Guia de início rápido: Implantar um cluster de big data do SQL Server no serviço de Kubernetes do Azure (AKS)

Neste início rápido, você pode usar um exemplo de script de implantação para implantar o cluster de big data de 2019 do SQL Server (versão prévia) para o serviço de Kubernetes do Azure (AKS). 

> [!TIP]
> O AKS é apenas uma opção para hospedagem de Kubernetes para seu cluster de big data. Para saber mais sobre outras opções de implantação, como personalizar a implantação de opções, consulte [clusters de como implantar grandes de dados do SQL Server em Kubernetes](deployment-guidance.md).

A implantação de cluster de big data padrão usada aqui consiste em duas instâncias de pool de armazenamento, computação de uma instância de pool, duas instâncias de pool de dados e uma instância do SQL Master. Os dados persistem usando volumes persistentes Kubernetes que usam as classes de armazenamento de padrão do AKS. A configuração padrão usada neste início rápido é adequada para ambientes de desenvolvimento/teste.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Prerequisites

- Uma assinatura do Azure.
- [Ferramentas de big data](deploy-big-data-tools.md):
   - **mssqlctl**
   - **kubectl**
   - **Azure Data Studio**
   - **Extensão do SQL Server de 2019**
   - **CLI do Azure**

## <a name="log-in-to-your-azure-account"></a>Faça logon sua conta do Azure

O script usa a CLI do Azure para automatizar a criação de um cluster do AKS. Antes de executar o script, você deve fazer logon sua conta do Azure com CLI do Azure pelo menos uma vez. Execute o seguinte comando em um prompt de comando.

```
az login
```

## <a name="download-the-deployment-script"></a>Baixe o script de implantação

Neste início rápido automatiza a criação do cluster de big data no AKS usando um script python **implantar-sql-big-data-aks.py**. Se você tiver instalado o python para o **mssqlctl**, você deve ser capaz de executar o script com êxito neste início rápido. 

Em um prompt de bash do Windows PowerShell ou do Linux, execute o seguinte comando para baixar o script de implantação do GitHub.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Execute o script de implantação

Use as etapas a seguir para executar o script de implantação. Esse script criará um serviço AKS no Azure e, em seguida, implantar um cluster de big data 2019 do SQL Server no AKS. Você também pode modificar o script com os outros [variáveis de ambiente](deployment-guidance.md#env) para criar uma implantação personalizada.

1. Execute o script com o seguinte comando:

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Se você tiver o python3 e python2 no computador cliente e no caminho, você precisa executar o comando usando python3: `python3 deploy-sql-big-data-aks.py`.

1. Quando solicitado, insira as seguintes informações:

   | Valor | Descrição |
   |---|---|
   | **ID da assinatura do Azure** | A ID de assinatura do Azure a ser usado para o AKS. Você pode listar todas as suas assinaturas e suas IDs executando `az account list` de outra linha de comando. |
   | **Grupo de recursos do Azure** | O nome do grupo de recursos do Azure para criar para o cluster do AKS. |
   | **Nome de usuário do docker** | O nome de usuário de Docker fornecido como parte da visualização pública limitada. |
   | **Senha do docker** | A senha de Docker fornecida como parte da visualização pública limitada. |
   | **Região do Azure** | A região do Azure para o novo cluster do AKS (padrão **westus**). |
   | **Tamanho da máquina** | O [tamanho de máquina](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) a ser usado para nós no cluster do AKS (padrão **Standard_L4s**). |
   | **Nós de trabalho** | O número de nós de trabalho no cluster do AKS (padrão **3**). |
   | **Nome do cluster** | O nome do cluster do AKS e o cluster de big data. O nome do cluster deve ser apenas caracteres alfanuméricos em letras minúsculas e sem espaços. (padrão **sqlbigdata**). |
   | **Senha** | Senha para o controlador, o gateway HDFS/Spark e a instância mestre (padrão **MySQLBigData2019**). |
   | **Usuário do controlador** | Nome de usuário para o usuário controlador (padrão: **admin**). |

   > [!IMPORTANT]
   > O padrão **Standard_L4s** tamanho da máquina pode não estar disponível em todas as regiões do Azure. Se você selecionar um tamanho de máquina diferente, certifique-se de que o número total de discos que podem ser anexados em todos os nós do cluster é maior que ou igual a 21. Cada declaração de volume persistente no cluster exige um disco anexado. Atualmente, o cluster de big data requer declarações de volume persistente 21. Por exemplo, o [Standard_L4s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#ls-series) tamanho da máquina dá suporte a 16 discos conectados, portanto, três nós significa que os discos de 48 podem ser anexados.

   > [!NOTE]
   > O `sa` conta é um administrador do sistema na instância mestre do SQL Server que é criada durante a instalação. Depois de criar a implantação, o `MSSQL_SA_PASSWORD` variável de ambiente é detectável executando `echo $MSSQL_SA_PASSWORD` no contêiner de instância principal. Para fins de segurança, altere sua `sa` senha na instância mestre após a implantação. Para obter mais informações, consulte [alterar a senha SA](../linux/quickstart-install-connect-docker.md#sapassword).

1. O script começar criando um cluster AKS usando os parâmetros especificados. Esta etapa leva vários minutos.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Monitorar o status

Depois que o script cria o cluster do AKS, ele prossegue para definir variáveis de ambiente necessárias com as configurações que você especificou anteriormente. Em seguida, ele chama **mssqlctl** para implantar o cluster de big data no AKS.

A janela de comando do cliente produzirá o status da implantação. Durante o processo de implantação, você deverá ver uma série de mensagens em que ele está aguardando o pod do controlador:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Depois de 10 a 20 minutos, você deve ser notificado se o pod de controlador está em execução:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.222.222.222:30080
```

> [!IMPORTANT]
> Toda a implantação pode levar muito tempo devido ao tempo necessário para baixar as imagens de contêiner para os componentes do cluster de big data. No entanto, ele não deve levar várias horas. Se você estiver tendo problemas com sua implantação, consulte o [solução de problemas de implantação](deployment-guidance.md#troubleshoot) seção do artigo de diretrizes de implantação.

## <a name="inspect-the-cluster"></a>Inspecione o cluster

A qualquer momento durante a implantação, você pode usar o kubectl ou o Portal de administração de Cluster para inspecionar o status e detalhes sobre o cluster de execução big data.

### <a name="use-kubectl"></a>Usar o kubectl

Abra uma nova janela de comando para usar **kubectl** durante o processo de implantação.

1. Execute o seguinte comando para obter um resumo do status de todo o cluster:

   ```
   kubectl get all -n <your-cluster-name>
   ```

1. Inspecione os serviços do kubernetes e seus pontos de extremidade internos e externos com os seguintes **kubectl** comando:

   ```
   kubectl get svc -n <your-cluster-name>
   ```

1. Você também pode inspecionar o status dos pods kubernetes com o seguinte comando:

   ```
   kubectl get pods -n <your-cluster-name>
   ```

1. Encontre mais informações sobre um pod específico com o seguinte comando:

   ```
   kubectl describe pod <pod name> -n <your-cluster-name>
   ```

> [!TIP]
> Para obter mais detalhes sobre como monitorar e solucionar problemas de uma implantação, consulte o [solução de problemas de implantação](deployment-guidance.md#troubleshoot) seção do artigo de diretrizes de implantação.

### <a name="use-the-cluster-administration-portal"></a>Usar o Portal de administração de Cluster

Quando o pod de controlador estiver em execução, você também pode usar o Portal de administração de Cluster para monitorar a implantação. Você pode acessar o portal usando o IP endereço e porta número externa para o `service-proxy-lb` (por exemplo: **https://\<endereço ip\>: 30777/portal**). As credenciais usadas para logon no portal correspondem aos valores para **usuário Controller** e **senha** que você especificou no script de implantação.

Você pode obter o endereço IP do **serviço de proxy de lb** serviço executando este comando em uma janela de bash ou cmd:

```bash
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

> [!NOTE]
> CTP 2.2, você verá um aviso de segurança ao acessar a página da web, porque os clusters de big data está usando certificados gerados automaticamente SSL. Além disso, no CTP 2.2, ele não mostra o status da instância mestre do SQL Server.

## <a name="connect-to-the-cluster"></a>Conectar-se ao cluster

Quando o script de implantação for concluída, a saída notifica você de sucesso:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Agora, o cluster de big data do SQL Server é implantado no AKS. Agora você pode usar o Studio de dados do Azure para conectar-se a instância mestre do SQL Server e os pontos de extremidade HDFS/Spark usando o Studio de dados do Azure.

### <a id="master"></a> Instância principal

A instância mestre do SQL Server é uma instância do SQL Server tradicional que contém os bancos de dados relacionais do SQL Server. As etapas a seguir descrevem como conectar-se à instância mestre usando o Studio de dados do Azure.

1. Na linha de comando, localize o IP da sua instância mestre com o seguinte comando:

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. No Azure Data Studio, pressione **F1** > **nova Conexão**.

1. Na **tipo de Conexão**, selecione **Microsoft SQL Server**.

1. Digite o endereço IP da instância mestre do SQL Server no **nome do servidor** (por exemplo: **\<Endereço IP\>, 31433**).

1. Insira um logon do SQL **nome de usuário** (`SA`) e **senha** (a senha inserida no script de implantação).

1. Alterar o destino **nome do banco de dados** para um dos seus bancos de dados relacionais.

   ![Conectar-se à instância do mestre](./media/quickstart-big-data-cluster-deploy/connect-to-cluster.png)

1. Pressione **Connect**e o **painel Server** deve aparecer.

### <a id="hdfs"></a> Gateway HDFS/Spark

O **gateway HDFS/Spark** permite que você conecte para trabalhar com o pool de armazenamento do HDFS e executar trabalhos do Spark. As etapas a seguir descrevem como conectar-se com o Studio de dados do Azure.

1. Na linha de comando, localize o endereço IP do seu gateway HDFS/Spark com o seguinte comando:

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```
 
1. No Azure Data Studio, pressione **F1** > **nova Conexão**.

1. Na **tipo de Conexão**, selecione **cluster de big data do SQL Server**.
   
   > [!TIP]
   > Se você não vir as **cluster de big data do SQL Server** conexão de tipo, certifique-se de ter instalado o [extensão do SQL Server 2019](../azure-data-studio/sql-server-2019-extension.md) e que você reiniciou o estúdio de dados do Azure após a conclusão de extensão instalando.

1. Digite o endereço IP do cluster de big data no **nome do servidor** (não especificar uma porta).

1. Insira `root` para o **usuário** e especifique o **senha** para seu cluster de big data que você inseriu no script de implantação.

   ![Conectar-se ao gateway HDFS/Spark](./media/quickstart-big-data-cluster-deploy/connect-to-cluster-hdfs-spark.png)

1. Pressione **Connect**e o **painel Server** deve aparecer.

## <a name="clean-up"></a>Limpar

Se você estiver testando a clusters de grandes dados do SQL Server no Azure, você deve excluir o cluster do AKS quando tiver terminado de evitar cobranças inesperadas. Não remova o cluster se você pretende continuar a usá-lo.

> [!WARNING]
> As etapas a seguir destrói o cluster do AKS que remove o cluster de big data do SQL Server. Se você tiver bancos de dados ou dados do HDFS que você deseja manter, fazer esses backup dos dados antes de excluir o cluster.

Execute o seguinte comando da CLI do Azure para remover o cluster de big data e o serviço AKS no Azure (substitua `<resource group name>` com o **grupo de recursos do Azure** especificado no script de implantação):

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Próximas etapas

O script de implantação configurado o serviço Kubernetes do Azure e também implantado um cluster de big data do SQL Server de 2019. Você também pode optar por personalizar as futuras implantações por meio de instalações manuais. Para saber mais sobre como grandes dados clusters são implantados, bem como como personalizar as implantações, consulte [clusters de como implantar grandes de dados do SQL Server em Kubernetes](deployment-guidance.md).

Agora que o cluster de big data do SQL Server é implantado, você pode carregar dados de exemplo e explore os tutoriais:

> [!div class="nextstepaction"]
> [Tutorial: Carregar dados de exemplo em um cluster de big data do SQL Server de 2019](tutorial-load-sample-data.md)