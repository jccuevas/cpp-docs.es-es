---
title: front_insert_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
ms.openlocfilehash: 455db433aff1c1aa241beeb6e2435807959b7dd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317148"
---
# <a name="front_insert_iterator-class"></a>front_insert_iterator (Clase)

Describe un adaptador de iterador que satisface los requisitos de un iterador de salida. Inserta, en lugar de sobrescribir, elementos en el inicio de una secuencia y proporciona así la semántica que es diferente de la semántica que sobrescribe proporcionada por los iteradores de los contenedores de la secuencia de C++. La clase `front_insert_iterator` se hace plantilla en el tipo de contenedor.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>Parámetros

*Contenedor*\
El tipo de contenedor en cuyo inicio `front_insert_iterator` va a insertar los elementos.

## <a name="remarks"></a>Observaciones

El contenedor debe satisfacer los requisitos para una secuencia de inserción en el inicio donde sea posible insertar elementos al inicio de la secuencia en tiempo constante amortizado. Los contenedores de secuencias de la biblioteca estándar de C++ definidos por las clases [deque](../standard-library/deque-class.md) y [list](../standard-library/list-class.md) proporcionan la función miembro `push_front` necesaria y cumplen estos requisitos. Por el contrario, los contenedores de secuencias definidos por la [clase vector](../standard-library/vector-class.md) no cumplen estos requisitos y no se pueden adaptar para su uso con `front_insert_iterator`s. Un `front_insert_iterator` debe inicializarse siempre con su contenedor.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[container_type](#container_type)|Tipo que representa el contenedor en el que se va a hacer una inserción inicial.|
|[Referencia](#reference)|Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|Operador de desreferenciación utilizado \* `i`  =  `x` para implementar la expresión de iterador de salida para una inserción frontal.|
|[operador++](#op_add_add)|Incrementa el `front_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.|
|[operador](#op_eq)|Operador de asignación utilizado \* `i`  =  `x` para implementar la expresión de iterador de salida para una inserción frontal.|

## <a name="requirements"></a>Requisitos

**Encabezado** \<: iterador>

**Espacio de nombres:** std

## <a name="front_insert_iteratorcontainer_type"></a><a name="container_type"></a>front_insert_iterator::container_type

Tipo que representa el contenedor en el que se va a hacer una inserción inicial.

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Container*.

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iteratorfront_insert_iterator"></a><a name="front_insert_iterator"></a>front_insert_iterator::front_insert_iterator

Crea un iterador que puede insertar elementos en el inicio de un objeto contenedor especificado.

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>Parámetros

*_Cont*\
Objeto contenedor en el que `front_insert_iterator` va a insertar elementos.

### <a name="return-value"></a>Valor devuelto

`front_insert_iterator` para el objeto contenedor del parámetro.

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_front_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_star"></a>front_insert_iterator::operador\*

Desreferencia el iterador de inserción que devuelve el elemento al que se dirige.

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>Valor devuelto

La función miembro devuelve el valor del elemento al que se dirige.

### <a name="remarks"></a>Observaciones

Se utiliza para implementar la expresión = **value** ** \*** de iterador de salida Iter value . Si `Iter` es un iterador que direcciona un elemento de una secuencia, el = **value** ** \*** valor de Iter reemplaza ese elemento por valor y no cambia el número total de elementos de la secuencia.

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_add_add"></a>front_insert_iterator::operador++

Incrementa el `back_insert_iterator` a la siguiente ubicación en la que puede almacenarse un valor.

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

`front_insert_iterator` que dirige a la siguiente ubicación en la que se puede almacenar un valor.

### <a name="remarks"></a>Observaciones

Ambos operadores de incremento previo e incremento posterior devuelven el mismo resultado.

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratoroperator"></a><a name="op_eq"></a>front_insert_iterator::operador ?

Anexa (inserta) un valor en el principio del contenedor.

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>Parámetros

*Val*\
Valor que se va a asignar al contenedor.

### <a name="return-value"></a>Valor devuelto

Referencia al último elemento insertado al principio del contenedor.

### <a name="remarks"></a>Observaciones

El primer operador miembro evalúa `container.push_front( val)` y después devuelve `*this`.

El segundo operador miembro evalúa

`container->push_front((typename Container::value_type&&) val)`,

después, devuelve `*this`.

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="front_insert_iteratorreference"></a><a name="reference"></a>front_insert_iterator::referencia

Tipo que proporciona una referencia a un elemento de una secuencia controlada por el contenedor asociado.

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>Ejemplo

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
