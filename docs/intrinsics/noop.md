---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 24ba85b1fbbba4491c03d5a81afae345228db3bd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217183"
---
# <a name="__noop"></a>__noop

**Específicos de Microsoft**

El `__noop` intrínseco especifica que una función debe omitirse. La lista de argumentos se analiza, pero no se genera ningún código para los argumentos. Está diseñado para usarse en funciones de depuración globales que toman un número variable de argumentos.

El compilador convierte `__noop` el intrínseco en 0 en tiempo de compilación.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo puede `__noop`usar.

```cpp
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

[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
