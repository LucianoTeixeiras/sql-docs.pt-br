---
title: Protocolos para propriedades MSSQLSERVER (guia Certificado) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 85e7e9cbc454785379fac029cbe970a492e0fffd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760094"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Protocolos para propriedades MSSQLSERVER (guia Certificado)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Use a guia **Certificado** na caixa de diálogo **Protocolos para Propriedades MSSQLSERVER** para selecionar um certificado para o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou para exibir as propriedades de um certificado. Todos os campos estarão em branco até que um certificado seja selecionado.  
  
 Os certificados são armazenados localmente para os usuários no computador. Para carregar um certificado a ser usado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], é necessário estar executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager sob a mesma conta de usuário que o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>Cabeçalho de página  
 **Exibir**  
 Fornece acesso a detalhes adicionais no certificado. Não disponível até que um certificado seja selecionado na caixa **Certificado** . Para obter informações adicionais sobre detalhes do certificado, consulte a documentação do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Liberada**  
 Remove a seleção na caixa **Certificado** .  
  
 **Certificado**  
 Nome do certificado, conforme determinado pelo provedor de segurança. Selecione um certificado para ver os detalhes na grade de propriedades.  
  
## <a name="options"></a>Opções  
 Data de Validade  
 A data final do período de validade do certificado.  
  
 Nome amigável  
 Um nome amigável ou comum do indivíduo ou autoridade de certificação para o qual o certificado é emitido.  
  
 Emitido por  
 Informações relativas à autoridade de certificação que emitiu o certificado.  
  
 Emitido para  
 Informações relativas ao destinatário do certificado.  
  
  
