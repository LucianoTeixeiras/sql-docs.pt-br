---
title: Instalar o SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a90a30a0ae7fe09d49b1d42b577b13370c48c0de
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360928"
---
# <a name="install-sql-server-powershell"></a>Instalar o SQL Server PowerShell
  A instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parará se detectar que você selecionou recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que incluem componentes do PowerShell, mas o Windows PowerShell 2.0 não é instalado. Você deve instalar o PowerShell usando o Windows Management Framework e depois executar novamente a Instalação.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>Instalando o suporte do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Você instala o software que oferece suporte do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ao Windows PowerShell usando o programa de instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quando você seleciona qualquer recurso do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que exige suporte do PowerShell, a Instalação verifica se o Windows PowerShell 2.0 está instalado. Se o PowerShell 2.0 estiver presente, a Instalação instalará os seguintes componentes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell:  
  
-   Snap-ins do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Os snap-ins são arquivos dll que implementam dois tipos de suporte do Windows PowerShell ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   Conjunto de cmdlets do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Os cmdlets são comandos que implementam uma ação específica. Por exemplo, **Invoke-Sqlcmd** executa um script [!INCLUDE[tsql](../../includes/tsql-md.md)] ou XQuery que também pode ser executado usando o utilitário **sqlcmd** , e **Invoke-PolicyEvaluation** relata se os objetos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cumprem as políticas de gerenciamento baseadas em políticas.  
  
    -   Um provedor do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . O provedor permite navegar pela hierarquia dos objetos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando um caminho semelhante a um caminho de sistema de arquivos. Cada objeto é associado a uma classe de modelos de objeto de gerenciamento do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Você pode usar os métodos e as propriedades da classe para realizar trabalhos nos objetos. Por exemplo, se você usar cd para um objeto do banco de dados em um caminho, poderá usar os métodos e as propriedades da classe Microsoft.SqlServer.Managment.SMO.Database para gerenciar o banco de dados.  
  
-   O **sqlps** módulo é importado para sessões do Windows PowerShell 2.0 para carregar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-ins.  
  
-   Preteridas **sqlps** utilitário que inicia uma sessão do Windows PowerShell 2.0 e importa o **sqlps** módulo.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dá suporte à inicialização das sessões do Windows PowerShell por meio da árvore do Pesquisador de Objetos. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dá suporte às etapas de trabalho do Windows PowerShell.  
  
 Se Windows PowerShell 2.0 não foi instalado ou foi desinstalado, você deve instalá-lo seguindo as instruções o [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) página.  
  
 Se o Windows PowerShell for desinstalado após a conclusão da Instalação, os recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para Windows PowerShell não funcionarão. O Windows PowerShell pode ser desinstalado pelos usuários do Windows, e a desinstalação pode ser exigida por algumas atualizações do sistema operacional Windows. Para usar os recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, você deve reinstalar o PowerShell 2.0 usando o Windows Management Framework.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
