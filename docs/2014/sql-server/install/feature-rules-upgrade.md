---
title: Recurso regras (atualização) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 998ff700a63274c2a57f7e3dc9d6981b2e43bb53
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48193098"
---
# <a name="feature-rules-upgrade"></a>Regras de recurso (atualizar)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instalação valida a configuração do computador antes da operação de instalação ser concluída. Durante a instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o sistema verifica o computador onde o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] será instalado e verifica as condições que impedem uma operação bem-sucedida de instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Antes que a Instalação inicie o assistente de atualização, ele recupera o status de cada item. Em seguida, compara o resultado com condições necessárias e fornece orientação para a remoção de problemas de bloqueio.  
  
 A verificação da configuração do sistema gera um relatório que contém uma breve descrição de cada regra executada, bem como o status de execução. O relatório de verificação de configuração do sistema está localizado em % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
 Antes de executar a operação de instalação, reveja os seguintes tópicos:  
  
1.  [Requisitos de hardware e software para a instalação do SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Recursos com suporte nas edições do SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considerações sobre segurança para uma instalação do SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versões de idiomas locais no SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Outras referências:  
  
1.  [Atualizações de versão e edição com suporte](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Antes de instalar o cluster de failover](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>Consulte também  
 [Normas de instalação](../../../2014/sql-server/install/install-rules.md)  
  
  
