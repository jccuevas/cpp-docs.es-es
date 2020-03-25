---
title: Error del compilador C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200543"
---
# <a name="compiler-error-c3615"></a>Error del compilador C3615

> la función constexpr '*function*' no puede dar como resultado una expresión constante

No se pudo evaluar la *función* de función como `constexpr` en tiempo de compilación. Para ser `constexpr`, una función solo puede llamar a otras funciones de `constexpr`.

## <a name="example"></a>Ejemplo

Visual Studio 2017 genera correctamente un error cuando el operando izquierdo de una operación de evaluación condicional no es válido en un contexto de `constexpr`. El código siguiente se compila en Visual Studio 2015, pero no en Visual Studio 2017.

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

Para corregir este problema, declare la función `array::size()` como `constexpr` o quite el calificador `constexpr` de `f`.
