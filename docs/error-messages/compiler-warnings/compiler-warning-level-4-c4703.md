---
title: Advertencia del compilador (nivel 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 5033490550f318cab65f984cab81b08102641c9d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518366"
---
# <a name="compiler-warning-level-4-c4703"></a>Advertencia del compilador (nivel 4) C4703

Se ha utilizado una variable de puntero local no inicializada ' nombre '

Es posible que se haya usado el *nombre* de la variable de puntero local sin tener asignado un valor. Esto puede producir resultados imprevisibles.

## <a name="example"></a>Ejemplo

El código siguiente genera C4701 y C4703.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

Para corregir esta advertencia, inicialice la variable tal como se muestra en este ejemplo:

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

int main()
{
    func(9);
}
```

## <a name="see-also"></a>Vea también

[Advertencia del compilador (nivel 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[ADVERTENCIAS,/SDL y mejorar la detección de variables sin inicializar](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
