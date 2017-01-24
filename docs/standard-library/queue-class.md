---
title: "queue (Clase) | Microsoft Docs"
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
  - "std.queue"
  - "std::queue"
  - "queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queue (clase)"
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# queue (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de adaptador de contenedor de plantilla que proporciona una restricción de la funcionalidad de algún tipo de contenedor subyacente, limitar el acceso a los elementos de la portada y contraportados. Pueden agregar en la parte posterior o quitar los elementos, y se pueden inspeccionar los elementos en cualquier extremo de la cola.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type, class Container = deque <Type>>  
class queue  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ype*  
 El tipo de datos del elemento que se almacenará en la cola  
  
 `Container`  
 El tipo del contenedor subyacente que se utiliza para implementar la cola.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos de la clase **tipo** estipulado en la primera plantilla son sinónimos de parámetro de un objeto de cola [value_type](#queue__value_type) y debe coincidir con el tipo de elemento de la clase de contenedor subyacente **contenedor** estipulado por el segundo parámetro de plantilla. El **tipo** debe ser asignable, por lo que es posible copiar objetos de ese tipo y para asignar valores a variables de ese tipo.  
  
 Clases de contenedor subyacente adecuado para la cola incluyen [deque](../standard-library/deque-class.md) y [lista](../standard-library/list-class.md), o cualquier otro contenedor de secuencia que admite las operaciones de `front`, **Atrás**, `push_back`, y `pop_front`. La clase de contenedor subyacente se encapsula dentro del adaptador de contenedor, que solo expone el conjunto limitado de las funciones miembro de contenedor de secuencias como una interfaz pública.  
  
 Objetos de la cola son igualdad comparable si y solo si los elementos de la clase **tipo** son comparables igualdad, y menor-que comparable si y solo si los elementos de la clase **tipo** son menores-que comparable.  
  
 Hay tres tipos de adaptadores de contenedor definidos por la STL: pila, cola y priority_queue. Cada uno restringe la funcionalidad de alguna clase de contenedor subyacente para proporcionar una interfaz con precisión controlada a una estructura de datos estándar.  
  
-   El [stack (clase)](../standard-library/stack-class.md) es compatible con una estructura de datos, último en salir (LIFO). Un buen símil sería una pila de platos. Solo se pueden insertar e inspeccionar elementos (platos) en la parte superior de la pila, que es el último elemento al final del contenedor base, y solo se pueden quitar de ahí. La restricción de acceder únicamente al elemento superior es el motivo por el que se usa la clase stack.  
  
-   Queue (clase) es compatible con una estructura de datos, primero en salir (FIFO). Un buen símil sería el de personas que hacen cola en un banco. Se pueden agregar elementos (personas) a la parte posterior de la línea y quitarlos de la parte delantera de la línea. Se puede inspeccionar tanto la parte delantera como trasera de una línea. La restricción de acceso a sólo los elementos de portada y contraportados de esta manera es la razón para utilizar la clase de la cola.  
  
-   El [priority_queue (clase)](../standard-library/priority-queue-class.md) ordena sus elementos para que siempre es el elemento más grande en la parte superior. Admite la inserción de un elemento y la inspección y eliminación del elemento superior. Un buen símil sería el de personas alineadas y organizadas por edad, altura o cualquier otro criterio.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[cola](#queue__queue)|Construye una `queue` que está vacía o que es una copia de un objeto contenedor base.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#queue__container_type)|Un tipo que proporciona el contenedor base debe adaptarse por la `queue`.|  
|[size_type](#queue__size_type)|Tipo entero sin signo que puede representar el número de elementos de un `queue`.|  
|[value_type](#queue__value_type)|Tipo que representa el tipo de objeto almacenado como elemento en una `queue`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[Atrás](#queue__back)|Devuelve una referencia a la última y más recientemente agregado el elemento en la copia de la `queue`.|  
|[vacía](#queue__empty)|Comprueba si la `queue` está vacía.|  
|[parte frontal](#queue__front)|Devuelve una referencia al primer elemento en la parte delantera de la `queue`.|  
|[POP](#queue__pop)|Quita un elemento de la parte delantera de la `queue`.|  
|[inserción](#queue__push)|Agrega un elemento a la parte posterior de la `queue`.|  
|[tamaño](#queue__size)|Devuelve el número de elementos de `queue`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< cola>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namequeuebacka-queueback"></a><a name="queue__back"></a>  Queue:: back  
 Devuelve que una referencia a la última y más recientemente agregado el elemento al final de la cola.  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El último elemento de la cola. Si la cola está vacía, el valor devuelto es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **volver** se asigna a un `const_reference`, no se puede modificar el objeto de cola. Si el valor devuelto de **volver** se asigna a un **referencia**, el objeto de cola se puede modificar.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta obtener acceso a un elemento en una cola vacía.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_back.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 11 );  
  
   int& i = q1.back( );  
   const int& ii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << i   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << ii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuecontainertypea-queuecontainertype"></a><a name="queue__container_type"></a>  Queue:: container_type  
 Un tipo que proporciona el contenedor base debe adaptarse.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Container`. Dos clases de contenedor de secuencia STL, la lista y una clase predeterminados deque, cumplir los requisitos que se usará como el contenedor base para un objeto de cola. También pueden utilizarse tipos definidos por el usuario que cumpla los requisitos.  
  
 Para obtener más información sobre `Container`, vea la sección Comentarios de la [queue clase](../standard-library/queue-class.md) tema.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [cola](#queue__queue) para obtener un ejemplo de cómo declarar y utilizar `container_type`.  
  
##  <a name="a-namequeueemptya-queueempty"></a><a name="queue__empty"></a>  Queue:: Empty  
 Comprueba si una cola está vacía.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** Si la cola está vacía; **false** Si la cola está vacía.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_empty.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue <int> q1, q2;  
  
   q1.push( 1 );  
  
   if ( q1.empty( ) )  
      cout << "The queue q1 is empty." << endl;  
   else  
      cout << "The queue q1 is not empty." << endl;  
  
   if ( q2.empty( ) )  
      cout << "The queue q2 is empty." << endl;  
   else  
      cout << "The queue q2 is not empty." << endl;  
}  
```  
  
```Output  
The queue q1 is not empty.  
The queue q2 is empty.  
```  
  
##  <a name="a-namequeuefronta-queuefront"></a><a name="queue__front"></a>  Queue:: front  
 Devuelve una referencia al primer elemento en la parte delantera de la cola.  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer elemento de la cola. Si la cola está vacía, el valor devuelto es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `front` se asigna a un `const_reference`, no se puede modificar el objeto de cola. Si el valor devuelto de `front` se asigna a un **referencia**, el objeto de cola se puede modificar.  
  
 La función miembro devuelve un **referencia** al primer elemento de la secuencia controlada, que debe estar vacío.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta obtener acceso a un elemento en una cola vacía.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_front.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   int& ii = q1.back( );  
   int& iii = q1.front( );  
  
   cout << "The integer at the back of queue q1 is " << ii   
        << "." << endl;  
   cout << "The integer at the front of queue q1 is " << iii   
        << "." << endl;  
}  
```  
  
##  <a name="a-namequeuepopa-queuepop"></a><a name="queue__pop"></a>  Queue:: POP  
 Quita un elemento de la parte delantera de la cola.  
  
```  
void pop();
```  
  
### <a name="remarks"></a>Comentarios  
 La cola debe estar vacía para aplicar la función miembro. La parte superior de la cola es la posición ocupada por el elemento agregado más recientemente y el último elemento al final del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_pop.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, s2;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
  
   q1.pop( );  
  
   i = q1.size( );  
   cout << "After a pop the queue length is "   
        << i << "." << endl;  
  
   i = q1. front ( );  
   cout << "After a pop, the element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
After a pop the queue length is 2.  
After a pop, the element at the front of the queue is 20.  
```  
  
##  <a name="a-namequeuepusha-queuepush"></a><a name="queue__push"></a>  Queue:: Push  
 Agrega un elemento al final de la cola.  
  
```  
void push(const Type& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 El elemento se agrega al final de la cola.  
  
### <a name="remarks"></a>Comentarios  
 La parte posterior de la cola es la posición ocupada por el elemento agregado más recientemente y el último elemento al final del contenedor.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_push.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1;  
  
   q1.push( 10 );  
   q1.push( 20 );  
   q1.push( 30 );  
  
   queue <int>::size_type i;  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   i = q1.front( );  
   cout << "The element at the front of the queue is "  
        << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 3.  
The element at the front of the queue is 10.  
```  
  
##  <a name="a-namequeuequeuea-queuequeue"></a><a name="queue__queue"></a>  Queue:: Queue  
 Construye una cola que está vacío o que es una copia de un objeto contenedor base.  
  
```  
queue();

explicit queue(const container_type& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El **const** de que la cola construida es ser una copia del contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El contenedor base predeterminado para la cola es deque. También puede especificar la lista como un contenedor base, pero no puede especificar vector, porque carece de los necesarios `pop_front` función miembro.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_queue.cpp  
// compile with: /EHsc  
#include <queue>  
#include <vector>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queue with default deque base container  
   queue <char> q1;  
  
   // Explicitly declares a queue with deque base container  
   queue <char, deque<char> > q2;  
  
   // These lines don't cause an error, even though they  
   // declares a queue with a vector base container  
   queue <int, vector<int> > q3;  
   q3.push( 10 );  
   // but the following would cause an error because vector has   
   // no pop_front member function  
   // q3.pop( );  
  
   // Declares a queue with list base container  
   queue <int, list<int> > q4;  
  
   // The second member function copies elements from a container  
   list<int> li1;  
   li1.push_back( 1 );  
   li1.push_back( 2 );  
   queue <int, list<int> > q5( li1 );  
   cout << "The element at the front of queue q5 is "  
        << q5.front( ) << "." << endl;  
   cout << "The element at the back of queue q5 is "  
        << q5.back( ) << "." << endl;  
}  
```  
  
```Output  
The element at the front of queue q5 is 1.  
The element at the back of queue q5 is 2.  
```  
  
##  <a name="a-namequeuesizea-queuesize"></a><a name="queue__size"></a>  Queue:: Size  
 Devuelve el número de elementos en la cola.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de la cola.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_size.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2;  
   queue <int>::size_type i;  
  
   q1.push( 1 );  
   i = q1.size( );  
   cout << "The queue length is " << i << "." << endl;  
  
   q1.push( 2 );  
   i = q1.size( );  
   cout << "The queue length is now " << i << "." << endl;  
}  
```  
  
```Output  
The queue length is 1.  
The queue length is now 2.  
```  
  
##  <a name="a-namequeuesizetypea-queuesizetype"></a><a name="queue__size_type"></a>  Queue:: size_type  
 Un tipo de entero sin signo que puede representar el número de elementos de una cola.  
  
```  
typedef typename Container::size_type size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la `size_type` del contenedor base adaptado por la cola.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [Queue:: front](#queue__front) para obtener un ejemplo de cómo declarar y utilizar `size_type`.  
  
##  <a name="a-namequeuevaluetypea-queuevaluetype"></a><a name="queue__value_type"></a>  Queue:: value_type  
 Tipo que representa el tipo de objeto almacenado como un elemento en una cola.  
  
```  
typedef typename Container::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de la `value_type` del contenedor base adaptado por la cola.  
  
### <a name="example"></a>Ejemplo  
  
```  
// queue_value_type.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
  
   // Declares queues with default deque base container  
   queue<int>::value_type AnInt;  
  
   AnInt = 69;  
   cout << "The value_type is AnInt = " << AnInt << endl;  
  
   queue<int> q1;  
   q1.push(AnInt);  
   cout << "The element at the front of the queue is "  
        << q1.front( ) << "." << endl;  
}  
```  
  
```Output  
The value_type is AnInt = 69  
The element at the front of the queue is 69.  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

