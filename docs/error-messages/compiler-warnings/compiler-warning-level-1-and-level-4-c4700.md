---
title: Advertencia del compilador (niveles 1 y 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463224"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Advertencia del compilador (niveles 1 y 4) C4700

> variable local sin inicializar '*nombre*' utiliza

La variable local *nombre* ha sido *usa*, es decir, se leen, antes de que tenga asignado un valor. En C y C++, las variables locales no se inicializan de forma predeterminada. Variables sin inicializar pueden contener cualquier valor, y su uso da lugar a un comportamiento indefinido. Advertencia C4700 casi siempre indica un error que puede provocar resultados imprevisibles o bloqueos en el programa.

Para corregir este problema, puede inicializar las variables locales cuando se declaran o asignarles un valor antes de usarse. Una función puede utilizarse para inicializar una variable que se pasa como un parámetro de referencia, o cuando su dirección se pasa como un parámetro de puntero.

## <a name="example"></a>Ejemplo

Este ejemplo genera C4700 cuando se usan variables t, u y v antes de que se inicializan y se muestra el tipo de valor de elementos no utilizados que puede producir. Las variables x y realice z no provocar la advertencia, porque se inicializan antes de su uso:

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

Cuando este código es la ejecución, t, u y v están sin inicializar y la salida de s es imprevisible:

```Output
Value in s: 37816963
Value in w: 42
```
