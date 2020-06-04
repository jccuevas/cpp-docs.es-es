---
title: Error del compilador C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 8c62117e9437233f614aa0e57a3848fcb8dd0c79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754854"
---
# <a name="compiler-error-c3854"></a>Error del compilador C3854

la expresión a la izquierda de ' = ' se evalúa como una función. No se puede asignar a una función (una función no es un valor l)

No se puede reinicializar una referencia. Al Desreferenciar una referencia a una función, se produce una función, que es un valor r, a la que no se puede asignar. Por lo tanto, no se puede asignar a través de una referencia a una función.

En el ejemplo siguiente se genera C3854:

```cpp
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```
