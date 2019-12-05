---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857936"
---
# <a name="__noop"></a>__noop

**Específicos de Microsoft**

El `__noop` intrínseco especifica que una función debe omitirse. La lista de argumentos se analiza, pero no se genera ningún código para los argumentos. Está diseñado para usarse en funciones de depuración globales que toman un número variable de argumentos.

El compilador convierte el `__noop` intrínseco en 0 en tiempo de compilación.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo puede usar `__noop`.

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

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Intrínsecos del Compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
