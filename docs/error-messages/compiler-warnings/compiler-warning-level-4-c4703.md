---
title: Advertencia del compilador (nivel 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 5f98a438769073dc5abb10f3de7fb0af2e8e88d4
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278442"
---
# <a name="compiler-warning-level-4-c4703"></a>Advertencia del compilador (nivel 4) C4703

Potencialmente no inicializada de la variable de puntero local 'nombre' utilizada

La variable de puntero local *nombre* es posible que se han usado sin que se asigna un valor. Esto podría producir resultados imprevisibles.

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

void main()
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

void main()
{
    func(9);
}
```

## <a name="see-also"></a>Vea también

[Advertencia del compilador (nivel 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[Advertencias, /sdl y mejora de la detección de variables sin inicializar](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)