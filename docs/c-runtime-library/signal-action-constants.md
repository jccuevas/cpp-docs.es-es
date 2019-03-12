---
title: signal (Constantes de acción)
ms.date: 11/04/2016
f1_keywords:
- SIG_IGN
- SIG_DFL
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
ms.openlocfilehash: 4ff79626d576a05744336d36f99caf95d9b9902d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743873"
---
# <a name="signal-action-constants"></a>signal (Constantes de acción)

La acción realizada cuando se recibe la señal de interrupción depende del valor de `func`.

## <a name="syntax"></a>Sintaxis

```
#include <signal.h>
```

## <a name="remarks"></a>Comentarios

El argumento `func` debe ser una dirección de función o una de las constantes de manifiesto enumeradas a continuación y definidas en SIGNAL.H.

|||
|-|-|
| `SIG_DFL`  | Usa la respuesta predeterminada del sistema. Si el programa de llamada usa E/S de secuencia, no se vacían los búferes creados por la biblioteca en tiempo de ejecución.  |
| `SIG_IGN`  | Ignora la señal de interrupción. Este valor nunca debe proporcionarse para `SIGFPE`, ya que el estado de punto flotante del proceso se deja sin definir.  |
| `SIG_SGE`  | Indica un error ocurrido en la señal.  |
| `SIG_ACK`  | Indica que se ha recibido una confirmación.  |
| `SIG_ERR`  | Una señal ha producido un tipo de error devuelto que indica que se ha producido un error.  |

## <a name="see-also"></a>Vea también

[signal](../c-runtime-library/reference/signal.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
