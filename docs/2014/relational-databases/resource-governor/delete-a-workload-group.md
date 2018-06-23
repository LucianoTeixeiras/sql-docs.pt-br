---
title: Excluir um grupo de carga de trabalho | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 793052419843c2e2421458da07b2815932683645
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36007266"
---
# <a name="delete-a-workload-group"></a>Excluir um grupo de carga de trabalho
  É possível excluir um grupo de carga de trabalho ou um pool de recursos usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To delete a workload group, using:**  [Object Explorer](#DelWGObjEx), [Resource Governor Properties](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
 Não é possível excluir um grupo de carga de trabalho se ele contiver sessões ativas.  
  
###  <a name="LimitationsRestrictions"></a> Limitações e Restrições  
 Se um grupo de cargas de trabalho contiver sessões ativas, a exclusão ou movimentação do grupo de cargas de trabalho para um pool de recursos diferente não terá êxito quando a instrução ALTER RESOURCE GOVERNOR RECONFIGURE for chamada para aplicar a alteração. Para evitar esse problema, é possível executar uma das seguintes ações:  
  
-   Aguardar até que todas as sessões do grupo afetado sejam desconectadas e depois executar novamente a instrução ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Interromper explicitamente as sessões do grupo afetado usando o comando KILL e depois executar novamente a instrução ALTER RESOURCE GOVERNOR RECONFIGURE. Se você decidir que não deseja interromper explicitamente as sessões depois de usar **Excluir** , mas antes de interromper as sessões ativas, recrie o grupo usando o nome original e mova o grupo para o pool de recursos original.  
  
-   Reinicie o servidor. Depois que o processo de reinicialização estiver concluído, o grupo excluído não será criado e um grupo movido usará a atribuição do novo pool de recursos.  
  
###  <a name="Permissions"></a> Permissões  
 Excluir um grupo de cargas de trabalho exige permissão CONTROL SERVER.  
  
##  <a name="DelWGObjEx"></a> Excluir um grupo de cargas de trabalho usando o Pesquisador de Objetos  
 **Para excluir um grupo de cargas de trabalho usando o Pesquisador de Objetos**  
  
1.  No[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], abra o Pesquisador de Objetos e expanda recursivamente o nó **Gerenciamento** para baixo e inclua o **Pools de Recursos**.  
  
2.  Expanda recursivamente o nó **Pools de Recursos** para baixo e incluindo o nó **Grupos de Cargas de Trabalho** no pool de recursos que contém o grupo de cargas de trabalho a ser excluído.  
  
3.  Clique com o botão direito do mouse em grupo de cargas de trabalho e clique em **Excluir**.  
  
4.  Na janela **Excluir Objeto** , o grupo de carga de trabalho é listado em **Objeto a ser excluído** . Para excluir o grupo de cargas de trabalho, clique em **OK**.  
  
##  <a name="DelWGRGProp"></a> Excluir um grupo de cargas de trabalho usando propriedades do administrador de recursos  
 **Para excluir um grupo de cargas de trabalho usando a página de propriedades do administrador de recursos**  
  
1.  No Pesquisador de Objetos, expanda recursivamente o nó **Gerenciamento** para baixo e incluindo **Pools de Recursos**.  
  
2.  Clique com o botão direito do mouse no pool de recursos que contém o grupo de cargas de trabalho a ser excluído e clique em **Propriedades**. Isso abre a página **Propriedades do Administrador de Recursos** .  
  
3.  Na janela **Grupos de cargas de trabalho para o pool de recursos** , clique na linha do grupo de cargas de trabalho a ser excluído, clique com o botão direito do mouse na seta para a direita no lado esquerdo da linha e clique em **Excluir**.  
  
4.  Para excluir o grupo de cargas de trabalho, clique em **OK**.  
  
##  <a name="DelWGTSQL"></a> Excluir grupo de cargas de trabalho usando Transact-SQL  
 **Para mover um grupo de cargas de trabalho usando Transact-SQL**  
  
1.  Execute o `DROP WORKLOAD GROUP` instrução especificando o nome do grupo de carga de trabalho para excluir.  
  
2.  Antes de emitir a instrução `ALTER RESOURCE GOVERNOR RECONFIGURE`, verifique se não há solicitações ativas no grupo de cargas de trabalho que está sendo excluído. Se houver solicitações ativas, `ALTER RESOURCE GOVERNOR` falhará. Para evitar esse problema, é possível executar uma das seguintes ações:  
  
    -   Aguarde até que todas as sessões do grupo de carga de trabalho estejam desconectadas.  
  
    -   Explicitamente pare sessões no grupo de cargas de trabalho usando o comando `KILL`.  
  
    -   Reinicie o servidor. O grupo de cargas de trabalho não será recriado.  
  
    -   Em um cenário no qual você emitiu a instrução `DROP WORKLOAD GROUP` mas decide que não deseja parar sessões explicitamente para aplicar a mudança, é possível recriar o grupo usando o mesmo nome que ele tinha antes de você emitir a instrução DROP e depois mover o grupo para o pool de recursos original.  
  
3.  Execute o `ALTER RESOURCE GOVERNOR RECONFIGURE` instrução.  
  
### <a name="example-transact-sql"></a>Exemplo (Transact-SQL)  
 O seguinte exemplo descarta um grupo de carga de trabalho denominado `groupAdhoc`.  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Administrador de Recursos](resource-governor.md)   
 [Criar um pool de recursos](create-a-resource-pool.md)   
 [Criar um grupo de carga de trabalho](create-a-workload-group.md)   
 [Excluir um pool de recursos](delete-a-resource-pool.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  