---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360810"
---
# <a name="__restrict"></a>__restrict

Al igual que el **modificador __declspec ( [restrict](../cpp/restrict.md) ),** la palabra clave **__restrict** indica que un símbolo no tiene alias en el ámbito actual. La **__restrict** palabra clave __restrict `__declspec ( restrict )` difiere del modificador de las siguientes maneras:

- La palabra clave **__restrict** solo es `__declspec ( restrict )` válida en variables y solo es válida en declaraciones y definiciones de función.

- **__restrict** es similar a **restringir** de la especificación C99, pero **__restrict** se puede utilizar en programas C++ o C.

- Cuando se utiliza **__restrict,** el compilador no propagará la propiedad no-alias de una variable. Es decir, si asigna una variable **de __restrict** a una variable que no**sea __restrict,** el compilador seguirá permitir que se dote de alias a la variable que no sea __restrict. Esto es diferente del comportamiento de la palabra clave **restrict** de la especificación C99.

Normalmente, si se modifica el comportamiento de una función completa, es mejor usar `__declspec ( restrict )` que la palabra clave.

Por compatibilidad con versiones anteriores, **_restrict** es un sinónimo de **__restrict** a menos que se especifique la opción del compilador [/Za \(Disable language extensions).](../build/reference/za-ze-disable-language-extensions.md)

En Visual Studio 2015 y versiones posteriores, se pueden usar **__restrict** en referencias de C++.

> [!NOTE]
> Cuando se utiliza en una variable que también tiene la palabra clave [volatile,](../cpp/volatile-cpp.md) **volatile** tendrá prioridad.

## <a name="example"></a>Ejemplo

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
