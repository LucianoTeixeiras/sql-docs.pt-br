---
title: 'Tarefa 16: Verificando com o Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0f8c608384e3840f0c154233e90a79d4319bbad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203186"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Tarefa 16: Verificando com o Master Data Manager
  Nesta tarefa, você verificará o status do trabalho em lotes enviado pelo pacote SSIS e verificará se os dados foram carregados no servidor MDS usando o Master Data Manager.  
  
1.  Inicie **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)). Se já estiver aberto, clique em **Microsoft SQL Server Master Data Services** na parte superior para alternar para o **home page do**.  
  
2.  Clique em **gerenciamento de integração**.  
  
3.  Observe que há um lote com denominado **EIMBatch** que você enviou na lista. Clique em **importação de dados** na barra de menus se você não vir a tela a seguir.  
  
     ![Lote EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "lote EIM")  
  
4.  Alternar de volta para a home page por clique **SQL Server 2012 Master Data Services** na parte superior.  
  
5.  Certifique-se de que **fornecedores** modelo é selecionado para **modelo** e **VERSION_1** está selecionado para **versão**e clique em  **Explorer**.  
  
6.  Você pode consultar o pacote SSIS de dados importado para o MDS. Os dados devem ser limpos e não ter nenhuma duplicata **código** valores (Observação: **SupplierID** coluna no Excel corresponde ao **código** atributo da entidade Supplier no MDS).  
  
## <a name="next-step"></a>Próxima etapa  
 [Tarefa 17: Examinando o projeto de limpeza do DQS criado pelo pacote SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
