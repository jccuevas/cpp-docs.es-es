---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 074ab4c6ea51c8b3a2543d9b43248a8da37567cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613021"
---
# <a name="noop"></a>__noop

**Específicos de Microsoft**

El `__noop` intrínseco especifica que se debe ignorar una función y se puede analizar la lista de argumentos, pero no se generará ningún código para los argumentos. Se está diseñado para su uso en funciones de depuración global que toman un número variable de argumentos.

El compilador convierte el `__noop` intrínseco en 0 en tiempo de compilación.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo se podría utilizar `__noop`.

```
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>Vea también

[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)