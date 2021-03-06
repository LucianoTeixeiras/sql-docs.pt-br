---
title: pdw_dms_external_work (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 47345015-f861-451e-97c4-6e1cb81d1922
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9c80038b344a942068f040bde040d4a9a29edcae
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419308"
---
# <a name="sysdmpdwdmsexternalwork-transact-sql"></a>sys.dm_pdw_dms_external_work (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] exibição do sistema que contém informações sobre todas as etapas de serviço de movimentação de dados (DMS) para operações externas.  
  
|Nome da coluna|Tipo de Dados|Descrição|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Consulta que está usando este trabalhador DMS.<br /><br /> request_id, step_index e dms_step_index formam a chave para esta exibição.|Mesmo que request_id na [DM pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Etapa de consulta que está invocando este trabalhador DMS.<br /><br /> request_id, step_index e dms_step_index formam a chave para esta exibição.|Mesmo que step_index na [DM pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Etapa atual no plano de DMS.<br /><br /> request_id, step_index e dms_step_index formam a chave para esta exibição.|Mesmo que dms___step_index na [DM pdw_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md).|  
|pdw_node_id|**int**|Nó que está executando o trabalho do DMS.|Mesmo que node_id na [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|Tipo|**nvarchar(60)**|Tipo de operação externa que este nó está em execução.<br /><br /> Dividir arquivo é uma operação em um arquivo do Hadoop externo que foi dividido em vários cai menores.|'DIVISÃO DE ARQUIVO'|  
|work_id|**int**|O arquivo dividido ID.|Maior que ou igual a 0.<br /><br /> Exclusivo por nó de computação.|  
|input_name|**nvarchar(60)**|Nome para a entrada que está sendo lida de cadeia de caracteres.|Para um arquivo do Hadoop, esse é o nome de arquivo do Hadoop.|  
|read_location|**bigint**|Deslocamento do local de leitura.||  
|estimated_bytes_processed|**bigint**|Número de bytes processados por este trabalhador.|Maior que ou igual a 0.|  
|comprimento|**bigint**|Número de bytes no arquivo de divisão.<br /><br /> Para Hadoop, esse é o tamanho do bloco de HDFS.|Definido pelo usuário. O padrão é 64 MB.|  
|status|**nvarchar(32)**|Estado do trabalhador.|Pendente, processando, concluído, falha, anulado|  
|start_time|**datetime**|Hora de início a execução deste trabalhador.|Maior que ou igual à hora de início da etapa de consulta esse trabalho pertence. Ver [DM pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|end_time|**datetime**|Hora em que a execução foi encerrado, falhou ou foi cancelada.|NULL para os trabalhos em andamento ou em fila. Caso contrário, maior que start_time.|  
|total_elapsed_time|**int**|Tempo total gasto na execução, em milissegundos.|Maior que ou igual a 0.<br /><br /> Se total_elapsed_time exceder o valor máximo para um número inteiro, o total_elapsed_time continuará a ser o valor máximo. Essa condição gerará o aviso "o valor máximo foi excedido."<br /><br /> O valor máximo em milissegundos é equivalente a 24,8 dias.|  
  
 Para obter informações sobre o máximo de linhas mantido por esta exibição, consulte [valores máximos de modo de exibição de sistema](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições do sistema &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
