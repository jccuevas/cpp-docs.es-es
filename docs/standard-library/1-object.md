---
title: _1 (Objeto)
ms.date: 11/04/2016
f1_keywords:
- _1
- std::_1
- functional/std::_1
helpviewer_keywords:
- _1 object
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
ms.openlocfilehash: 248bb4733849b231ee4ff9180dd04e288412af3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666372"
---
# <a name="1-object"></a>_1 (Objeto)

Marcadores de posición para argumentos reemplazables.

## <a name="syntax"></a>Sintaxis

```cpp
namespace placeholders {
    extern unspecified _1,
    _2, ... _M
} // namespace placeholders (within std)
```

## <a name="remarks"></a>Comentarios

Los objetos `_1, _2, ... _M` son marcadores de posición que designa el primer, segundo, …, m-ésimo argumentos, respectivamente, en una llamada de función a un objeto devuelto por [enlazar](../standard-library/functional-functions.md#bind). `_N` se usa para especificar dónde se debe insertar el argumento Nth cuando se evalúa la expresión de enlace.

En esta implementación, el valor de `M` es 20.

## <a name="example"></a>Ejemplo

```cpp
// std__functional_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
    {
    std::cout << x << "^2 == " << x * x << std::endl;
    }

void product(double x, double y)
    {
    std::cout << x << "*" << y << " == " << x * y << std::endl;
    }

int main()
    {
    double arg[] = {1, 2, 3};

    std::for_each(&arg[0], &arg[3], square);
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], &arg[3], std::bind(square, _1));

    return (0);
    }

```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[bind](../standard-library/functional-functions.md#bind)<br/>
[is_placeholder (Clase)](../standard-library/is-placeholder-class.md)<br/>
