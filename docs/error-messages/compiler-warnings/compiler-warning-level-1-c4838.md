---
title: Compilador advertencia (nivel 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: dcb7062c751320a9f9c612b42caf6d018047d8d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380843"
---
# <a name="compiler-warning-level-1-c4838"></a>Compilador advertencia (nivel 1) C4838

conversión de 'type_1' a 'type_2' requiere una conversión de restricción

Se encontró una conversión de restricción implícita cuando se usa la inicialización de agregado o lista.

Conversiones de restricción implícitas en las asignaciones y la inicialización permite que el lenguaje C y C++ sigue palo, aunque inesperado de restricción es una causa de muchos errores de código. Para mejorar la seguridad de código, el estándar de C++ requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es [Error del compilador C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) cuando se usa la sintaxis de inicialización uniforme admitida a partir de Visual Studio 2015. El compilador genera la advertencia C4838 cuando se usa la lista o la sintaxis de inicialización de agregado compatibles con Visual Studio 2013.

Una conversión de restricción puede ser correcta cuando se sabe que el intervalo posible de los valores convertidos puede caber en el destino. En este caso, sabrá que más de lo que hace el compilador. Si realiza una conversión de restricción intencionadamente, hacer que sus intenciones explícito mediante el uso de una conversión estática. En caso contrario, este mensaje de advertencia casi siempre indica que hay un error en el código. Puede corregirlo asegurándose de que los objetos que se inicializa con tipos que son lo suficientemente grandes como para controlar las entradas.

El ejemplo siguiente genera C4838 y muestra una forma de corregirlo:

```
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