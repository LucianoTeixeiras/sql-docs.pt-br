---
title: Configurações globais (caixas de diálogo) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c0ac65e0973ac9e862a73dd9c04a916156c8a314
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750245"
---
# <a name="global-settings-dialogs-db2tosql"></a>Configurações globais (caixas de diálogo) (DB2ToSQL)
Use a página de caixas de diálogo do **configurações globais** caixa de diálogo para especificar as configurações de aviso para o SSMA e uma ação do usuário padrão.  
  
Para acessar as configurações de caixa de diálogo sobre o **ferramentas** menu, selecione **configurações globais**, clique em **GUI** na parte inferior do painel esquerdo e, em seguida, selecione **caixas de diálogo**.  
  
## <a name="options"></a>Opções  
**Avisar antes de substituir os objetos**  
Quando o SSMA converte objetos para o SQL Server, alguns objetos talvez já exista nos metadados do SQL Server do projeto. Esses objetos podem já foram convertidos ou os objetos simplesmente podem ter o mesmo nome dentro do esquema de destino que objetos que serão convertidas.  
  
Use esta opção para especificar se o SSMA solicitará que você para substituir as definições de objeto duplicados:  
  
-   Se você selecionar **verdadeira**, SSMA exibirá uma caixa de diálogo de aviso quando ele encontra um objeto duplicado. Nesta caixa de diálogo, você pode especificar para substituir os objetos individuais ou todos os objetos duplicados ou para ignorar objetos individuais ou para todos os objetos duplicados.  
  
-   Se você selecionar **falsos**, o **ação padrão de substituição de objeto** opção é exibida em que você especifica a ação padrão.  
  
**Ação de padrão de substituição de objeto**  
Essa opção aparecerá se você selecionar **falsos** para o **Avisar antes de substituir objetos** opção.  
  
Use esta opção para especificar o comportamento de substituição de objeto padrão:  
  
-   Se você selecionar **verdadeira**, SSMA substituirá automaticamente os objetos nos metadados do projeto do SQL Server que têm o mesmo nome e estão no mesmo esquema de destino como o objeto a ser convertido.  
  
-   Se você selecionar **falsos**, SSMA não substitui os metadados de objeto durante a conversão.  
  
