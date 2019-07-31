---
title: Ordenación parcial de plantillas de función (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682424"
---
# <a name="partial-ordering-of-function-templates-c"></a>Ordenación parcial de plantillas de función (C++)

Puede haber varias plantillas de función que coincidan con la lista de argumentos de una llamada de función. C++ define el orden parcial de las plantillas de función para especificar a qué función se debe llamar. El orden es parcial porque puede haber algunas plantillas que se consideren especializadas por igual.

El compilador elige la función de plantilla más especializada que esté disponible entre las posibles coincidencias. Por ejemplo, si una plantilla de función toma un `T` tipo y otra plantilla de función `T*` que toma está disponible `T*` , se dice que la versión es más especializada. Es preferible usar la versión `T` genérica siempre que el argumento sea un tipo de puntero, aunque ambos serían coincidencias permitidas.

Utilice el proceso siguiente para determinar si un candidato de plantilla de función es más especializado:

1. Considere dos plantillas de función, T1 y T2.

1. Reemplace los parámetros de T1 con un tipo único hipotético X.

1. Con la lista de parámetros de T1, vea si T2 es una plantilla válida para esa lista de parámetros. Omita cualquier conversión implícita.

1. Repita el mismo proceso con T1 y T2 a la inversa.

1. Si una plantilla es una lista de argumentos de plantilla válida para la otra plantilla, pero el opuesto no es cierto, esa plantilla se considera menos especializada que la otra plantilla. Si usa el paso anterior, ambas plantillas forman argumentos válidos entre sí, se considera que son igualmente especializadas y una llamada ambigua se produce cuando intenta usarlas.

1. Según estas reglas:

   1. Una especialización de plantilla para un tipo concreto se considera más especializada que una que toma un argumento de tipo genérico.

   1. Una plantilla que solo `T*` se toma es más especializada que una `T`sola, porque un tipo `X*` hipotético es un argumento válido para `T` un argumento de plantilla `X` , pero no es un argumento válido para un `T*`argumento de plantilla.

   1. `const T`es más especializado que `T`, porque `const X` es un argumento válido para un `T` argumento de plantilla, `X` pero no es un argumento válido para `const T` un argumento de plantilla.

   1. `const T*`es más especializado que `T*`, porque `const X*` es un argumento válido para un `T*` argumento de plantilla, `X*` pero no es un argumento válido para `const T*` un argumento de plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente funciona como se especifica en el estándar:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Salida

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>Vea también

[Plantillas de función](../cpp/function-templates.md)
