---
title: sp_setapprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 78cf616c0b09d1404f0c7e7fe5f3b382f08d59a8
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168795"
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ativa as permissões associadas a uma função de aplicativo no banco de dados atual.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>Argumentos

 [  **@rolename =** ] **'***função***'**  
 É o nome da função de aplicativo definida no banco de dados atual. *função* está **sysname**, sem padrão. *função* deve existir no banco de dados atual.  
  
 [  **@password =** ] **{criptografar N'***senha***'}**  
 É a senha necessária para ativar a função de aplicativo. *senha* está **sysname**, sem padrão. *senha* pode ser ofuscado usando o ODBC **criptografar** função. Quando você usa o **criptografar** função, a senha deve ser convertida em uma cadeia de caracteres Unicode colocando **N** antes da primeira marca de aspas simples.  
  
 Não há suporte para a opção de criptografia em conexões que usam **SqlClient**.  
  
> [!IMPORTANT]  
> O ODBC **criptografar** função não fornece criptografia. Você não deve confiar nessa função para proteger senhas que são transmitidas pela rede. Se essas informações forem transmitidas por uma rede, use SSL ou IPSec.
  
 **@encrypt = 'none'**  
 Especifica que nenhuma ofuscação deve ser usada. A senha é transmitida para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como texto sem-formatação. Esse é o padrão.  
  
 **@encrypt= 'odbc'**  
 Especifica que o ODBC será ofuscado pela senha usando o ODBC **criptografar** função antes de enviar a senha para o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Isso pode ser especificado somente quando um cliente ODBC ou o provedor OLE DB para SQL Server for utilizado.  
  
 [  **@fCreateCookie =** ] **verdadeira** | **false**  
 Especifica se um cookie deve ser criado. **True** é implicitamente convertido em 1. **False** é implicitamente convertido em 0.  
  
 [  **@cookie =** ]  **@cookie SAÍDA**  
 Especifica um parâmetro de saída para conter o cookie. O cookie é gerado apenas se o valor de **@fCreateCookie** é **true**. **varbinary(8000)**  
  
> [!NOTE]  
> O parâmetro **OUTPUT** de cookie para **sp_setapprole** está documentado atualmente como **varbinary(8000)** , que tem o tamanho máximo correto. No entanto, a implementação atual retorna **varbinary(50)**. Aplicativos devem continuar a reservar **varbinary(8000)** para que o aplicativo continue a operar corretamente se o cookie retornar aumentos de tamanho em uma versão futura.
  
## <a name="return-code-values"></a>Valores do código de retorno

 0 (êxito) e 1 (falha)  
  
## <a name="remarks"></a>Comentários

 Depois de um aplicativo de função for ativada por meio **sp_setapprole**, a função permanece ativa até que o usuário se desconecta do servidor ou executa **sp_unsetapprole**. **sp_setapprole** pode ser executado somente por direct [!INCLUDE[tsql](../../includes/tsql-md.md)] instruções. **sp_setapprole** não pode ser executado em outro procedimento armazenado ou uma transação definida pelo usuário.  
  
 Para obter uma visão geral das funções de aplicativo, consulte [funções de aplicativo](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
> Para proteger a senha da função de aplicativo quando ele é transmitido em uma rede, você sempre deve usar uma conexão criptografada ao habilitar uma função de aplicativo.
> O [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC **criptografar** opção não é suportada pelo **SqlClient**. Se for necessário armazenar credenciais, criptografe-as com as funções da API de criptografia. O parâmetro *senha* é armazenado como um hash unidirecional. Para preservar a compatibilidade com versões anteriores do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], política de complexidade de senha não é imposta pelo **sp_addapprole**. Para impor a política de complexidade de senha, use [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Permissões

Requer associação na **pública** e conhecimento da senha para a função.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Ativando uma função de aplicativo sem a opção de criptografia

 O exemplo a seguir ativa uma função de aplicativo `SalesAppRole`, com a senha de texto sem-formatação `AsDeF00MbXX`, criada com permissões projetadas especificamente para o aplicativo usado pelo usuário atual.

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Ativando uma função de aplicativo com um cookie e revertendo para o contexto original

 O exemplo a seguir ativa a função de aplicativo `Sales11` com a senha `fdsd896#gfdbfdkjgh700mM` e cria um cookie. O exemplo retorna o nome do usuário atual e, em seguida, reverte para o contexto original executando `sp_unsetapprole`.  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>Consulte também

 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) [procedimentos armazenados de segurança &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [CREATE APPLICATION ROLE &#40;Transact-SQL&#41; ](../../t-sql/statements/create-application-role-transact-sql.md) [DROP APPLICATION ROLE &#40;Transact-SQL&#41; ](../../t-sql/statements/drop-application-role-transact-sql.md) [sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
