---
title: C3615 de Error del compilador | Documentos de Microsoft
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3615
dev_langs:
- C++
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1ab43f8e15535614cedf43dba42fef882bf87a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3615"></a>C3615 de Error del compilador

> función constexpr '*función*' no se puede dar lugar a una expresión constante

La función *función* no se pudo evaluar como `constexpr` en tiempo de compilación. Para ser `constexpr`, una función solo puede llamar a otro `constexpr` funciones.

## <a name="example"></a>Ejemplo

Visual Studio de 2017 correctamente genera un error si el operando izquierdo de una operación de evaluación condicional no es válido en un `constexpr` contexto. El siguiente código se compila en Visual Studio 2015, pero no en Visual Studio de 2017.

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

Para corregir este problema, ya sea declare el `array::size()` funcionar como `constexpr` o quitar el `constexpr` calificador de `f`.