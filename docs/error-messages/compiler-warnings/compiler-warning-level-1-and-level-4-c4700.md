---
title: Compilador (niveles 1 y 4) C4700 | Documentos de Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4700
dev_langs:
- C++
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b871d6199338cc3040d6bddedb85f8732dfccd
ms.sourcegitcommit: 4e416049665819ac62f5300ddf86e94adede4ba0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Advertencia del compilador (niveles 1 y 4) C4700

> variable local no inicializada '*nombre*' utiliza

La variable local *nombre* ha sido *usa*, es decir, lectura desde, antes de que ha asignado ningún valor. En C y C++, no se inicializan las variables locales de forma predeterminada. Las variables sin inicializar pueden contener cualquier valor y su uso conduce a un comportamiento indefinido. Advertencia C4700 casi siempre indica un error que puede provocar resultados imprevisibles o bloqueos en el programa.

Para corregir este problema, puede inicializar las variables locales cuando se declaran o asignarles un valor antes de utilizarlos. Una función puede usarse para inicializar una variable que se pasa como un parámetro de referencia, o cuando su dirección se pasa como un parámetro de puntero.

## <a name="example"></a>Ejemplo

Este ejemplo genera C4700 cuando se utilizan variables t, u y v antes de que se inicializan y muestra el tipo de valor de elementos no utilizados que puede provocar. Las variables x y realice z no provocar la advertencia, porque se inicializan antes de su uso:

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

Cuando este código es ejecutar, t, u y v están sin inicializar, y el resultado de s es impredecible:

```Output
Value in s: 37816963
Value in w: 42
```
