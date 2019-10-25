---
title: Macros variádicas
ms.date: 10/17/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: de4d3a7f03f613cb058e564664f01837df23aefb
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587881"
---
# <a name="variadic-macros"></a>Macros variádicas

Las macros variádicas son macros estilo funciones que contienen un número variable de argumentos.

## <a name="remarks"></a>Comentarios

Para usar macros variádicas, los puntos suspensivos se pueden especificar como el argumento formal final en una definición de macro, y el identificador de reemplazo `__VA_ARGS__` se puede usar en la definición para insertar los argumentos adicionales.  `__VA_ARGS__` se reemplaza por todos los argumentos que coinciden con los puntos suspensivos, incluidas las comas entre ellos.

El estándar de C especifica que se debe pasar al menos un argumento a los puntos suspensivos para asegurarse de que la macro no se resuelva en una expresión con una coma final. La implementación tradicional C++ de Microsoft suprime una coma final si no se pasa ningún argumento a los puntos suspensivos. Cuando se establece la opción del compilador `/experimental:preprocessor`, no se suprime la coma final.

## <a name="example"></a>Ejemplo

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>Vea también

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)
