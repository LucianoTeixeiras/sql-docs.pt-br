---
title: O que é o controlador?
titleSuffix: SQL Server 2019 big data clusters
description: Este artigo descreve o controlador de um cluster de big data do SQL Server 2019 (visualização).
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 84162981b68a309f4a21efc0c0610837be308ddb
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241277"
---
# <a name="what-is-the-controller-on-a-sql-server-2019-big-data-cluster"></a>O que é o controlador em um cluster de big data do SQL Server 2019?

O controlador hospeda a lógica básica para implantar e gerenciar um cluster de big data. Ele cuida de todas as interações com o Kubernetes, instâncias do SQL Server que fazem parte do cluster e outros componentes, como HDFS e Spark. 

O serviço do controlador fornece as seguintes funcionalidades principais:

- Gerenciar o ciclo de vida do cluster: a inicialização do cluster & exclusão, atualize as configurações
- Gerenciar instâncias do mestres do SQL Server
- Gerenciar pools de computação, dados e armazenamento
- Expor as ferramentas de monitoramento para observar o estado do cluster
- Ferramentas de solução de problemas para detectar e reparar problemas inesperados de expor
- Gerenciar a segurança de cluster: Certifique-se de pontos de extremidade do cluster seguro, gerenciar usuários e funções, configurar as credenciais para a comunicação dentro do cluster
- Gerenciar o fluxo de trabalho de atualizações para que eles são implementados com segurança (não disponível no CTP 2.2)
- Gerenciar a alta disponibilidade e recuperação de desastres para serviços com estado no cluster (não disponível no CTP 2.2)

## <a name="deploying-the-controller-service"></a>Implantando o serviço do controlador

O controlador é implantado e hospedado no mesmo namespace do Kubernetes em que o cliente deseja criar um cluster de big data. Esse serviço é instalado por um administrador do Kubernetes durante a inicialização do cluster, usando o utilitário de linha de comando mssqlctl:

```bash
mssqlctl create cluster <name of your cluster>
```

O fluxo de trabalho buildout definirá o layout na parte superior do Kubernetes um cluster de big data totalmente funcional do SQL Server que inclui todos os componentes descritos os [visão geral](big-data-cluster-overview.md) artigo. O fluxo de trabalho de inicialização primeiro cria o serviço do controlador, e quando isso for implantado, o serviço do controlador coordena a instalação e configuração do rest da parte dos serviços de pools de armazenamento, computação, dados e mestre.

## <a name="managing-the-cluster-through-the-controller-service"></a>Gerenciando o cluster por meio do serviço de controlador

Você pode gerenciar o cluster puramente por meio do serviço de controlador usando `mssqlctl` APIs ou o portal de administração de cluster que está hospedado dentro do cluster. Se você implantar objetos Kubernetes adicionais, como os pods no mesmo namespace, eles não são gerenciados ou monitorados pelo serviço do controlador.

O controlador e os objetos de Kubernetes (conjuntos com monitoração de estado, pods, segredos, etc.) criados para um cluster de big data residem em um namespace dedicado do Kubernetes. O serviço do controlador será concedido permissão pelo administrador de cluster do Kubernetes para gerenciar todos os recursos dentro desse namespace.  A política RBAC para esse cenário é configurada automaticamente como parte da implantação de cluster inicial usando `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` um utilitário de linha de comando é escrito em Python que permite aos administradores de cluster inicializar e gerenciar clusters de big data por meio das APIs REST expostas pelo serviço do controlador.

### <a name="cluster-administration-portal"></a>Portal de administração de cluster

Depois que o serviço do controlador está em execução, o administrador de cluster pode usar o [Portal de administração de Cluster](cluster-admin-portal.md) para monitorar o progresso da implantação, detectar e solucionar problemas com os serviços dentro do cluster.

## <a name="controller-service-security"></a>Segurança do controlador de serviço

Toda a comunicação com o serviço do controlador é realizada por meio da API REST sobre HTTPS. Um certificado autoassinado será automaticamente gerado para você em tempo de inicialização. 

Autenticação para o ponto de extremidade de serviço do controlador se baseia no nome de usuário e senha. Essas credenciais são provisionadas no momento de inicialização do cluster usando a entrada para as variáveis de ambiente `CONTROLLER_USERNAME` e `CONTROLLER_PASSWORD`.

> [!NOTE]
> Você deve fornecer uma senha que está em conformidade com [requisitos de complexidade de senha do SQL Server](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre os clusters de grandes dados do SQL Server, consulte a visão geral a seguir:

- [Quais são os clusters do SQL Server 2019 grandes dados?](big-data-cluster-overview.md)
