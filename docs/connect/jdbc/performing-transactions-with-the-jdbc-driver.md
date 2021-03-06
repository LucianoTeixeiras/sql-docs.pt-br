---
title: Executando transações com o JDBC Driver | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d18f5c550bbf60446ac47961d16c1bbdb7cb2e4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770334"
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Executando transações com o JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  O processamento de transações é um requisito obrigatório de todos os aplicativos que desejam garantir consistência de seus dados persistentes. Com o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], o processamento de transações pode ser realizado localmente ou ser distribuído. Transações são módulos de execução atômicos, consistentes, isolados e duráveis (ACID).  
  
 Os tópicos nesta seção descrevem como o driver JDBC oferece suporte a transações inclusive níveis de isolamento, pontos de salvamento de transação e retenção do conjunto de resultados.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Noções básicas sobre transações](../../connect/jdbc/understanding-transactions.md)|Fornece uma visão geral de como são usadas transações com o driver JDBC.|  
|[Noções básicas sobre transações XA](../../connect/jdbc/understanding-xa-transactions.md)|Fornece uma visão geral de como são usadas transações XA com o driver JDBC.|  
|[Noções básicas sobre os níveis de isolamento](../../connect/jdbc/understanding-isolation-levels.md)|Descreve os vários níveis de isolamento que têm suporte pelo driver JDBC.|  
|[Usando pontos de salvamento](../../connect/jdbc/using-savepoints.md)|Descreve como usar o driver JDBC com pontos de salvamento de transação.|  
|[Usando colocação em espera](../../connect/jdbc/using-holdability.md)|Descreve como usar o driver JDBC com colocação em espera do conjunto de resultados.|  
  
## <a name="see-also"></a>Consulte Também  
 [Visão geral do JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
