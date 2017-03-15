---
title: "Ordenaci&#243;n parcial de plantillas de funci&#243;n (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordenación parcial de plantillas de función"
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ordenaci&#243;n parcial de plantillas de funci&#243;n (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede haber varias plantillas de función que coincidan con la lista de argumentos de una llamada de función.  C\+\+ define el orden parcial de las plantillas de función para especificar a qué función se debe llamar.  El orden es parcial porque puede haber algunas plantillas que se consideren especializadas por igual.  
  
 El compilador elige la función de plantilla más especializada que esté disponible entre las posibles coincidencias.  Por ejemplo, si una plantilla de función toma un tipo **T** y hay otra plantilla de función que toma **T\***, se considera que la versión de **T\*** es más especializada y se prefiere esta antes que la versión genérica **T** siempre que el argumento sea un tipo de puntero, aunque ambas coincidencias estarían permitidas.  
  
 Utilice el proceso siguiente para determinar si un candidato de plantilla de función es más especializado:  
  
1.  Considere dos plantillas de función, T1 y T2.  
  
2.  Reemplace los parámetros de T1 con un tipo único hipotético X.  
  
3.  Con la lista de parámetros de T1, vea si T2 es una plantilla válida para esa lista de parámetros.  Omita cualquier conversión implícita.  
  
4.  Repita el mismo proceso con T1 y T2 a la inversa.  
  
5.  Si una plantilla es una lista de argumentos de plantilla válida para otra plantilla pero no al revés, esa plantilla se considera menos especializada que la otra plantilla.  Si las dos plantillas del paso anterior forman argumentos válidos para ambas, se consideran especializadas por igual y, cuando se intente usarlas, se producirá una llamada ambigua.  
  
6.  Según estas reglas:  
  
    1.  Una especialización de plantilla para un tipo concreto se considera más especializada que una que toma un argumento de tipo genérico.  
  
    2.  Una plantilla que toma solo **T\*** es más especializada que una que toma solo **T**, porque un tipo hipotético **X\*** es un argumento válido para un argumento de plantilla **T**, pero **X** no es un argumento válido para un argumento de plantilla **T\***.  
  
    3.  **const T** es más especializado que **T**, porque **const X** es un argumento válido para un argumento de plantilla **T**, pero **X** no es un argumento válido para un argumento de plantilla **const T**.  
  
    4.  **const T\*** es más especializado que **T\***, porque **const X\*** es un argumento válido para un argumento de plantilla **T\***, pero **X\*** no es un argumento válido para un argumento de plantilla **const T\***.  
  
7.  El ejemplo siguiente funciona en Visual C\+\+ .NET 2003 según se especifica en el estándar:  
  
```  
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
  
### Output  
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## Vea también  
 [Plantillas de función](../cpp/function-templates.md)