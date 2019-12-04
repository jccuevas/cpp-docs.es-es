---
title: Error irrecuperable C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756947"
---
# <a name="fatal-error-c1017"></a>Error irrecuperable C1017

expresión constante de tipo entero no válida

La expresión de una directiva de `#if` no existe o no se ha evaluado como una constante.

Las constantes definidas mediante `#define` deben tener valores que se evalúen como una constante entera si se usan en una directiva `#if`, `#elif`o `#else`.

En el ejemplo siguiente se genera C1017:

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Solución posible:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Dado que `CONSTANT_NAME` se evalúa como una cadena y no como un entero, la Directiva `#if` genera un error irrecuperable C1017.

En otros casos, el preprocesador evalúa una constante sin definir como cero. Esto puede producir resultados imprevistos, como se muestra en el ejemplo siguiente. `YES` no está definido, por lo que se evalúa como cero. La expresión `#if` `CONSTANT_NAME` se evalúa como false y el preprocesador quita el código que se va a utilizar en `YES`. `NO` también está sin definir (cero), por lo `#elif` `CONSTANT_NAME==NO` se evalúa como true (`0 == 0`), lo que hace que el preprocesador deje el código en la parte `#elif` de la instrucción, exactamente lo contrario del comportamiento previsto.

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Para ver exactamente cómo el compilador controla las directivas de preprocesador, use [/p](../../build/reference/p-preprocess-to-a-file.md), [/e](../../build/reference/e-preprocess-to-stdout.md)o [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).
