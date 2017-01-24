---
title: "Instrucci&#243;n for basada en intervalo (C++) | Microsoft Docs"
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
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instrucci&#243;n for basada en intervalo (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ejecuta `statement` de forma repetida y secuencial para cada elemento de `expression`.  
  
## Sintaxis  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## Comentarios  
 Utilice la instrucción `for` basada en intervalo para construir los bucles que se deben ejecutar a lo largo de un "intervalo", que se define como cualquier elemento que se puede recorrer en iteración; por ejemplo, `std::vector`, o cualquier otra secuencia de STL cuyo intervalo esté definido por `begin()` y `end()`.  El nombre que se declara en la parte `for-range-declaration` es local de la instrucción `for` y no se puede volver a declarar en `expression` o `statement`.  Tenga en cuenta que es preferible utilizar la palabra clave [auto](../cpp/auto-cpp.md) en la parte `for-range-declaration` de la instrucción.  
  
 En este código se muestra cómo utilizar bucles `for` con intervalos para recorrer en iteración una matriz y un vector:  
  
```cpp  
  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 Este es el resultado:  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
  
 Un bucle `for` basado en intervalo finaliza cuando se ejecuta uno de estos elementos en `statement`: [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md) o [goto](../cpp/goto-statement-cpp.md) a una instrucción con etiqueta fuera del bucle **for** basado en intervalo.  Una instrucción [continue](../cpp/continue-statement-cpp.md) en un bucle `for` basado en intervalo solo finaliza la iteración actual.  
  
 Tenga en cuenta lo siguiente sobre la instrucción `for` basada en intervalo:  
  
-   Reconoce automáticamente las matrices.  
  
-   Reconoce los contenedores que tienen `.begin()` y `.end()`.  
  
-   Utiliza la búsqueda dependiente de argumentos `begin()` y `end()` para todo lo demás.  
  
## Vea también  
 [auto](../cpp/auto-cpp.md)   
 [Instrucciones de iteración](../cpp/iteration-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [while \(Instrucción\) \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [do\-while \(instrucción de C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for \(Instrucción\) \(C\+\+\)](../cpp/for-statement-cpp.md)