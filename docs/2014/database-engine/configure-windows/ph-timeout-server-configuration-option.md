---
title: Opção de configuração de servidor PH timeout | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 25a89c00466cf4a702202f6a6fb4959f1d845c41
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52639414"
---
# <a name="ph-timeout-server-configuration-option"></a>Opção de configuração de servidor PH timeout
  Use a opção tempo limite PH para especificar o tempo, em segundos, que o manipulador de protocolo de texto completo deve aguardar para se conectar a um banco de dados antes que o tempo limite seja excedido. O valor padrão é 60 segundos. Aumente o valor tempo limite ph quando as tentativas de conexão estiverem excedendo o tempo limite devido a problemas temporários na rede.  
  
 O manipulador de protocolo de texto completo é hospedado no host de daemon de filtro e é usado para buscar no SQL Server os dados de texto completo a serem indexados. Para obter mais informações sobre os componentes da pesquisa de texto completo, veja [Pesquisa de Texto Completo](../../relational-databases/search/full-text-search.md).  
  
 Ao tentar buscar uma linha de dados, se o manipulador de protocolo não puder se conectar ao SQL Server dentro do tempo especificado, ele informará um erro de tempo limite para aquela linha. A busca de texto completo será feita na linha mais tarde. Para obter mais informações sobre o gatherer de texto completo, veja [Popular índices de texto completo](../../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Pesquisa de Texto Completo](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opções de configuração do servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
