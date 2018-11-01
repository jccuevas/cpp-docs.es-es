---
title: Error del compilador C3853
ms.date: 11/04/2016
f1_keywords:
- C3853
helpviewer_keywords:
- C3853
ms.assetid: 5b71805d-52b4-44ec-80ae-37c68d876f6a
ms.openlocfilehash: c2282196d045ffd88696149f7d22d4ed7f9603ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535179"
---
# <a name="compiler-error-c3853"></a>Error del compilador C3853

'=': volver a inicializar una referencia o asignación a través de una referencia a la función no es válido

No se puede asignar a una referencia a través de una función porque las funciones no son valores l.

Los ejemplos siguientes generan C3853:

```
// C3853.cpp
// compile with: /EHsc
#include <iostream>
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   rf = afunc;   // C3853, can't reassign to a ref that's an lvalue
   int i = 99;
   int & ri = i;
   std::cout << i << std::endl;
   ri = 0;   // OK, i = 88;
   std::cout << i << std::endl;
}
```