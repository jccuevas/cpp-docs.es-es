---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 674b5170dd2bba7038dfe11af906e31540acd993
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262988"
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