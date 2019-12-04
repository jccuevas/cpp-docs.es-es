---
title: Error del compilador C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: 8d318742a367487f3688717046a6a798c2add87a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759846"
---
# <a name="compiler-error-c2764"></a>Error del compilador C2764

' param ': el parámetro de plantilla no se ha usado o no se ha deducido en la especialización parcial ' especialización '

Un parámetro de plantilla no se utiliza en una especialización parcial. Esto hace que la especialización parcial quede inutilizable porque no se puede deducir el parámetro de plantilla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2764:

```cpp
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
