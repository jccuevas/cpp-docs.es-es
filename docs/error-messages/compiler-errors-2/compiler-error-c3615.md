---
title: Error del compilador C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652223"
---
# <a name="compiler-error-c3615"></a>Error del compilador C3615

> la función constexpr '*función*' no se puede dar lugar a una expresión constante

La función *función* no se puede evaluar como `constexpr` en tiempo de compilación. Para ser `constexpr`, una función solo puede llamar a otro `constexpr` funciones.

## <a name="example"></a>Ejemplo

Visual Studio 2017 genera correctamente un error cuando el operando izquierdo de una operación de evaluación condicional no es válido en un `constexpr` contexto. El siguiente código se compila en Visual Studio 2015, pero no en Visual Studio 2017.

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

Para corregir este problema, declare el `array::size()` funcionar como `constexpr` o quitar el `constexpr` calificador `f`.