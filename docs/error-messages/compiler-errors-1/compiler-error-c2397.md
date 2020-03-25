---
title: Error del compilador C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206020"
---
# <a name="compiler-error-c2397"></a>Error del compilador C2397

la conversión de ' type_1 ' a ' type_2 ' requiere una conversión de restricción

Se encontró una conversión de restricción implícita al utilizar la inicialización uniforme.

El lenguaje C permite conversiones de restricción implícitas en las asignaciones y la inicialización, y C++ sigue el palo, aunque la restricción inesperada es una causa de muchos errores de código. Para que el código sea más C++ seguro, el estándar requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es el error del compilador C2397 cuando se usa la sintaxis de inicialización uniforme que se admite a partir de Visual Studio 2015. El compilador genera la [Advertencia del compilador (nivel 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) cuando se usa la sintaxis de inicialización de lista o agregado compatible con Visual Studio 2013.

Una conversión de restricción puede ser correcta si sabe que el posible intervalo de valores convertidos puede caber en el destino. En este caso, sabe que es más que el compilador. Si realiza una conversión de restricción intencionadamente, haga que sus intenciones sean explícitas mediante una conversión estática. De lo contrario, este mensaje de error casi siempre indica que hay un error en el código. Puede corregirlo asegurándose de que los objetos que inicializa tienen tipos que son lo suficientemente grandes como para controlar las entradas.

En el ejemplo siguiente se genera C2397 y se muestra una manera de corregirlo:

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
