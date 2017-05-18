---
title: "Compatibilidad de los iteradores de depuración | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9e2bfb1095c28ea3592c5af2b89cb2fbeddcb60c
ms.openlocfilehash: 37f3450fbd320105781fa5398e838d3a8e317879
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="debug-iterator-support"></a>Debug Iterator Support
La biblioteca en tiempo de ejecución de Visual C++ detecta un uso incorrecto del iterador, valida y muestra un cuadro de diálogo en tiempo de ejecución. Para habilitar la compatibilidad con el iterador de depuración, debe usar versiones de depuración de la biblioteca estándar de C++ y la biblioteca en tiempo de ejecución de C para compilar el programa. Para obtener más información, vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md). Para obtener información sobre cómo usar iteradores comprobados, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
 El estándar de C++ describe cómo las funciones miembro pueden provocar que los iteradores de un contenedor se conviertan en no válidos. Dos ejemplos son:  
  
-   Borrar un elemento de un contenedor hace que los iteradores del elemento sean no válidos.  
  
-   Aumentar el tamaño de un [vector](../standard-library/vector.md) mediante inserción causa que los iteradores de `vector` no sean válidos.  
  
## <a name="example"></a>Ejemplo  
Si compila este programa de ejemplo en modo de depuración, en tiempo de ejecución se valida y finaliza.  
  
```cpp  
// iterator_debugging_0.cpp  
// compile by using /EHsc /MDd  
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
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
## <a name="example"></a>Ejemplo  
Puede usar la macro de preprocesador [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) para desactivar la característica de depuración de iteradores en una compilación de depuración. Este programa no valida, pero aún desencadena un comportamiento indefinido.  
  
```cpp  
// iterator_debugging_1.cpp  
// compile by using: /EHsc /MDd  
#define _ITERATOR_DEBUG_LEVEL 0  
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
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
```Output  
20  
-572662307  
```  
  
## <a name="example"></a>Ejemplo  
También se produce una aserción si intenta usar un iterador antes de que se inicialice, como se muestra aquí:  
  
```cpp  
// iterator_debugging_2.cpp  
// compile by using: /EHsc /MDd  
#include <string>  
using namespace std;  
  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## <a name="example"></a>Ejemplo  
En el ejemplo de código siguiente se produce una aserción porque los dos iteradores del algoritmo [for_each](../standard-library/algorithm-functions.md#for_each) son incompatibles. Comprobación de algoritmos para determinar si los iteradores que se les suministran hacen referencia al mismo contenedor.  
  
```cpp  
// iterator_debugging_3.cpp  
// compile by using /EHsc /MDd  
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
  
    // The next line asserts because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
Tenga en cuenta que este ejemplo usa la expresión lambda `[] (int& elem) { elem *= 2; }` en lugar de un functor. Aunque esta opción no influye en el error de aserción (un functor similar provocaría el mismo error), las expresiones lambda son una forma muy útil de realizar tareas de objeto de función compacta. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example"></a>Ejemplo  
Las comprobaciones de iteradores de depuración también provocan que una variable de iterador que se declara en un bucle `for` esté fuera de ámbito cuando el ámbito de bucle `for` finaliza.  
  
```cpp  
// iterator_debugging_4.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)  
      ;   // do nothing  
   --i;   // C2065  
}  
```  
  
## <a name="example"></a>Ejemplo  
Los iteradores de depuración tienen destructores no triviales. Si no se ejecuta un destructor, por el motivo que sea, se podrían producir infracciones de acceso y daños en los datos. Considere este ejemplo:  
  
```cpp  
// iterator_debugging_5.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
struct base {  
   // TO FIX: uncomment the next line  
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
  
## <a name="see-also"></a>Vea también  
[Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)





