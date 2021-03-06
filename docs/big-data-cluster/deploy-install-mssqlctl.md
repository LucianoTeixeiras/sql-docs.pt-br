---
title: Instalar mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Saiba como instalar a ferramenta mssqlctl para instalar e gerenciar clusters de big data de 2019 do SQL Server (visualização).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/15/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aec8f030a996e5dd86c44a5a655e98d4926988ed
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361406"
---
# <a name="install-mssqlctl-to-manage-sql-server-2019-big-data-clusters"></a>Instalar mssqlctl para gerenciar clusters do SQL Server 2019 big data

Este artigo descreve como instalar o **mssqlctl** ferramenta no Windows ou Linux.

**mssqlctl** é um utilitário de linha de comando escrito em Python que permite que os administradores para inicializar e gerenciar o cluster de big data por meio de APIs REST de cluster. A versão do Python mínima necessária é v 3.5. Você também deve ter `pip` que é usado para baixar e instalar **mssqlctl** ferramenta. As instruções a seguir fornecem exemplos para Windows e Ubuntu. Para instalar o Python em outras plataformas, consulte a [documentação do Python](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Se você instalou uma versão anterior do **mssqlctl**, você deve excluir o cluster *antes* Atualizando **mssqlctl** e instalar a nova versão. Para obter mais informações, consulte [atualizar para uma nova versão](deployment-guidance.md#upgrade).

## <a id="windows"></a> Instalação do Windows mssqlctl

1. Em um cliente Windows, baixe o pacote Python necessário [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Para python3.5.3 e posterior, pip3 também é instalado quando você instala o Python. 

   > [!TIP] 
   > Ao instalar Python3, selecione Adicionar Python à sua **caminho**. Se você não fizer isso, você pode descobrir mais tarde onde se encontra pip3 e adicioná-lo para manualmente sua **caminho**.

1. Abra uma nova sessão do Windows PowerShell para que ele obtém o caminho mais recente com o Python nele.

2. Instale **mssqlctl** com o seguinte comando:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a id="linux"></a> Instalação do Linux mssqlctl

No Linux, você deve instalar o Python 3.5 e, em seguida, atualizar o pip. O exemplo a seguir mostra os comandos que funcionariam para Ubuntu. Para outras plataformas Linux, consulte o [documentação do Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Instale os pacotes Python necessários:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Atualize pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```
   
1. Instale **mssqlctl** com o seguinte comando:

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl --user
   ```
   
   > [!NOTE]
   > O `--user` switch instala mssqlctl para o diretório de instalação de usuário do Python. Isso é normalmente `~/.local/bin` no Linux. Adicionar esse diretório ao seu caminho ou navegue até o diretório de instalação do usuário e executar `./mssqlctl` a partir daí.
   
## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre clusters de big data, consulte [quais são os clusters do SQL Server 2019 big data?](big-data-cluster-overview.md).
