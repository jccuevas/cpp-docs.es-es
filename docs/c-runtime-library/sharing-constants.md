---
title: Constantes de uso compartido | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs:
- C++
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05226ffcc5a10785391969f8162a76034efc4d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097313"
---
# <a name="sharing-constants"></a>Constantes de uso compartido

Constantes para modos de uso compartido de archivos.

## <a name="syntax"></a>Sintaxis

```

#include <share.h>

```

## <a name="remarks"></a>Comentarios

El argumento *shflag* determina el modo de uso compartido, que consta de una o más constantes de manifiesto. Estas se pueden combinar con los argumentos *oflag* (vea [Constantes de archivo](../c-runtime-library/file-constants.md)).

En la tabla siguiente se enumeran las constantes y sus significados:

|Constante|Significado|
|--------------|-------------|
|`_SH_DENYRW`|Deniega el acceso de lectura y escritura al archivo.|
|`_SH_DENYWR`|Deniega el acceso de escritura al archivo.|
|`_SH_DENYRD`|Deniega el acceso de lectura al archivo.|
|`_SH_DENYNO`|Permite el acceso de lectura y escritura.|
|`_SH_SECURE`|Establece el modo seguro (lectura compartida o acceso de escritura exclusivo).|

## <a name="see-also"></a>Vea también

[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)