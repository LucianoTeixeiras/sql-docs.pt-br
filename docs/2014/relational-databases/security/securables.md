---
title: Protegíveis | Microsoft Docs
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
caps.latest.revision: 36
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b2679a2583b21ba1015b9b54e5e1662c9e89bf5d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36130729"
---
# <a name="securables"></a>Protegíveis
  Protegíveis são os recursos cujo acesso é regulado pelo sistema de autorização do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Por exemplo, uma tabela é um protegível. Alguns protegíveis podem ser contidos dentro de outros, criando hierarquias aninhadas chamadas "escopos" que podem ser protegidos. Os escopos protegíveis são **servidor**, **banco de dados**e **esquema**.  
  
## <a name="securable-scope-server"></a>Escopo protegível: servidor  
 O escopo protegível **servidor** contém os seguintes protegíveis:  
  
-   grupo de disponibilidade  
  
-   Ponto de extremidade  
  
-   Logon  
  
-   Função de servidor  
  
-   banco de dados  
  
## <a name="securable-scope-database"></a>Escopo protegível: banco de dados  
 O escopo protegível **banco de dados** contém os seguintes protegíveis:  
  
-   Função de aplicativo  
  
-   Assembly  
  
-   Chave assimétrica  
  
-   Certificado  
  
-   Contrato  
  
-   Catálogo de texto completo  
  
-   Lista de palavras irrelevantes completa  
  
-   Tipo de mensagem  
  
-   Associação de serviço remoto  
  
-   Função (banco de dados)  
  
-   Rota  
  
-   esquema  
  
-   Lista de propriedades de pesquisa  
  
-   Serviço  
  
-   Chave simétrica  
  
-   Usuário  
  
## <a name="securable-scope-schema"></a>Escopo protegível: esquema  
 O escopo protegível **esquema** contém os seguintes protegíveis:  
  
-   Tipo  
  
-   Coleção de esquemas XML  
  
-   Objeto – A classe de objeto tem os seguintes membros:  
  
    -   Agregado  
  
    -   Função  
  
    -   Procedimento  
  
    -   Fila  
  
    -   Sinônimo  
  
    -   Table  
  
    -   Exibição  
  
## <a name="controlling-access-to-a-securable"></a>Controlando o acesso a um protegível  
 A entidade que recebe permissão para um protegível é chamada de entidade de segurança. As entidades de segurança mais comuns são logons e usuários de banco de dados. O acesso a protegíveis é controlado pela concessão ou negação de permissões, ou pela adição de logons e de usuários a funções que têm acesso. Para obter informações sobre como controlar permissões, veja [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) e [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).  
  
> [!CAUTION]  
>  As permissões padrão concedidas aos objetos de sistema no momento da instalação são avaliadas cuidadosamente contra possíveis ameaças e não precisam ser alteradas como parte do sistema de proteção de instalação do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Qualquer alteração nas permissões nos objetos de sistema poderia limitar ou interromper a funcionalidade e potencialmente pode deixar a instalação do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] em um estado sem suporte.  
  
## <a name="related-content"></a>Conteúdo relacionado  
 [Protegendo o SQL Server](securing-sql-server.md)  
  
 [sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [sys.server_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  