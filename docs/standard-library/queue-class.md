---
title: queue (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
dev_langs:
- C++
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5442888e8e370892add687c21132e397ae683ac8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861508"
---
# <a name="queue-class"></a>queue (Clase)

Una clase de adaptador de contenedor de plantilla que proporciona una restricción de la función de algunos tipos de contenedor subyacentes y que limita el acceso a los elementos frontal y trasero. Los elementos pueden agregarse en la parte trasera o quitarse de la parte delantera, y pueden inspeccionarse en cualquier extremo de la cola.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>Parámetros

*Tipo* tipo de los datos del elemento que se almacenará en la cola

`Container` El tipo de contenedor subyacente usado para implementar la cola.

## <a name="remarks"></a>Comentarios

Los elementos de la clase **Type** estipulada en el primer parámetro de plantilla de un objeto de cola son sinónimos de [value_type](#value_type) y deben coincidir con el tipo de elemento de la clase de contenedor subyacente **Container** estipulada por el segundo parámetro de plantilla. El **tipo** debe ser asignable, para que sea posible copiar objetos de ese tipo y asignar valores a variables de ese tipo.

Entre las clases de contenedor subyacente adecuadas para la cola se incluyen [deque](../standard-library/deque-class.md) y [list](../standard-library/list-class.md), o cualquier otro contenedor de secuencias que admita las operaciones de `front`, **back**, `push_back` y `pop_front`. La clase de contenedor subyacente se encapsula dentro del adaptador de contenedor, que solo expone el conjunto limitado de las funciones miembro de contenedor de secuencias como una interfaz pública.

Los objetos de la cola solo se pueden someter a una comparación de igualdad si los elementos de la clase **Type** se pueden someter a una comparación de igualdad. Además, solo se pueden someter a una comparación de tipo menor-que si los elementos de la clase **Type** se pueden someter a una comparación de tipo menor-que.

Existen tres tipos de adaptadores de contenedor que se definen mediante la biblioteca estándar de C++: stack, queue y priority_queue. Cada uno restringe la función de alguna clase de contenedor subyacente para proporcionar una interfaz controlada de manera precisa para una estructura de datos estándar.

- La [clase stack](../standard-library/stack-class.md) es compatible con una estructura de datos LIFO (el último en entrar es el primero en salir). Un buen símil sería una pila de platos. Solo se pueden insertar e inspeccionar elementos (platos) en la parte superior de la pila, que es el último elemento al final del contenedor base, y solo se pueden quitar de ahí. La restricción de acceder únicamente al elemento superior es el motivo por el que se usa la clase stack.

- La clase queue es compatible con una estructura de datos FIFO (el primero en entrar es el primero en salir). Un buen símil sería el de personas que hacen cola en un banco. Se pueden agregar elementos (personas) a la parte posterior de la línea y quitarlos de la parte delantera de la línea. Se puede inspeccionar tanto la parte delantera como trasera de una línea. La restricción de acceder únicamente a los elementos delanteros y traseros de esta manera es el motivo por el que se usa la clase queue.

- La [clase priority_queue](../standard-library/priority-queue-class.md) ordena sus elementos de tal modo que el elemento más grande siempre esté en la parte superior. Admite la inserción de un elemento y la inspección y eliminación del elemento superior. Un buen símil sería el de personas alineadas y organizadas por edad, altura o cualquier otro criterio.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[queue](#queue)|Construye una `queue` que está vacía o que es una copia de un objeto contenedor base.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[container_type](#container_type)|Un tipo que proporciona el contenedor base que debe adaptarse mediante `queue`.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `queue`.|
|[value_type](#value_type)|Tipo que representa el tipo de objeto almacenado como elemento en una `queue`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[back](#back)|Devuelve una referencia al último elemento que se ha agregado más recientemente en la parte trasera de `queue`.|
|[empty](#empty)|Comprueba si la `queue` está vacía.|
|[front](#front)|Devuelve una referencia al primer elemento en la parte delantera de `queue`.|
|[pop](#pop)|Quita un elemento de la parte delantera de `queue`.|
|[push](#push)|Agrega un elemento a la parte trasera de `queue`.|
|[size](#size)|Devuelve el número de elementos de `queue`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<queue>

**Espacio de nombres:** std

## <a name="back"></a> queue::back

Devuelve una referencia al último elemento que se ha agregado más recientemente en la parte trasera de la cola.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

El último elemento de la cola. Si la cola está vacía, el valor devuelto es indefinido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de **back** se asigna a `const_reference`, el objeto queue no se puede modificar. Si el valor devuelto de **back** se asigna a una **referencia**, el objeto queue se puede modificar.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento en una cola vacía.  Vea [Iteradores comprobados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="container_type"></a> queue::container_type

Un tipo que proporciona el contenedor base que debe adaptarse.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Container`. Dos clases de contenedor de secuencias de la biblioteca estándar de C++ (la clase list y la clase deque predeterminada) que cumplen los requisitos para usarse como el contenedor base para un objeto queue. También pueden usarse tipos definidos por el usuario que cumplan los requisitos.

Para obtener más información sobre `Container`, vea la sección Comentarios del tema [queue (Clase)](../standard-library/queue-class.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [queue](#queue) para obtener un ejemplo de cómo declarar y usar `container_type`.

## <a name="empty"></a> queue::empty

Comprueba si una cola está vacía.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si la cola está vacía; **False** si no lo está.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="front"></a> queue::front

Devuelve una referencia al primer elemento en la parte delantera de la cola.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

El primer elemento de la cola. Si la cola está vacía, el valor devuelto es indefinido.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `front` se asigna a `const_reference`, el objeto queue no puede modificarse. Si el valor devuelto de `front` se asigna a una **referencia**, el objeto queue puede modificarse.

La función miembro devuelve una **referencia** al primer elemento de la secuencia controlada, que no debe estar vacío.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento en una cola vacía.  Vea [Iteradores comprobados](../standard-library/checked-iterators.md) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="pop"></a> queue::pop

Quita un elemento de la parte delantera de la cola.

```cpp
void pop();
```

### <a name="remarks"></a>Comentarios

La cola no debe estar vacía para aplicar la función miembro. La parte superior de la cola es la posición ocupada por el elemento agregado más recientemente y es el último elemento al final del contenedor.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="push"></a> queue::push

Agrega un elemento a la parte trasera de la cola.

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>Parámetros

`val` El elemento agregado a la parte posterior de la cola.

### <a name="remarks"></a>Comentarios

La parte trasera de la cola es la posición ocupada por el elemento agregado más recientemente y es el último elemento al final del contenedor.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="queue"></a> queue::queue

Construye una cola que está vacía o que es una copia de un objeto contenedor base.

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>Parámetros

`right` El **const** contenedor de los cuales es la cola construida va a ser una copia.

### <a name="remarks"></a>Comentarios

El contenedor base predeterminado para la cola es deque. También puede especificar list como un contenedor base, pero no puede especificar vector, porque le falta la función miembro `pop_front` necesaria.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="size"></a> queue::size

Devuelve el número de elementos de la cola.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud actual de la cola.

### <a name="example"></a>Ejemplo

```cpp
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

## <a name="size_type"></a> queue::size_type

Un tipo entero sin signo que puede representar el número de elementos de una cola.

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `size_type` del contenedor base adaptado por la cola.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [queue::front](#front) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="value_type"></a> queue::value_type

Un tipo que representa el tipo de objeto almacenado como elemento en una cola.

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `value_type` del contenedor base adaptado por la cola.

### <a name="example"></a>Ejemplo

```cpp
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

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
