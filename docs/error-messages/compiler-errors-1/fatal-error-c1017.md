---
title: Error irrecuperable C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: e2309b93be65b049c35abf96572e144a0a518007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614284"
---
# <a name="fatal-error-c1017"></a>Error irrecuperable C1017

expresión constante de tipo entero no válida

La expresión en una `#if` directiva no existe o no se evaluaran como una constante.

Constantes definidas mediante `#define` deben tener valores que se evalúan como una constante entera si se usan en un `#if`, `#elif`, o `#else` directiva.

El ejemplo siguiente genera C1017:

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Posible resolución:

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Dado que `CONSTANT_NAME` se evalúa como una cadena y no es un entero, el `#if` directiva generará el error irrecuperable C1017.

En otros casos, el preprocesador se evalúa como una constante sin definir como cero. Esto puede provocar resultados no deseados, como se muestra en el ejemplo siguiente. `YES` no está definido, por lo que se evalúa como cero. La expresión `#if` `CONSTANT_NAME` se evalúa como false y el código que se usará en `YES` se quita el preprocesador. `NO` es también definido (cero), por lo que `#elif` `CONSTANT_NAME==NO` se evalúa como true (`0 == 0`), lo que el preprocesador dejará el código en el `#elif` parte de la instrucción, justo lo contrario al comportamiento esperado.

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Para ver exactamente cómo controla el compilador las directivas de preprocesador, use [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), o [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).