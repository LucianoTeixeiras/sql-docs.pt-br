---
title: 'Configurando o TLS 1.2 no Analytics Platform System | Microsoft Docs '
description: Recomendação para configurar o TLS 1.2 no APS
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 24e93c91c916272f71f137dd10bf402d693bbcd8
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52615976"
---
# <a name="configure-tls-12-in-aps"></a>Configurar o TLS 1.2 no APS

Para proteger pontos de acesso para usar somente o TLS 1.2, você terá que desabilitar explicitamente o outro protocolo em todos os hosts físicos e virtuais. Desabilitando protocolos exigem alterações de configuração do registro.

> [!WARNING]
> Esta seção, método ou tarefa contêm as etapas que indicam como modificar o Registro. No entanto, problemas graves podem ocorrer se você modificar o Registro incorretamente que pode causar perda de dados e exigir a reinstalação do sistema operacional. É altamente recomendável fazer backup do registro antes de modificá-lo. Em seguida, restaure o Registro se ocorrer algum problema. Para obter mais informações sobre como fazer backup e restaurar o registro, clique no número abaixo para ler o artigo da Base de dados de Conhecimento Microsoft:<br>
[322756](https://support.microsoft.com/help/322756) como fazer backup e restaurar o registro no Windows

**Desative:**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Também defina as seguintes chaves no seu cliente máquinas em que as ferramentas, como adaptadores de destino SSIS APS estão instaladas.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



