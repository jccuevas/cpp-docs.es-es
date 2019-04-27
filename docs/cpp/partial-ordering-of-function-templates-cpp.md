---
title: Ordenación parcial de plantillas de función (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 9a3dc687f197770f7a11440699163787b1dc48ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183382"
---
# <a name="partial-ordering-of-function-templates-c"></a>Ordenación parcial de plantillas de función (C++)

Puede haber varias plantillas de función que coincidan con la lista de argumentos de una llamada de función. C++ define el orden parcial de las plantillas de función para especificar a qué función se debe llamar. El orden es parcial porque puede haber algunas plantillas que se consideren especializadas por igual.

El compilador elige la función de plantilla más especializada que esté disponible entre las posibles coincidencias. Por ejemplo, si una plantilla de función toma un tipo __T__y otra plantilla de función teniendo __T\*__  está disponible, el __T\*__  se dice que la versión para ser más especializado y se prefiere el tipo genérico __T__ versión cada vez que el argumento es un tipo de puntero, aunque ambos serían coincidencias permitidas.

Utilice el proceso siguiente para determinar si un candidato de plantilla de función es más especializado:

1. Considere dos plantillas de función, T1 y T2.

1. Reemplace los parámetros de T1 con un tipo único hipotético X.

1. Con la lista de parámetros de T1, vea si T2 es una plantilla válida para esa lista de parámetros. Omita cualquier conversión implícita.

1. Repita el mismo proceso con T1 y T2 a la inversa.

1. Si una plantilla es una lista de argumentos de plantilla válida para otra plantilla pero no al revés, esa plantilla se considera menos especializada que la otra plantilla. Si las dos plantillas anterior paso formulario argumentos válidos para entre sí, a continuación, se consideran especializadas por igual, y da como resultado una llamada ambigua cuando se intenta utilizarlos.

1. Según estas reglas:

   1. Una especialización de plantilla para un tipo concreto se considera más especializada que una que toma un argumento de tipo genérico.

   1. Una plantilla que toma solo __T\*__  es más especializado que toma un solo __T__, porque el tipo de un hipotético __X\*__  es un argumento válido para un __T__ argumento de plantilla, pero __X__ no es un argumento válido para un __T\*__  argumento de plantilla.

   1. __const T__ es más especializado que __T__, porque __const X__ es un argumento válido para un __T__ argumento de plantilla, pero __X__ es no es un argumento válido para un __const T__ argumento de plantilla.

   1. __const T\*__  es más especializado que __T\*__, porque __const X\*__  es un argumento válido para un __T\*__  argumento de plantilla, pero __X\*__  no es un argumento válido para un __const T\*__  argumento de plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente funciona según lo especificado en el estándar:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

extern "C" int printf(const char*,...);
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
