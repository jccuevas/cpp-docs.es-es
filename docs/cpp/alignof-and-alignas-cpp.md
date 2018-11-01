---
title: alignof y alignas (C++)
ms.date: 11/04/2016
ms.assetid: 1d18aa8a-9621-4fb5-86e5-4cc86d5187f4
ms.openlocfilehash: e5d023d7969764bdd36030a508abdd94068e48b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493657"
---
# <a name="alignof-and-alignas-c"></a>alignof y alignas (C++)

El **alignas** especificador de tipo es una manera estándar de C++ portátil, para especificar una alineación personalizada de variables y tipos definidos por el usuario. El **alignof** operador igualmente es una forma estándar y portátil de obtener la alineación de una variable o un tipo especificado.

## <a name="example"></a>Ejemplo

Puede usar **alignas** en una clase, struct o union, o en los miembros individuales. Cuando varios **alignas** especificadores se encuentran, el compilador elige el más estricto, (uno con el valor más grande).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Vea también

[Alineación](../cpp/alignment-cpp-declarations.md)