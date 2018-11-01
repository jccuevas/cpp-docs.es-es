---
title: Error del compilador C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 998067e9af178c1898c3443c4e84da965c22fa81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576909"
---
# <a name="compiler-error-c2229"></a>Error del compilador C2229

el tipo 'identifier' tiene una matriz de tamaño cero no válida

Un miembro de un estructura o campo de bits contiene una matriz de tamaño cero que no es el último miembro.

Dado que puede tener una matriz de tamaño cero como el último miembro del struct, debe especificar su tamaño al asignar la estructura.

Si la matriz de tamaño cero no es el último miembro del struct, el compilador no puede calcular el desplazamiento para los campos restantes.

El ejemplo siguiente genera C2229:

```
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```