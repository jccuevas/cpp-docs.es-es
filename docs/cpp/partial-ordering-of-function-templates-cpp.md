---
title: "Ordenación parcial de plantillas de función (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cddc0f1680a3354276a2135dd28c31a2037a8202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="partial-ordering-of-function-templates-c"></a>Ordenación parcial de plantillas de función (C++)

Puede haber varias plantillas de función que coincidan con la lista de argumentos de una llamada de función. C++ define el orden parcial de las plantillas de función para especificar a qué función se debe llamar. El orden es parcial porque puede haber algunas plantillas que se consideren especializadas por igual.

El compilador elige la función de plantilla más especializada que esté disponible entre las posibles coincidencias. Por ejemplo, si una plantilla de función toma un tipo __T__y otra plantilla de función toma __T\*__  está disponible, el __T\*__  se dice que versión más especializada y es preferible genérico __T__ versión siempre que el argumento es un tipo de puntero, aunque ambos sería coincidencias permitidos.

Utilice el proceso siguiente para determinar si un candidato de plantilla de función es más especializado:

1. Considere dos plantillas de función, T1 y T2.

2. Reemplace los parámetros de T1 con un tipo único hipotético X.

3. Con la lista de parámetros de T1, vea si T2 es una plantilla válida para esa lista de parámetros. Omita cualquier conversión implícita.

4. Repita el mismo proceso con T1 y T2 a la inversa.

5. Si una plantilla es una lista de argumentos de plantilla válida para otra plantilla pero no al revés, esa plantilla se considera menos especializada que la otra plantilla. Si las dos plantillas anterior paso formulario argumentos válidos para entre sí, se consideran especializadas por igual y da como resultado una llamada ambigua cuando se intenta utilizarlos.

6. Según estas reglas:

     1. Una especialización de plantilla para un tipo concreto se considera más especializada que una que toma un argumento de tipo genérico.

     2. Una plantilla que toma solo __T\*__  es más especializado que toma un solo __T__, porque el tipo de un hipotético __X\*__  es un argumento válido para un __T__ argumento de plantilla, pero __X__ no es un argumento válido para un __T\*__  argumento de plantilla.

     3. __const T__ es más especializado que __T__, porque __const X__ es un argumento válido para un __T__ argumento de plantilla, pero __X__ no es un argumento válido para un __const T__ argumento de plantilla.

     4. __const T\*__  es más especializado que __T\*__, porque __const X\*__  es un argumento válido para un __T\*__  argumento de plantilla, pero __X\*__  no es un argumento válido para un __const T\*__  argumento de plantilla.

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
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## <a name="see-also"></a>Vea también

[Plantillas de función](../cpp/function-templates.md)
