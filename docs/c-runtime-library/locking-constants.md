---
title: _locking (Constantes)
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: d559a68e8fede6e0b6dd40505a041b14da703681
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738491"
---
# <a name="locking-constants"></a>_locking (Constantes)

## <a name="syntax"></a>Sintaxis

```
#include <sys/locking.h>
```

## <a name="remarks"></a>Comentarios

El argumento *mode* en la llamada a la función `_locking` especifica la acción de bloqueo que se va a realizar.

El argumento *mode* debe ser una de las siguientes constantes de manifiesto.

|||
|-|-|
| `_LK_LOCK`  | Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la función lo vuelve a intentar después de 1 segundo. Si, después de 10 intentos, no se pueden bloquear los bytes, la función devuelve un error.  |
| `_LK_RLCK`  | Igual a `_LK_LOCK`.  |
|`_LK_NBLCK`  | Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la función devuelve un error.  |
| `_LK_NBRLCK`  | Igual a `_LK_NBLCK`.  |
| `_LK_UNLCK`  | Desbloquea los bytes especificados. (Los bytes deben haberse bloqueado previamente).  |

## <a name="see-also"></a>Vea también

[_locking](../c-runtime-library/reference/locking.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
