---
title: Abrir, desbloquear, renomear e excluir um projeto de qualidade de dados | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5ead34cab28f4988f649c6bc9dcfec5d282a08f1
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617816"
---
# <a name="open-unlock-rename-and-delete-a-data-quality-project"></a>Abrir, desbloquear, renomear e excluir um projeto do Data Quality

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Este tópico descreve como gerenciar um projeto de qualidade de dados usando o [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , por exemplo, como abrir, desbloquear, renomear e excluir um projeto de qualidade de dados.  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="LimitationsRestrictions"></a> Limitações e restrições  
  
-   Você não pode abrir um projeto bloqueado criado por outro usuário.  
  
-   Você não pode desbloquear, renomear ou excluir um projeto de qualidade de dados criado por outro usuário.  
  
-   Você não pode excluir um projeto de qualidade de dados bloqueado. Primeiro você deve desbloqueá-lo para excluir.  
  
-   Você somente pode desbloquear um projeto de qualidade de dados criado por você.  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
 Você deve ter pelo menos um projeto de qualidade de dados para gerenciar.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você deve ter a função dqs_kb_editor ou dqs_kb_operator no banco de dados DQS_MAIN para gerenciar um projeto de qualidade de dados.  
  
##  <a name="Open"></a> Abrir um projeto de qualidade de dados  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Executar o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Abrir projeto de qualidade de dados**. A tela **Abrir projeto** é aberta.  
  
     Alternativamente, você pode abrir, de modo direto, um projeto de qualidade de dados listado em **Projeto de qualidade de dados recente** clicando nele.  
  
3.  Na tela **Abrir projeto** , clique para selecionar o projeto de qualidade de dados que você deseja abrir e clique em **Avançar**.  
  
4.  O projeto de qualidade de dados é aberto no mesmo estado da atividade quando foi fechado pela última vez. Um projeto de qualidade de dados tem os seguintes estados:  
  
    -   Para a atividade **Limpeza**, um projeto de qualidade de dados pode ter os seguintes estados: **Limpeza – Mapa**, **Limpeza – Limpar**, **Limpeza – Gerenciar e Exibir Resultados** e **Limpeza – Exportar**.  
  
    -   Para a atividade **Correspondência**, um projeto de qualidade de dados pode ter os seguintes estados: **Correspondência – Mapa**, **Correspondência – Correspondência**, **Correspondência – Sobrevivência** e **Correspondência – Exportar**.  
  
##  <a name="Unlock"></a> Desbloquear um projeto de qualidade de dados  
 Quando você cria um projeto de qualidade de dados, ele permanece em estado bloqueado para impedir seu uso ou modificação por outros usuários. Você deverá desbloquear o projeto de qualidade de dados depois de concluir seu trabalho se quiser que outros usuários trabalhem no seu projeto de qualidade de dados. Um símbolo de bloqueio é exibido para projetos que estão bloqueados.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Executar o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Abrir projeto de qualidade de dados**. A tela **Abrir projeto** é aberta.  
  
3.  Na tela **Abrir projeto** , clique com o botão direito do mouse no projeto de qualidade de dados bloqueado criado por você e clique em **Desbloquear** no menu de atalho. Uma marca de seleção verde é exibida para o projeto, indicando que ele está desbloqueado.  
  
##  <a name="Rename"></a> Renomear um projeto de qualidade de dados  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Executar o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Abrir projeto de qualidade de dados**. A tela **Abrir projeto** é aberta.  
  
3.  Na tela **Abrir projeto** , clique com o botão direito do mouse no projeto de qualidade de dados criado por você e clique em **Renomear** no menu de atalho.  
  
4.  O nome de projeto de qualidade de dados fica editável na coluna **Nome** . Digite um novo nome e pressione Enter.  
  
##  <a name="Delete"></a> Excluir um projeto de qualidade de dados  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Executar o aplicativo Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , clique em **Abrir projeto de qualidade de dados**. A tela **Abrir projeto** é aberta.  
  
3.  Na tela **Abrir projeto** , clique com o botão direito do mouse em um projeto de qualidade de dados desbloqueado criado por você e clique em **Excluir** no menu de atalho.  
  
4.  Uma mensagem de confirmação é exibida. Clique em **Sim**.  
  
  
