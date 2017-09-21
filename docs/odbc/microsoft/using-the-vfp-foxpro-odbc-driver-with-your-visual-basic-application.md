---
title: Usar o Driver ODBC FoxPro VFP com seu aplicativo Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 37834afc7cc69e0276645d68752e66f68449fbb3
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Usando o Driver ODBC FoxPro VFP com seu aplicativo Visual Basic
Aplicativo do Microsoft® Visual Basic® pode se comunicar com os dados do Visual FoxPro, criando um controle de dados que se conecta a uma fonte de dados do Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Para se conectar a dados do Visual FoxPro usando o controle de dados no Visual Basic  
  
1.  Crie uma fonte de dados chamada "test" que se conecta ao banco de dados de exemplo TasTrade incluído no Visual FoxPro. A instalação padrão do Visual FoxPro coloca o banco de dados de exemplo TasTrade no local:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  No Visual Basic, crie um novo formulário e coloque uma caixa de texto e um controle de dados nele.  
  
3.  Altere a propriedade de conexão do controle de dados da seguinte maneira:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Altere a propriedade TipoDeConjuntoDeRegistros para o seguinte:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Altere a propriedade OrigemDoRegistro para o seguinte:  
  
    ```  
    customer  
    ```  
  
6.  Altere a propriedade de fonte de dados da caixa de texto para o nome padrão para o controle de dados para o seguinte:  
  
    ```  
    data1  
    ```  
  
7.  Altere a propriedade DataField da caixa de texto para o seguinte:  
  
    ```  
    customer_id  
    ```  
  
8.  Executar o formulário e use o controle de dados para saltar entre os campos id do cliente do banco de dados de exemplo TasTrade do Visual FoxPro.