---
title: signal (Constantes)
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: e9953e967d1c94ae56dfc1063fb0deafa342631c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738732"
---
# <a name="signal-constants"></a>signal (Constantes)

## <a name="syntax"></a>Sintaxis

```
#include <signal.h>
```

## <a name="remarks"></a>Comentarios

El argumento `sig` debe ser una de las constantes de manifiesto enumeradas a continuación y definidas en SIGNAL.H.

|||
|-|-|
|SIGABRT|Terminación anómala. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  |
|SIGABRT_COMPAT|Igual que SIGABRT. Por compatibilidad con otras plataformas.  |
|SIGFPE|Error de punto flotante, como desbordamiento, división por cero u operación no válida. La acción predeterminada finaliza el programa de llamada.  |
|SIGILL|Instrucción no válida. La acción predeterminada finaliza el programa de llamada.  |
|SIGINT|Interrupción de CTRL+C. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  |
|SIGSEGV|Acceso no válido a almacenamiento. La acción predeterminada finaliza el programa de llamada.  |
|SIGTERM|Solicitud de finalización enviada al programa. La acción predeterminada finaliza el programa de llamada con el código de salida 3.  |
|SIG_ERR|Una señal ha producido un tipo de error devuelto que indica que se ha producido un error.  |

## <a name="see-also"></a>Vea también

[signal](../c-runtime-library/reference/signal.md)<br/>
[raise](../c-runtime-library/reference/raise.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
