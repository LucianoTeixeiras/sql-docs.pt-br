---
title: Organizar Trabalhos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job category
- organize jobs
ms.assetid: 629c3e06-f933-483b-8621-280dbb7a7bd1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 45296a5f2e2d36e0e3e62938a0a2396c9a26a7fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47661064"
---
# <a name="organize-jobs"></a>organizar trabalhos
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

As categorias de trabalho ajudam a organizar os trabalhos de modo a facilitar sua filtragem e agrupamento. Por exemplo, você pode organizar todos os seus trabalhos de backup de banco de dados na categoria Manutenção de Banco de Dados. Você também pode criar suas próprias categorias de trabalho.  
  
> [!WARNING]  
> As categorias multisservidor só existem em um servidor mestre. Há apenas uma categoria de trabalho padrão disponível em um servidor mestre: [**Não Categorizado (Multisservidor)**]. Quando um trabalho multisservidor é baixado, sua categoria é alterada para **Trabalhos do MSX** no servidor de destino.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descrição**|**Tópico**|  
|Descreve como criar uma categoria de trabalho.|[Criar uma categoria de trabalho](../../ssms/agent/create-a-job-category.md)|  
|Descreve como excluir uma categoria de trabalho.|[Excluir uma categoria de trabalho](../../ssms/agent/delete-a-job-category.md)|  
|Descreve como atribuir um trabalho a uma categoria de trabalho.|[Atribuir um trabalho a uma categoria de trabalho](../../ssms/agent/assign-a-job-to-a-job-category.md)|  
|Descreve como alterar a associação de uma categoria de trabalho.|[Change the Membership of a Job Category](../../ssms/agent/change-the-membership-of-a-job-category.md)|  
|Descreve como listar as informações de categoria.|[Listar informações de categoria de trabalho](../../ssms/agent/list-job-category-information.md)|  
  
