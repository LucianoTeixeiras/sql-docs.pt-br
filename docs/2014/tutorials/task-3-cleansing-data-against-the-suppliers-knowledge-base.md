---
title: 'Tarefa 3: Limpeza de dados em relação a Base de dados de Conhecimento fornecedores | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5aca49b5260fc68f899a012aadaac7609fdb7062
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360328"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a>Tarefa 3: Limpando dados em relação à base de dados de conhecimento Fornecedores
  Nesta tarefa, você executará o processo de limpeza auxiliado por computador. O DQS usa algoritmos avançados e níveis de confiança baseados nos valores de limite especificados para analisar os dados em relação à base de dados de conhecimento selecionada e depois limpá-los. Ver [conhecimento de limpeza de dados usando o DQS (interno)](https://msdn.microsoft.com/library/hh213061.aspx) para obter mais detalhes.  
  
1.  Clique em **iniciar** para iniciar o processo de limpeza auxiliada por computador.  
  
     ![Limpar página do processo de limpeza](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "Limpar página do processo de limpeza")  
  
2.  Quando o processo de limpeza for concluído, examine **estatísticas** na **Profiler** guia. As Estatísticas de Origem fornecem o número de registros processados, o número de registros considerados corretos, o número de registros que o DQS corrige, o número de registros que têm alterações sugeridas pelo DQS e o número de registros inválidos. Na caixa de listagem à direita, você pode visualizar os valores corrigidos, os valores sugeridos e a integridade (até que ponto os dados estão presentes) e a precisão (até que ponto os dados podem ser usados para os fins pretendidos) de valores para cada domínio envolvido no processo de limpeza.  
  
     ![Os resultados da limpeza](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "os resultados da limpeza")  
  
3.  Clique em **próxima** para alternar para o **gerenciar e exibir resultados** página.  
  
## <a name="next-step"></a>Próxima etapa  
 [Tarefa 4: Gerenciando e exibindo resultados](../../2014/tutorials/task-4-manaing-and-viewing-results.md)  
  
  
