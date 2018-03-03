---
title: "Range-based for (instrucción) (C++) | Documentos de Microsoft"
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
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43ded324227878b44f997e6539e060145ad0fb66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="range-based-for-statement-c"></a>Instrucción for basada en intervalo (C++)
Ejecuta `statement` de forma repetida y secuencial para cada elemento de `expression`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>Comentarios  
 Usar basado en el intervalo `for` instrucción para construir los bucles que se deben ejecutar a través de un "intervalo", que se define como cualquier elemento que puede recorrer en iteración, por ejemplo, `std::vector`, o cualquier otra secuencia de la biblioteca estándar de C++ cuyo intervalo esté definido por un `begin()` y `end()`. El nombre que se declara en la parte `for-range-declaration` es local de la instrucción `for` y no se puede volver a declarar en `expression` o `statement`. Tenga en cuenta que la [automática](../cpp/auto-cpp.md) se prefiere la palabra clave en el `for-range-declaration` parte de la instrucción. 

 **Novedades en Visual Studio de 2017:** basada en intervalo para bucles ya no necesitan que las funciones begin() y end() devuelven objetos del mismo tipo. Esto permite que end() devuelva un objeto centinela como el usado por los intervalos tal como se define en la propuesta de intervalos V3. Para más información, vea [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (Generalización del bucle for basado en intervalos) y [range-v3 library](https://github.com/ericniebler/range-v3) (Biblioteca range-v3) en GitHub.
  
 Este código muestra cómo utilizar basada en intervalo `for` bucles y recorrer en iteración una matriz y un vector:  
  
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
  
    for( const auto &y : x ) { // Type inference by const reference.  
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
  
 Basado en un intervalo `for` bucle finaliza cuando uno de ellos en `statement` se ejecuta: una [salto](../cpp/break-statement-cpp.md), [devolver](../cpp/return-statement-cpp.md), o [goto](../cpp/goto-statement-cpp.md) a una instrucción con etiqueta fuera de la basado en intervalo **para** bucle. A [continuar](../cpp/continue-statement-cpp.md) instrucción está basado en un intervalo en `for` bucle finaliza solo la iteración actual.  
  
 Tenga en cuenta lo siguiente sobre la instrucción `for` basada en intervalo:  
  
-   Reconoce automáticamente las matrices.  
  
-   Reconoce los contenedores que tienen `.begin()` y `.end()`.  
  
-   Utiliza la búsqueda dependiente de argumentos `begin()` y `end()` para todo lo demás.  
  
## <a name="see-also"></a>Vea también  
 [Automático](../cpp/auto-cpp.md)   
 [Iteration Statements](../cpp/iteration-statements-cpp.md)  (Instrucciones de iteración)  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [while (Instrucción) (C++)](../cpp/while-statement-cpp.md)   
 [Instrucción do-while (C++)](../cpp/do-while-statement-cpp.md)   
 [for (Instrucción) (C++)](../cpp/for-statement-cpp.md)