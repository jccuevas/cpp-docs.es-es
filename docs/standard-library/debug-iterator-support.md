---
title: "Compatibilidad de los iteradores de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad de los iteradores de depuración"
  - "iteradores incompatibles"
  - "iteradores, compatibilidad de los iteradores de depuración"
  - "iteradores, incompatibles"
  - "bibliotecas seguras"
  - "bibliotecas seguras, Biblioteca estándar de C++"
  - "biblioteca estándar de C++ segura"
  - "Biblioteca estándar de C++, compatibilidad de los iteradores de depuración"
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# Compatibilidad de los iteradores de depuraci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de Visual C\+\+ detecta uso incorrecto de iterador, y aserciones y muestra un cuadro de diálogo en tiempo de ejecución.  Para habilitar la compatibilidad de iterador de depuración, debe utilizar una versión de depuración de la biblioteca en tiempo de ejecución de C. para compilar el programa.  Para obtener más información, vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  Para obtener información sobre cómo usar iteradores, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
 El estándar de C\+\+ describe cómo las funciones miembro pueden hacer iteradores un contenedor para volverse no válidas.  Dos ejemplos son:  
  
-   Borrar un elemento de un contenedor hace iteradores al elemento dejen de ser válido.  
  
-   Aumentar el tamaño de [vector](../standard-library/vector.md) \(inserción o inserción\) hace iteradores en `vector` dejen de ser válido.  
  
## Ejemplo  
 Si compila el programa siguiente en modo de depuración, en tiempo de ejecución validar y finalizará.  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
  
```  
  
## Ejemplo  
 Puede utilizar el símbolo [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) para desactivar la característica de depuración de iterador en una compilación de depuración.  El siguiente programa no validar, pero todavía desencadena un comportamiento indefinido.  
  
> [!IMPORTANT]
>  Uso `_ITERATOR_DEBUG_LEVEL` de controlar `_HAS_ITERATOR_DEBUGGING`.  Para obtener más información, vea [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md).  
  
```cpp  
// iterator_debugging.cpp  
// compile with: /EHsc /MDd  
#define _HAS_ITERATOR_DEBUGGING 0  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout<<*j<<'\n';  
  
   v.insert(i,25);   
  
   std::cout<<*j<<'\n'; // Using an old iterator after an insert  
}  
```  
  
  **20**  
**\-572662307**   
## Ejemplo  
 Validar también aparece si intenta utilizar un iterador antes de inicializarse, como se muestra aquí:  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <string>  
using namespace std;  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## Ejemplo  
 El ejemplo de código siguiente se genera una aserción porque los dos iteradores del algoritmo de [for\_each](../Topic/for_each.md) son incompatibles.  Comprobación de los algoritmos para determinar si los iteradores que se proporcionan a ellos hacen referencia al mismo contenedor.  
  
```cpp  
/* compile with /EHsc /MDd */  
#include <algorithm>  
#include <vector>  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int> v2;  
  
    v1.push_back(10);  
    v1.push_back(20);  
  
    v2.push_back(10);  
    v2.push_back(20);  
  
    // The next line will assert because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
 Observe que este ejemplo utiliza la expresión lambda `[] (int& elem) { elem *= 2; }` en lugar de un functor.  Aunque esta opción tiene ningún efecto en el error \- uno validar que el functor similar produciría el mismo error \- lambdas es una manera muy útil de lograr compacto las tareas del objeto.  Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## Ejemplo  
 Depurar el iterador que comprueba también genera una variable de iterador que se declara en un bucle de `for` que está fuera de ámbito cuando el ámbito del bucle de `for` finaliza.  
  
```cpp  
// debug_iterator.cpp  
// compile with: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin() ; i != v.end(); ++i)  
   ;  
   --i;   // C2065  
}  
```  
  
## Ejemplo  
 Los iteradores de depuración tienen destructores no triviales.  Si el destructor no se ejecuta, por cualquier razón, las infracciones de acceso y daños en los datos se pueden producir.  Considere este ejemplo:  
  
```cpp  
/* compile with: /EHsc /MDd */  
#include <vector>  
struct base {  
   // FIX: uncomment the next line  
   // virtual ~base() {}  
};  
  
struct derived : base {  
   std::vector<int>::iterator m_iter;  
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}  
   ~derived() {}  
};  
  
int main() {  
   std::vector<int> vect( 10 );  
   base * pb = new derived( vect.begin() );  
   delete pb;  // doesn't call ~derived()  
   // access violation  
}  
```  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)