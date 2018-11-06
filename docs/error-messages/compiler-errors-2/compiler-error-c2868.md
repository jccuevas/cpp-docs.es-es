---
title: Error del compilador C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614778"
---
# <a name="compiler-error-c2868"></a>Error del compilador C2868

> '*identificador*': sintaxis no válida para la declaración using; esperado nombre completo

Un [mediante declaración](../../cpp/using-declaration.md) requiere un *nombre completo*, un operador de ámbito (`::`) separados por la secuencia de nombres de espacio de nombres, clase o enumeración que termina con el nombre del identificador. Un operador de resolución de ámbito solo puede utilizarse para introducir un nombre de espacio de nombres global.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2868 y también muestra el uso correcto:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```