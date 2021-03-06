---
title: Alterando um Assembly | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9c6b6f864f5935ab6e814c3ceac822a930e25952
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771644"
---
# <a name="altering-an-assembly"></a>Alterando um assembly
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Os assemblies que foram registrados no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] podem ser atualizados de uma versão mais recente que use a instrução ALTER ASSEMBLY. Para atualizar um assembly, use a instrução ALTER ASSEMBLY com a seguinte sintaxe:  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 A instrução ALTER ASSEMBLY não interrompe processos em execução que estejam usando o assembly; os processos continuam executando com o assembly inalterado. ALTER ASSEMBLY não pode ser usada para alterar as assinaturas de funções CLR (Common Language Runtime), funções de agregação, procedimentos armazenados e gatilhos. Novos métodos públicos podem ser adicionados ao assembly, métodos particulares podem ser modificados de alguma forma e métodos públicos podem ser modificados enquanto assinaturas ou atributos não são alterados. Os campos contidos em um tipo definido pelo usuário serializado nativo, incluindo membros de dados ou classes base, não podem ser alterados com o uso de ALTER ASSEMBLY. Não é oferecido suporte a todas as demais alterações. Para obter mais informações, consulte [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Alterando o conjunto de permissões de um assembly  
 O conjunto de permissões de um assembly pode também ser alterado com a instrução ALTER ASSEMBLY. A instrução a seguir altera o conjunto de permissões do assembly SQLCLRTest para **EXTERNAL_ACCESS**.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Se o conjunto de permissões de um assembly é alterado de **seguro** à **EXTERNAL_ACCESS** ou **UNSAFE**, uma chave assimétrica e um logon correspondente com  **EXTERNAL ACCESS ASSEMBLY** permissão ou **UNSAFE ASSEMBLY** permissão para o assembly deve primeiramente ser criada. Para obter mais informações, consulte [Criando um assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Adicionando o código-fonte de um assembly  
 A cláusula ADD FILE na sintaxe ALTER ASSEMBLY não está presente em CREATE ASSEMBLY. Você pode usá-la para adicionar código-fonte ou outros arquivos associados a um assembly. Os arquivos serão copiados dos seus locais originais e armazenados em tabelas do sistema do banco de dados. Isso garante que você sempre tenha código-fonte ou outros arquivos à mão, se precisar recriar ou documentar a versão atual do UDT.  
  
 A instrução a seguir adiciona o código-fonte de classe Point.cs para o UDT Point. O texto contendo o arquivo Point.cs será copiado e armazenado no banco de dados com o nome "PointSource".  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando Assemblies de integração CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Criando um Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Descarte de um Assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
