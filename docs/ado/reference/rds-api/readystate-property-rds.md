---
title: Propriedade ReadyState (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c575683b5ec23c6739a37eae177be004efea0a57
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51599897"
---
# <a name="readystate-property-rds"></a>Propriedade ReadyState (RDS)
Indica o progresso de uma [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) do objeto conforme ele recupera dados em seus [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (consulte o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Devem ser migrados para aplicativos que usam o RDS [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>As configurações e valores de retorno  
 Define ou retorna um dos valores a seguir.  
  
|Valor|Description|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|A consulta atual ainda está em execução e sem linhas foram buscadas. O **DataControl** do objeto **Recordset** não está disponível para uso.|  
|**adcReadyStateInteractive**|Um conjunto inicial de linhas recuperadas pela consulta atual foi armazenado na **DataControl** do objeto **Recordset** e estão disponíveis para uso. As linhas restantes ainda estão sendo buscadas.|  
|**adcReadyStateComplete**|Todas as linhas recuperadas pela consulta atual foram armazenadas em do **DataControl** do objeto **Recordset** e estão disponíveis para uso.<br /><br /> Esse estado também existirão se uma operação anulada devido a um erro ou se o **Recordset** objeto não foi inicializado.|  
  
> [!NOTE]
>  Cada arquivo executável do lado do cliente que usa constantes deve fornecer declarações para eles. Você pode recortar e colar as declarações de constante desejada do arquivo Adcvbs.inc, localizado na pasta de instalação padrão para a biblioteca RDS.  
  
## <a name="remarks"></a>Comentários  
 Use o [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) evento para monitorar as alterações na **ReadyState** propriedade durante uma operação de consulta assíncrona. Isso é mais eficiente do que periodicamente para verificar o valor da propriedade.  
  
 Se ocorrer um erro durante uma operação assíncrona, o **ReadyState** alteração na propriedade **adcReadyStateComplete**, o [estado](../../../ado/reference/ado-api/state-property-ado.md) propriedade muda de **adStateExecuting** para **adStateClosed**e o **conjunto de registros** objeto [valor](../../../ado/reference/ado-api/value-property-ado.md) propriedade permanece *nada* .  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo da propriedade ReadyState (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Método Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Propriedade ExecuteOptions (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


