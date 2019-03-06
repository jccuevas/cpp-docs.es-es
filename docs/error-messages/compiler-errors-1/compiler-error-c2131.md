---
title: C2131 de Error del compilador
ms.date: 02/28/2019
f1_keywords:
- C2131
helpviewer_keywords:
- C2131
ms.openlocfilehash: 19bdf73efa82e624382446c94642ceddac00bf2e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426966"
---
# <a name="compiler-error-c2131"></a>C2131 de Error del compilador

> expresión no se evaluaran como una constante

Una expresión que se declara como **const** o **constexpr** no se evalúa como una constante en tiempo de compilación. El compilador debe ser capaz de determinar el valor de la expresión en el momento en que se utiliza.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una manera de hacer que el error C2131 y cómo corregirlo.

```cpp
// c2131.cpp
// compile by using: cl /EHsc /W4 /c c2131.cpp

struct test
{
    static const int array_size; // To fix, init array_size here.
    int size_array[array_size];  // C2131
};

const int test::array_size = 42;
```

```Output
c2131.cpp
c2131.cpp(7): error C2131: expression did not evaluate to a constant
c2131.cpp(7): note: failure was caused by non-constant arguments or reference to a non-constant symbol
c2131.cpp(7): note: see usage of 'array_size'
```

## <a name="see-also"></a>Vea también

[const](../../cpp/const-cpp.md)<br/>
[constexpr](../../cpp/constexpr-cpp.md)<br/>
