---
title: Del compilador (nivel 4) de la advertencia C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360013"
---
# <a name="compiler-warning-level-4-c4840"></a>Del compilador (nivel 4) de la advertencia C4840

> uso no portable de la clase*tipo*' como argumento a una función variádica

## <a name="remarks"></a>Comentarios

Clases o structs que se pasan a una función variádica debe poder copiar trivialmente. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

Esta advertencia está disponible a partir de Visual Studio 2017.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4840 y muestra cómo corregirlo:

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

Para las cadenas compiladas y administradas mediante `CStringW`, proporcionado `operator LPCWSTR()` debe usarse para convertir un `CStringW` objeto para el puntero de cadena de estilo C esperado por la cadena de formato:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```