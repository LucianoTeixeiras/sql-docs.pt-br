---
title: srv_parammaxlen (API de Procedimento Armazenado Estendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_parammaxlen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f86d56a9f9b2d490a1cb3043d9b0761a05a848fa
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657655"
---
# <a name="srvparammaxlen-extended-stored-procedure-api"></a>srv_parammaxlen (API de procedimento armazenado estendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Em vez disso, use a Integração CLR.  
  
 Retorna o comprimento máximo de dados de um parâmetro de chamada de procedimento armazenado remoto. Essa função foi substituída pela função **srv_paraminfo**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 É um ponteiro para a estrutura SRV_PROC que identifica uma conexão de cliente específica (nesse caso, o identificador que recebeu a chamada do procedimento armazenado remoto). A estrutura contém informações que a biblioteca de APIs de procedimento armazenado estendido usa para gerenciar a comunicação e os dados entre o aplicativo e o cliente.  
  
 *n*  
 Indica o número do parâmetro. O primeiro parâmetro é 1.  
  
## <a name="returns"></a>Retorna  
 O comprimento máximo, em bytes, dos dados do parâmetro. Se não houver *n*-ésimo parâmetro nem procedimento armazenado remoto, o valor retornado será -1.  
  
 Essa função retornará os valores a seguir se o parâmetro for um dos tipos de dados do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a seguir.  
  
|Novos tipos de dados|Comprimento dos dados de entrada|  
|--------------------|-----------------------|  
|**BITN**|**NULL:** 1<br /><br /> **ZERO:** 1<br /><br /> **>=255:** N/A<br /><br /> **<255:** N/A|  
|**BIGVARCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**BIGCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**BIGBINARY**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**BIGVARBINARY**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**NCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**NVARCHAR**|**NULL:** 255<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**NTEXT**|**NULL:** -1<br /><br /> **ZERO:** -1<br /><br /> **>=255:** -1<br /><br /> **\<255:** -1|  
  
## <a name="remarks"></a>Remarks  
 Cada parâmetro de procedimento armazenado remoto tem um comprimento de dados real e um máximo. Para tipos de dados padrão de comprimento fixo que não permitem valores nulos, os comprimentos real e máximo são os mesmos. Para tipos de dados de comprimento de variável, os comprimentos podem variar. Por exemplo, um parâmetro declarado como **varchar(30)** pode ter dados de apenas 10 bytes de comprimento. O comprimento real do parâmetro é 10 e seu comprimento máximo é 30. A função **srv_parammaxlen** obtém o tamanho máximo de dados de um procedimento armazenado remoto. Para obter o tamanho real de um parâmetro, use **srv_paramlen**.  
  
 Quando uma chamada de procedimento armazenado remoto é feita com parâmetros, os parâmetros podem ser passados pelo nome ou pela posição (sem-nome). Se a chamada de procedimento armazenado remoto for feita com alguns parâmetros transmitidos pelo nome e outros pela posição, ocorrerá um erro. O manipulador SRV_RPC ainda é chamado, mas aparece como se não houvesse parâmetros e **srv_rpcparams** retorna 0.  
  
> [!IMPORTANT]  
>  Você deve examinar totalmente o código-fonte de procedimentos armazenados estendidos e deve testar as DLLs compiladas antes de instalá-las em um servidor de produção. Para obter informações sobre revisão e testes de segurança, consulte este [site da Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte Também  
 [srv_paraminfo &#40;API de Procedimento Armazenado Estendido&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams &#40;API de Procedimento Armazenado Estendido&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
