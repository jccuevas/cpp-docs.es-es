---
title: ADVERTENCIA del compilador (nivel 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: c3ddc861e5da271903372eac1ef1e8f6916e06df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199373"
---
# <a name="compiler-warning-level-1-c4838"></a>ADVERTENCIA del compilador (nivel 1) C4838

la conversión de ' type_1 ' a ' type_2 ' requiere una conversión de restricción

Se encontró una conversión de restricción implícita al utilizar la inicialización de agregado o de lista.

El lenguaje C permite conversiones de restricción implícitas en las asignaciones y la inicialización, y C++ sigue el palo, aunque la restricción inesperada es una causa de muchos errores de código. Para que el código sea más C++ seguro, el estándar requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es el [error del compilador C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) cuando se usa la sintaxis de inicialización uniforme que se admite a partir de Visual Studio 2015. El compilador genera la advertencia C4838 cuando se usa la sintaxis de inicialización de lista o agregado compatible con Visual Studio 2013.

Una conversión de restricción puede ser correcta si sabe que el posible intervalo de valores convertidos puede caber en el destino. En este caso, sabe que es más que el compilador. Si realiza una conversión de restricción intencionadamente, haga que sus intenciones sean explícitas mediante una conversión estática. De lo contrario, este mensaje de advertencia casi siempre indica que hay un error en el código. Puede corregirlo asegurándose de que los objetos que inicializa tienen tipos que son lo suficientemente grandes como para controlar las entradas.

En el ejemplo siguiente se genera C4838 y se muestra una manera de corregirlo:

```cpp
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```
