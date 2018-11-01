---
title: Error del compilador C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: ba16431fc71a0e594b77dcc6dab62ed6c49c9137
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587112"
---
# <a name="compiler-error-c2764"></a>Error del compilador C2764

'param': parámetro de plantilla no utilizado o deducible en la especialización parcial 'specialization'

No se utiliza un parámetro de plantilla en una especialización parcial. Esto hace que la especialización parcial que quede inutilizable porque no se puede deducir el parámetro de plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2764:

```
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```