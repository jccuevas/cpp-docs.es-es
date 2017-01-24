---
title: "checked_array_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/checked_array_iterator"
  - "checked_array_iterator"
  - "std::checked_array_iterator"
  - "std.checked_array_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "checked_array_iterator"
  - "checked_array_iterator (clase)"
  - "checked_array_iterator, sintaxis"
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
caps.latest.revision: 28
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# checked_array_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase `checked_array_iterator` permite transformar una matriz o un puntero en un iterador comprobado.  Utilice esta clase como contenedor \(mediante la función [make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md)\) para matrices o punteros sin formato como una manera dirigida de comprobar y administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias.  Si es necesario, puede utilizar la versión no comprobada de esta clase, [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md).  
  
> [!NOTE]
>  Esta clase es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.  Para obtener un ejemplo en el que se muestra cómo escribir código que no requiere el uso de esta clase, vea el segundo ejemplo siguiente.  
  
## Sintaxis  
  
```  
template <class _Iterator>  
    class checked_array_iterator;  
```  
  
## Comentarios  
 Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).  
  
 Para obtener más información y código de ejemplo acerca de la característica iterador comprobado, consulte [Iteradores activados](../standard-library/checked-iterators.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo definir y utilizar un iterador de matrices comprobado.  
  
 Si el destino no es suficientemente grande para contener todos los elementos que se van a copiar, como ocurriría si cambió la línea:  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
```  
  
 hasta  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 4));  
```  
  
 Se producirá un error en tiempo de ejecución.  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[]={0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
  
   // constructor example  
   checked_array_iterator<int*> checked_out_iter(b, 5);  
   copy(a, a + 5, checked_out_iter);  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
}  
```  
  
  **\( 0 1 2 3 4 \)**  
**\( 0 1 2 3 4 \)**   
## Ejemplo  
 Para evitar la necesidad de la clase `checked_array_iterator` cuando se utilizan algoritmos de la Biblioteca estándar de C\+\+, considere la posibilidad de usar `vector` en lugar de una matriz asignada dinámicamente.  En el ejemplo siguiente se muestra cómo hacerlo:  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
    std::vector<int> v(10);  
    int *arr = new int[10];  
    for (int i = 0; i < 10; ++i)  
    {  
        v[i] = i;  
        arr[i] = i;  
    }  
  
    // std::copy(v.begin(), v.end(), arr); will result in  
    // warning C4996. To avoid this warning while using int *,  
    // use the Microsoft extension checked_array_iterator.  
    std::copy(v.begin(), v.end(),  
              stdext::checked_array_iterator<int *>(arr, 10));  
  
    // Instead of using stdext::checked_array_iterator and int *,  
    // consider using std::vector to encapsulate the array. This will  
    // result in no warnings, and the code will be portable.  
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];  
    std::copy(v.begin(), v.end(), arr2.begin());  
  
    for (int j = 0; j < arr2.size(); ++j)  
    {  
        cout << " " << arr2[j];  
    }  
    cout << endl;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
### Constructores  
  
|||  
|-|-|  
|[checked\_array\_iterator](../Topic/checked_array_iterator::checked_array_iterator.md)|Construye un `checked_array_iterator` predeterminado o un `checked_array_iterator` a partir de un iterador subyacente.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[difference\_type](../Topic/checked_array_iterator::difference_type.md)|Tipo que proporciona la diferencia entre dos `checked_array_iterator` que hacen referencia a elementos del mismo contenedor.|  
|[puntero](../Topic/checked_array_iterator::pointer.md)|Tipo que proporciona un puntero a un elemento direccionado por `checked_array_iterator`.|  
|[referencia](../Topic/checked_array_iterator::reference.md)|Tipo que proporciona una referencia a un elemento direccionado por `checked_array_iterator`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[base](../Topic/checked_array_iterator::base.md)|Recupera el iterador subyacente de su `checked_array_iterator`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/checked_array_iterator::operator==.md)|Comprueba dos `checked_array_iterator` para ver si son iguales.|  
|[operator\!\=](../Topic/checked_array_iterator::operator!=.md)|Comprueba dos `checked_array_iterator` para ver si son distintos.|  
|[operador \<](../Topic/checked_array_iterator::operator%3C.md)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor que el `checked_array_iterator` de la derecha.|  
|[operador \>](../Topic/checked_array_iterator::operator%3E.md)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor que el `checked_array_iterator` de la derecha.|  
|[operator\<\=](../Topic/checked_array_iterator::operator%3C=.md)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor o igual que el `checked_array_iterator` de la derecha.|  
|[operator\>\=](../Topic/checked_array_iterator::operator%3E=.md)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor o igual que el `checked_array_iterator` de la derecha.|  
|[operator\*](../Topic/checked_array_iterator::operator*.md)|Devuelve el elemento que direcciona un `checked_array_iterator`.|  
|[operator\-\>](../Topic/checked_array_iterator::operator-%3E.md)|Devuelve un puntero al elemento direccionado por `checked_array_iterator`.|  
|[operator\+\+](../Topic/checked_array_iterator::operator++.md)|Incrementa el `checked_array_iterator` al elemento siguiente.|  
|[operator\-\-](../Topic/checked_array_iterator::operator--.md)|Disminuye el `checked_array_iterator` al elemento anterior.|  
|[operator\+\=](../Topic/checked_array_iterator::operator+=.md)|Agrega un desplazamiento especificado a un `checked_array_iterator`.|  
|[operator\+](../Topic/checked_array_iterator::operator+.md)|Agrega un desplazamiento a un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator\-\=](../Topic/checked_array_iterator::operator-=.md)|Disminuye un desplazamiento especificado de un `checked_array_iterator`.|  
|[operator\-](../Topic/checked_array_iterator::operator-.md)|Disminuye un desplazamiento de un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator&#91;&#93;](../Topic/checked_array_iterator::operator.md)|Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `checked_array_iterator` un número especificado de posiciones.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)