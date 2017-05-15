---
title: priority_queue (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- priority_queue
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
dev_langs:
- C++
helpviewer_keywords:
- priority_queue class
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
caps.latest.revision: 25
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 31191f5109242dc239ac0237a2eab6ff459fe41b
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="priorityqueue-class"></a>priority_queue (Clase)
Una clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad que limita el acceso al elemento superior de algún tipo de contenedor subyacente, que siempre es el más grande o el que tiene una prioridad más alta. Pueden agregarse nuevos elementos a priority_queue y el elemento superior de priority_queue puede inspeccionarse o quitarse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>  
class priority_queue  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ype*  
 El tipo de datos de los elementos que se va a almacenar en priority_queue.  
  
 `Container`  
 El tipo del contenedor subyacente que se usa para implementar priority_queue.  
  
 *Compare*  
 El tipo que proporciona un objeto de función que puede comparar dos valores de elementos como claves de ordenación para determinar su orden relativo en priority_queue. Este argumento es opcional y el predicado binario **less***\<***typename** *Container***::value_type***>* es el valor predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos de la clase **Type** estipulada en el primer parámetro de plantilla de un objeto de cola son sinónimos de [value_type](#value_type) y deben coincidir con el tipo de elemento de la clase de contenedor subyacente **Container** estipulada por el segundo parámetro de plantilla. El **tipo** debe ser asignable, para que sea posible copiar objetos de ese tipo y asignar valores a variables de ese tipo.  
  
 El objeto priority_queue ordena la secuencia que controla llamando a un objeto de función almacenado de clase **Traits**. En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  
  
 Las clases contenedoras subyacentes adecuadas para priority_queue incluyen [deque (Clase)](../standard-library/deque-class.md) y la clase [vector (Clase)](../standard-library/vector-class.md) predeterminada, o cualquier otro contenedor de secuencias que admita las operaciones `front`, `push_back` y `pop_back`, y un iterador de acceso aleatorio. La clase de contenedor subyacente se encapsula dentro del adaptador de contenedor, que solo expone el conjunto limitado de las funciones miembro de contenedor de secuencias como una interfaz pública.  
  
 Agregar elementos y quitarlos de `priority_queue` tiene una complejidad logarítmica. Tener acceso a elementos en `priority_queue` tiene una complejidad constante.  
  
 Existen tres tipos de adaptadores de contenedor que se definen mediante la biblioteca estándar de C++: stack, queue y priority_queue. Cada uno restringe la función de alguna clase de contenedor subyacente para proporcionar una interfaz controlada de manera precisa para una estructura de datos estándar.  
  
-   La [clase stack](../standard-library/stack-class.md) es compatible con una estructura de datos LIFO (el último en entrar es el primero en salir). Un buen símil sería una pila de platos. Solo se pueden insertar e inspeccionar elementos (platos) en la parte superior de la pila, que es el último elemento al final del contenedor base, y solo se pueden quitar de ahí. La restricción de acceder únicamente al elemento superior es el motivo por el que se usa la clase stack.  
  
-   La [clase queue](../standard-library/queue-class.md) es compatible con una estructura de datos FIFO (el primero en entrar es el primero en salir). Un buen símil sería el de personas que hacen cola en un banco. Se pueden agregar elementos (personas) a la parte posterior de la línea y quitarlos de la parte delantera de la línea. Se puede inspeccionar tanto la parte delantera como trasera de una línea. La restricción de acceder únicamente a los elementos delanteros y traseros de esta manera es el motivo por el que se usa la clase queue.  
  
-   La clase priority_queue ordena sus elementos de tal modo que el elemento más grande siempre esté en la parte superior. Admite la inserción de un elemento y la inspección y eliminación del elemento superior. Un buen símil sería el de personas alineadas y organizadas por edad, altura o cualquier otro criterio.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[priority_queue](#priority_queue)|Construye un `priority_queue` que está vacío o que es una copia de un intervalo de un objeto contenedor base o de otro `priority_queue`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[container_type](#container_type)|Tipo que proporciona el contenedor base que debe adaptarse mediante una `priority_queue`.|  
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `priority_queue`.|  
|[value_type](#value_type)|Tipo que representa el tipo de objeto almacenado como elemento en una `priority_queue`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[empty](#empty)|Comprueba si la `priority_queue` está vacía.|  
|[pop](#pop)|Quita el elemento más grande del `priority_queue` desde la posición superior.|  
|[push](#push)|Agrega un elemento a la cola de prioridad basándose en la prioridad del elemento desde operator<.|  
|[size](#size)|Devuelve el número de elementos de `priority_queue`.|  
|[top](#top)|Devuelve una referencia constante al elemento más grande en la parte superior del `priority_queue`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<queue>  
  
 **Espacio de nombres:** std  
  
##  <a name="container_type"></a> priority_queue::container_type  
 Un tipo que proporciona el contenedor base que debe adaptarse.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Container`. La clase de contenedor de secuencias de la biblioteca estándar de C++ `deque` y la clase predeterminada `vector`, cumplen los requisitos para usarse como el contenedor base para un objeto priority_queue. También pueden usarse tipos definidos por el usuario que cumplan los requisitos.  
  
 Para obtener más información sobre `Container`, vea la sección Comentarios del tema [Clase priority_queue](../standard-library/priority-queue-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [priority_queue](#priority_queue) para obtener un ejemplo de cómo declarar y usar `container_type`.  
  
##  <a name="empty"></a> priority_queue::empty  
 Prueba si un objeto priority_queue está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si priority_queue está vacío; **False** si no lo está.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue <int> q1, s2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The priority_queue q1 is empty." << endl;  
   else  
      cout << "The priority_queue q1 is not empty." << endl;  
  
   if ( s2.empty( ) )  
      cout << "The priority_queue s2 is empty." << endl;  
   else  
      cout << "The priority_queue s2 is not empty." << endl;  
}  
```  
  
```Output  
The priority_queue q1 is not empty.  
The priority_queue s2 is empty.  
```  
  
##  <a name="pop"></a> priority_queue::pop  
 Quita el elemento más grande de priority_queue desde la posición superior.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Comentarios  
 La priority_queue no debe estar vacía para aplicar la función de miembro. La parte superior de priority_queue está siempre ocupada por el elemento más grande del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   priority_queue <int>::size_type i, iii;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
  
   q1.pop( );  
  
   iii = q1.size( );  
   cout << "After a pop, the priority_queue length is "   
        << iii << "." << endl;  
  
   const int& iv = q1.top( );  
   cout << "After a pop, the element at the top of the "  
        << "priority_queue is " << iv << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
After a pop, the priority_queue length is 2.  
After a pop, the element at the top of the priority_queue is 20.  
```  
  
##  <a name="priority_queue"></a> priority_queue::priority_queue  
 Construye un objeto priority_queue que está vacío o que es una copia de un intervalo de un objeto contenedor base o de otro priority_queue.  
  
```  
priority_queue();

explicit priority_queue(const Traits&_comp);

priority_queue(const Traits&_comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp);

template <class InputIterator>  
priority_queue(InputIterator first, InputIterator last, const Traits&_comp, const container_type& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 *_ comp*  
 Función de comparación de tipo **constTraits** usada para ordenar los elementos de priority_queue, que de manera predeterminada es la función de comparación del contenedor base.  
  
 `_Cont`  
 El contenedor base del que el objeto priority_queue creado va a ser una copia.  
  
 `right`  
 El objeto priority_queue del que el conjunto creado va a ser una copia.  
  
 `first`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar.  
  
 `last`  
 Posición del primer elemento más allá del intervalo de elementos que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Cada uno de los tres primeros constructores especifican un priority_queue inicial vacío, el segundo también especifica el tipo de función de comparación (`comp`) que se usará para establecer el orden de los elementos y el tercero especifica explícitamente el `container_type` (`_Cont`) que se va a usar. La palabra clave **explicit** suprime ciertos tipos de conversión automática de tipos.  
  
 El cuarto constructor especifica una copia del objeto priority_queue `right`.  
  
 Los tres últimos constructores copian el intervalo [* primero, último *) de algunos contenedor y utilizar los valores para inicializar un priority_queue cada vez más explícita para especificar el tipo de función de comparación de clase **rasgos** y `container_type`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_ctor.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <deque>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // The first member function declares priority_queue  
   // with a default vector base container  
   priority_queue <int> q1;  
   cout << "q1 = ( ";  
   while ( !q1.empty( ) )  
   {  
      cout << q1.top( ) << " ";  
      q1.pop( );  
   }  
   cout << ")" << endl;  
  
   // Explicitly declares a priority_queue with nondefault  
   // deque base container  
   priority_queue <int, deque <int> > q2;  
   q2.push( 5 );  
   q2.push( 15 );  
   q2.push( 10 );  
   cout << "q2 = ( ";  
   while ( !q2.empty( ) )  
   {  
      cout << q2.top( ) << " ";  
      q2.pop( );  
   }  
   cout << ")" << endl;  
  
   // This method of printing out the elements of a priority_queue  
   // removes the elements from the priority queue, leaving it empty  
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;  
  
   // The third member function declares a priority_queue   
   // with a vector base container and specifies that the comparison   
   // function greater is to be used for ordering elements  
   priority_queue <int, vector<int>, greater<int> > q3;  
   q3.push( 2 );  
   q3.push( 1 );  
   q3.push( 3 );  
   cout << "q3 = ( ";  
   while ( !q3.empty( ) )  
   {  
      cout << q3.top( ) << " ";  
      q3.pop( );  
   }  
   cout << ")" << endl;  
  
   // The fourth member function declares a priority_queue and  
   // initializes it with elements copied from another container:  
   // first, inserting elements into q1, then copying q1 elements into q4  
   q1.push( 100 );  
   q1.push( 200 );  
   priority_queue <int> q4( q1 );  
   cout << "q4 = ( ";     
   while ( !q4.empty( ) )  
   {  
      cout << q4.top( ) << " ";  
      q4.pop( );  
   }  
   cout << ")" << endl;  
  
   // Creates an auxiliary vector object v5 to be used to initialize q5  
   vector <int> v5;  
   vector <int>::iterator v5_Iter;  
   v5.push_back( 10 );  
   v5.push_back( 30 );  
   v5.push_back( 20 );  
   cout << "v5 = ( " ;  
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )  
      cout << *v5_Iter << " ";  
   cout << ")" << endl;  
  
   // The fifth member function declares and  
   // initializes a priority_queue q5 by copying the  
   // range v5[ first,  last) from vector v5  
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q5 = ( ";  
   while ( !q5.empty( ) )  
   {  
      cout << q5.top( ) << " ";  
      q5.pop( );  
   }  
   cout << ")" << endl;  
  
   // The sixth member function declares a priority_queue q6  
   // with a comparison function greater and initializes q6  
   // by copying the range v5[ first,  last) from vector v5  
   priority_queue <int, vector<int>, greater<int> >   
      q6( v5.begin( ), v5.begin( ) + 2 );  
   cout << "q6 = ( ";  
   while ( !q6.empty( ) )  
   {  
      cout << q6.top( ) << " ";  
      q6.pop( );  
   }  
   cout << ")" << endl;  
}  
```  
  
##  <a name="push"></a> priority_queue::push  
 Agrega un elemento a la cola de prioridad basándose en la prioridad del elemento desde operator<.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 El elemento que se ha agregado a la parte superior de priority_queue.  
  
### <a name="remarks"></a>Comentarios  
 La parte superior de priority_queue es la posición ocupada por el elemento más grande del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="size"></a> priority_queue::size  
 Devuelve el número de elementos de priority_queue.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de priority_queue.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue <int> q1, q2;  
   priority_queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The priority_queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 1.  
The priority_queue length is now 2.  
```  
  
##  <a name="size_type"></a> priority_queue::size_type  
 Un tipo entero sin signo que puede representar el número de elementos de priority_queue.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `size_type` del contenedor base adaptado por priority_queue.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.  
  
##  <a name="top"></a> priority_queue::top  
 Devuelve una referencia constante al elemento más grande en la parte superior de la priority_queue.  
  
```  
const_reference top() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento más grande, según lo determinado por la función **Traits**, objeto de priority_queue.  
  
### <a name="remarks"></a>Comentarios  
 La priority_queue no debe estar vacía para aplicar la función de miembro.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_top.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   priority_queue<int> q1;  
  
   q1.push( 10 );  
   q1.push( 30 );  
   q1.push( 20 );  
  
   priority_queue<int>::size_type i;  
   i = q1.size( );  
   cout << "The priority_queue length is " << i << "." << endl;  
  
   const int& ii = q1.top( );  
   cout << "The element at the top of the priority_queue is "  
        << ii << "." << endl;  
}  
```  
  
```Output  
The priority_queue length is 3.  
The element at the top of the priority_queue is 30.  
```  
  
##  <a name="value_type"></a> priority_queue::value_type  
 Un tipo que representa el tipo de objeto almacenado como un elemento en priority_queue.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `value_type` del contenedor base adaptado por priority_queue.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// pqueue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares priority_queues with default deque base container  
   priority_queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   priority_queue<int> q1;  
   q1.push( AnInt );  
   cout << "The element at the top of the priority_queue is "  
        << q1.top( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the top of the priority_queue is 69.  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)


