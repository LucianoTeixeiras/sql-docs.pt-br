---
title: sp_helpmergearticle (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticle
- sp_helpmergearticle_TSQL
helpviewer_keywords:
- sp_helpmergearticle
ms.assetid: 0fb9986a-3c33-46ef-87bb-297396ea5a6a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7a103f309067b5e78024a1687c24bb37bf5c3a8b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779748"
---
# <a name="sphelpmergearticle-transact-sql"></a>sp_helpmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações sobre um artigo. Esse procedimento armazenado é executado no Publicador no banco de dados de publicação ou em um Assinante de republicação no banco de dados de assinatura.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções de sintaxe de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpmergearticle [ [ @publication = ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=**] **'***publicação***'**  
 É o nome da publicação sobre a qual recuperar informações. *publicação*está **sysname**, com um padrão de **%**, que retorna informações sobre todos os artigos de mesclagem contidos em todas as publicações no banco de dados atual.  
  
 [  **@article=**] **'***artigo***'**  
 É o nome do artigo do qual retornar informações. *artigo*está **sysname**, com um padrão de **%**, que retorna informações sobre todos os artigos de mesclagem na determinada publicação.  
  
## <a name="result-set"></a>Conjunto de resultados  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identificador do artigo.|  
|**name**|**sysname**|Nome do artigo.|  
|**source_owner**|**sysname**|Nome do proprietário do objeto de origem.|  
|**source_object**|**sysname**|Nome do objeto de origem do qual adicionar o artigo.|  
|**sync_object_owner**|**sysname**|Nome do proprietário da exibição que define o artigo publicado.|  
|**sync_object**|**sysname**|Nome do objeto personalizado usado para estabelecer os dados iniciais para a partição.|  
|**description**|**nvarchar(255)**|Descrição do artigo.|  
|**status**|**tinyint**|Estado do artigo que pode ser um dos seguintes:<br /><br /> **1** = inativo<br /><br /> **2** = Active Directory<br /><br /> **5** = operação de DDL (linguagem) de definição de dados pendentes<br /><br /> **6** = operações DDL com um instantâneo recém-gerado<br /><br /> Observação: Quando um artigo é reiniciado, valores de **5** e **6** são alterados para **2**.|  
|**creation_script**|**nvarchar(255)**|Caminho e nome de um script de esquema de artigo opcional usados para criar o artigo no banco de dados de assinatura.|  
|**conflict_table**|**nvarchar(270)**|Nome da tabela que armazena os conflitos de entrada ou atualização.|  
|**article_resolver**|**nvarchar(255)**|Resolvedor personalizado para o artigo.|  
|**subset_filterclause**|**nvarchar(1000)**|Cláusula WHERE especificando filtragem horizontal.|  
|**pre_creation_command**|**tinyint**|Método de pré-criação, que pode ser um dos seguintes:<br /><br /> **0** = nenhum<br /><br /> **1** = descartar<br /><br /> **2** = excluir<br /><br /> **3** = truncar|  
|**schema_option**|**binary(8)**|Bitmap da opção de geração de esquema para o artigo. Para obter informações sobre essa opção de bitmap, consulte [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) ou [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md).|  
|**type**|**smallint**|Tipo do artigo que pode ser um dos seguintes:<br /><br /> **10** = tabela<br /><br /> **32** = procedimento armazenado<br /><br /> **64** = exibição ou exibição indexada<br /><br /> **128** = função definida pelo usuário<br /><br /> **160** = somente esquema sinônimo|  
|**column_tracking**|**int**|Configuração para acompanhamento de nível de coluna. em que **1** significa que o controle em nível de coluna está ativada, e **0** significa que o controle em nível de coluna está desativado.|  
|**resolver_info**|**nvarchar(255)**|Nome do resolvedor do artigo.|  
|**vertical_partition**|**bit**|Se o artigo estiver particionado verticalmente; em que **1** significa que o artigo está verticalmente particionado e **0** significa que não é.|  
|**destination_owner**|**sysname**|Proprietário do objeto de destino. Aplicável apenas em procedimentos armazenados de mesclagem, exibições e artigos de esquema UDF (função definida pelo usuário).|  
|**identity_support**|**int**|Se o tratamento de intervalo de identidade automático estiver habilitado; em que **1** está habilitado e **0** está desabilitado.|  
|**pub_identity_range**|**bigint**|O tamanho de intervalo a ser usado ao atribuir novos valores de identidade. Para obter mais informações, consulte a seção "Replicação de mesclagem" do [replicar colunas de identidade](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**identity_range**|**bigint**|O tamanho de intervalo a ser usado ao atribuir novos valores de identidade. Para obter mais informações, consulte a seção "Replicação de mesclagem" do [replicar colunas de identidade](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**threshold**|**int**|Valor de porcentagem usado por assinantes que executam [!INCLUDE[ssEW](../../includes/ssew-md.md)] ou versões anteriores do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **limite** controla quando o Merge Agent atribui um novo intervalo de identidade. Quando a porcentagem de valores especificada no limite é usada, o Merge Agent cria um novo intervalo de identidade. Para obter mais informações, consulte a seção "Replicação de mesclagem" do [replicar colunas de identidade](../../relational-databases/replication/publish/replicate-identity-columns.md).|  
|**verify_resolver_signature**|**int**|Se uma assinatura digital é verificada antes de usar um resolvedor em replicação de mesclagem; em que **0** significa que a assinatura não for verificada, e **1** significa que a assinatura é verificada para ver se ele é de uma fonte confiável.|  
|**destination_object**|**sysname**|Nome do objeto de destino. Aplicável apenas a procedimentos armazenados de mesclagem, exibições e artigos de esquema UDF.|  
|**allow_interactive_resolver**|**int**|Se o resolvedor interativo é usado em um artigo; em que **1** significa que esse resolvedor é usado, e **0** significa que não é usada.|  
|**fast_multicol_updateproc**|**int**|Habilita ou desabilita o Merge Agent para aplicar as alterações em várias colunas na mesma linha em uma instrução UPDATE; em que **1** significa que várias colunas são atualizadas em uma instrução, e **0** significa que instruções UPDATE separadas são problemas para cada coluna atualizada.|  
|**check_permissions**|**int**|Valor inteiro que representa o bitmap de permissões de nível de tabela verificadas. Para obter uma lista de valores possíveis, consulte [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**processing_order**|**int**|A ordem na qual as alterações de dados são aplicadas a artigos em uma publicação.|  
|**upload_options**|**tinyint**|Define restrições em atualizações feitas em um Assinante com uma assinatura de cliente, que pode ser um dos valores a seguir.<br /><br /> **0** = não há restrições em atualizações feitas em um assinante com assinatura de cliente; todas as alterações são carregadas no publicador.<br /><br /> **1** = as alterações são permitidas em um assinante com assinatura de cliente, mas eles não são carregados no publicador.<br /><br /> **2** = não são permitidas alterações em um assinante com assinatura de cliente.<br /><br /> Para obter mais informações, consulte [Optimize Merge Replication Performance with Download-Only Articles](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md) (Otimizar o desempenho da replicação de mesclagem com artigos somente para download).|  
|**identityrangemanagementoption**|**int**|Se o tratamento de intervalo de identidade automático estiver habilitado; em que **1** está habilitado e **0** está desabilitado.|  
|**delete_tracking**|**bit**|Se as exclusões são replicadas; em que **1** significa que as exclusões são replicadas, e **0** significa que eles não são.|  
|**compensate_for_errors**|**bit**|Indica se ações compensatórias são tomadas quando forem encontrados erros durante a sincronização. em que **1** indica que as ações compensatórias são tomadas, e **0** significa que as ações de compensação não são executadas.|  
|**partition_options**|**tinyint**|Define a forma pela qual os dados no artigo são particionados, o que habilita otimizações de desempenho quando todas as linhas pertencem a apenas uma partição ou assinatura. *partition_options* pode ser um dos valores a seguir.<br /><br /> **0** = a filtragem do artigo é estática ou não produz um único subconjunto de dados para cada partição; ou seja, ele é uma partição "sobreposta".<br /><br /> **1** = as partições são sobrepostas e as atualizações da DML (linguagem) de manipulação de dados feitas no assinante não podem alterar a partição à qual uma linha pertence.<br /><br /> **2** = a filtragem para o artigo gera partições não sobrepostas, mas vários assinantes podem receber a mesma partição.<br /><br /> **3** = a filtragem para o artigo gera partições não sobrepostas exclusivas de cada assinatura.|  
|**artid**|**uniqueidentifier**|Um identificador que identifica exclusivamente o artigo.|  
|**pubid**|**uniqueidentifier**|Um identificador que identifica exclusivamente a publicação na qual o artigo é publicado.|  
|**stream_blob_columns**|**bit**|Se a otimização de fluxo de dados for usada ao replicar colunas de objeto binário grande. **1** significa que a otimização está sendo usada, e **0** significa que a otimização não está sendo usada.|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_helpmergearticle** é usado em replicação de mesclagem.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros dos **db_owner** função de banco de dados fixa no banco de dados de publicação, o **replmonitor** no banco de dados de distribuição ou a lista de acesso à publicação para uma publicação podem executar **sp_helpmergearticle**.  
  
## <a name="example"></a>Exemplo  
 [!code-sql[HowTo#sp_helpmergearticle](../../relational-databases/replication/codesnippet/tsql/sp-helpmergearticle-tran_1.sql)]  
  
## <a name="see-also"></a>Consulte também  
 [Exibir e modificar propriedades do artigo](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [Procedimentos armazenados de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
