---
title: ADVERTENCIA del compilador (nivel 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185209"
---
# <a name="compiler-warning-level-4-c4840"></a>ADVERTENCIA del compilador (nivel 4) C4840

> uso no portátil de la clase '*Type*' como argumento de una función variádicas

## <a name="remarks"></a>Observaciones

Las clases o Structs que se pasan a una función variádicas se deben poder copiar de forma trivial. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

Esta advertencia está disponible a partir de Visual Studio 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4840 y se muestra cómo corregirlo:

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

En el caso de las cadenas compiladas y administradas mediante `CStringW`, se debe usar el `operator LPCWSTR()` proporcionado para convertir un objeto `CStringW` en el puntero de cadena de estilo C esperado por la cadena de formato:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
