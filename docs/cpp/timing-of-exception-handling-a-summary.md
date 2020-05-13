---
title: 'Tiempo de manejo de excepciones: Un resumen'
ms.date: 05/07/2019
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 17d1c250a98afc2b86c198735602df7d80118bd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316597"
---
# <a name="timing-of-exception-handling-a-summary"></a>Tiempo de manejo de excepciones: Un resumen

Un controlador de terminación se ejecuta independientemente de cómo se termina el bloque de instrucciones **__try.** Las causas incluyen saltar fuera `longjmp` del **bloque __try,** una instrucción que transfiere el control fuera del bloque y desenredar la pila debido al control de excepciones.

> [!NOTE]
> El compilador de Microsoft C++ `setjmp` `longjmp` admite dos formas de las instrucciones y. La versión rápida omite el control de terminación pero es más eficaz. Para utilizar esta versión, incluya el archivo \<setjmp.h>. La otra versión admite el control de terminación como se describe en el párrafo anterior. Para utilizar esta versión, incluya el archivo \<setjmpex.h>. El aumento del rendimiento de la versión rápida depende de la configuración de hardware.

El sistema operativo ejecuta todos los controladores de terminación en el orden adecuado antes de que cualquier otro código pueda ejecutarlos, incluido el cuerpo de un controlador de excepciones.

Cuando la causa de la interrupción es una excepción, el sistema debe ejecutar primero la parte del filtro de uno o varios controladores de excepciones antes de decidir qué debe terminar. El orden de los eventos es:

1. Se produce una excepción.

1. El sistema busca en la jerarquía de controladores de excepciones activos y ejecuta el filtro del controlador de mayor prioridad, que es el controlador de excepciones instalado más recientemente y más profundamente anidado, en términos de bloques y llamadas de función.

1. Si este filtro pasa el control (devuelve 0), el proceso continúa hasta que se encuentra un filtro que no pase el control.

1. Si este filtro devuelve -1, la ejecución continúa donde se generó la excepción y no se produce ninguna terminación.

1. Si el filtro devuelve 1, se producen los eventos siguientes:

   - El sistema desenreda la pila, borrando todos los marcos de pila entre el código que se está ejecutando actualmente (donde se produjo la excepción) y el marco de pila que contiene el controlador de excepciones que obtiene el control.

   - Cuando se desenreda la pila, se ejecuta cada controlador de terminación de la pila.

   - Se ejecuta el propio controlador de excepciones.

   - El control se pasa a la línea de código después del final de este controlador de excepciones.

## <a name="see-also"></a>Consulte también

[Escribir un controlador de terminación](../cpp/writing-a-termination-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
