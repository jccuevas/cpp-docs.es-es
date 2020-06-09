---
title: allocator (Clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
ms.openlocfilehash: 5459fdbd445e7823dcc28096a7b7da3c0c5b38cf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617506"
---
# <a name="allocator-class"></a>allocator (Clase)

La plantilla de clase describe un objeto que administra la asignación de almacenamiento y la liberación de las matrices de objetos de tipo `Type` . Un objeto de clase `allocator` es el objeto de asignador predeterminado especificado en los constructores para varias plantillas de clase de contenedor en la biblioteca estándar de C++.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>Parámetros

*Automáticamente*\
Tipo de objeto al que se va a asignar o desasignar almacenamiento.

## <a name="remarks"></a>Observaciones

Todos los contenedores de la biblioteca estándar de C++ tienen un parámetro de plantilla que tiene como valor predeterminado `allocator` . Crear un contenedor con un asignador personalizado confiere control sobre la asignación y la liberación de los elementos de ese contenedor.

Así, por ejemplo, un objeto de asignador puede asignar almacenamiento en un montón privado o en la memoria compartida, o puede optimizar los tamaños de objetos pequeños o grandes. También puede especificar, a través de las definiciones de tipo que proporciona, que el acceso a los elementos tiene que realizarse a través de objetos de descriptor de acceso especiales que administran la memoria compartida, o realizar una recolección automática de elementos no utilizados. Por lo tanto, una clase que asigna almacenamiento con un objeto de asignador debe usar estos tipos para declarar los objetos de puntero y referencia, tal como hacen los contenedores de la biblioteca estándar de C++.

<strong>(Solo C++ 98/03)</strong> Al derivar de la clase allocator, tendrá que proporcionar un struct de [reenlace](#rebind) , cuyo `_Other` typedef haga referencia a la clase recién derivada.

Por lo tanto, un asignador define los siguientes tipos:

- el [puntero](#pointer) se comporta como un puntero a `Type` .

- [const_pointer](#const_pointer) se comporta como un puntero const a `Type` .

- la [referencia](#reference) se comporta como una referencia a `Type` .

- [const_reference](#const_reference) se comporta como una referencia const a `Type` .

Estos `Type` s especifican el formulario que deben tomar los punteros y las referencias para los elementos asignados. ( [allocator::p ointer](#pointer) no es necesariamente el mismo que `Type*` para todos los objetos de asignador, aunque tiene esta definición obvia para la clase `allocator` ).

**C++11 y versiones posteriores:** para permitir las operaciones de movimiento en el asignador, use la interfaz de asignador mínima e implemente el constructor de copias, los operadores == y! = y allocate y deallocate. Para obtener más información y ver un ejemplo, vea [Asignadores](allocators.md)

## <a name="members"></a>Members

### <a name="constructors"></a>Constructores

|||
|-|-|
|[allocator](#allocator)|Constructores usados para crear objetos `allocator`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.|
|[difference_type](#difference_type)|Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.|
|[puntero](#pointer)|Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.|
|[reference](#reference)|Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de tipo `allocator` puede asignar.|
|[value_type](#value_type)|Tipo administrado por el asignador.|

### <a name="functions"></a>Functions

|||
|-|-|
|[address](#address)|Encuentra la dirección de un objeto cuyo valor se especifica.|
|[allocate](#allocate)|Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.|
|[construir](#construct)|Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.|
|[desasignar](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[borrar](#destroy)|Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.|
|[max_size](#max_size)|Devuelve el número de elementos de tipo `Type` que podrían ser asignados por un objeto de clase `allocator` antes de que la memoria libre se agote.|
|[rebind](#rebind)|Estructura que permite que un asignador de objetos de un tipo asigne almacenamiento para objetos de otro tipo.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#op_eq)|Asigna un objeto `allocator` a otro objeto `allocator`.|

### <a name="address"></a>Dirección <a name="address"></a>

Encuentra la dirección de un objeto cuyo valor se especifica.

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

#### <a name="parameters"></a>Parámetros

*Val*\
Valor const o nonconst del objeto cuya dirección se busca.

#### <a name="return-value"></a>Valor devuelto

Puntero const o nonconst al objeto encontrado de valor const o nonconst respectivamente.

#### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven la dirección de *Val*, en el formulario que los punteros deben realizar para los elementos asignados.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_address.cpp
// compile with: /EHsc
#include <memory>
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 8;
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );
   // v1Ptr = v1Alloc.address( k );
   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.
```

### <a name="allocate"></a><a name="allocate"></a>asignación

Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.

```cpp
pointer allocate(size_type count, const void* _Hint);
```

#### <a name="parameters"></a>Parámetros

*contabiliza*\
El número de elementos para los que se puede asignar suficiente espacio de almacenamiento.

*_Hint*\
Puntero const que puede ayudar al objeto de asignador a satisfacer la solicitud de almacenamiento al buscar la dirección de un objeto asignado antes de la solicitud.

#### <a name="return-value"></a>Valor devuelto

Puntero al objeto asignado o nulo si no se ha asignado memoria.

#### <a name="remarks"></a>Observaciones

La función miembro asigna almacenamiento para una matriz de elementos de recuento de tipo `Type` , llamando al operador New (*Count*). Devuelve un puntero al objeto asignado. El argumento de sugerencia ayuda a algunos asignadores a mejorar la localidad de referencia; una opción válida es la dirección de un objeto anteriormente asignado por el mismo objeto de asignador y que aún no se ha desasignado. Para no proporcionar ningún argumento de sugerencia, use un argumento de puntero nulo.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_allocate.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<int> v1Alloc;
   allocator<int>::pointer v1aPtr;
   v1aPtr = v1Alloc.allocate ( 10 );

   int i;
   for ( i = 0 ; i < 10 ; i++ )
   {
      v1aPtr[ i ] = i;
   }

   for ( i = 0 ; i < 10 ; i++ )
   {
      cout << v1aPtr[ i ] << " ";
   }
   cout << endl;
   v1Alloc.deallocate( v1aPtr, 10 );
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="allocator"></a><a name="allocator"></a>Asignador

Constructores usados para crear objetos de asignador.

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
    allocator(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parámetros

*correcta*\
Objeto de asignador que se va a copiar.

#### <a name="remarks"></a>Observaciones

El constructor no hace nada. Pero, en general, un objeto de asignador creado a partir de otro objeto de asignador debe ser igual a él y permitir la mezcla de asignación de objetos y liberación entre los dos objetos de asignador.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_allocator.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int( int i )
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<double> Alloc;
   vector <Int>:: allocator_type v1Alloc;

   allocator<double> cAlloc(Alloc);
   allocator<Int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="const_pointer"></a><a name="const_pointer"></a>const_pointer

Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.

```cpp
typedef const value_type *const_pointer;
```

#### <a name="remarks"></a>Observaciones

El tipo de puntero describe un objeto `ptr` que puede designar, a través de la expresión `*ptr` , cualquier objeto const que puede asignar un objeto de tipo `allocator` .

#### <a name="example"></a>Ejemplo

```cpp
// allocator_const_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 10;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer's address found has a value of: "
        << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer's address found has a value of: 10.
```

### <a name="const_reference"></a><a name="const_reference"></a>const_reference

Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.

```cpp
typedef const value_type& const_reference;
```

#### <a name="remarks"></a>Observaciones

El tipo de referencia describe un objeto que puede designar cualquier objeto const que puede asignar un objeto de tipo `allocator` .

#### <a name="example"></a>Ejemplo

```cpp
// allocator_const_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::const_reference vcref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vcref << ",\n the first element in the vector." << endl;

   // const references can have their elements modified,
   // so the following would generate an error:
   // vcref = 150;
   // but the value of the first element could be modified through
   // its nonconst iterator and the const reference would remain valid
*vfIter = 175;
   cout << "The value of the element referred to by vcref,"
        <<"\n after nofication through its nonconst iterator, is: "
        << vcref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The value of the element referred to by vcref,
after nofication through its nonconst iterator, is: 175.
```

### <a name="construct"></a><a name="construct"></a>construir

Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
    void construct(pointer ptr, _Other&&... val);
```

#### <a name="parameters"></a>Parámetros

*anota*\
Puntero a la ubicación donde se va a crear el objeto.

*Val*\
Valor con el que se va a inicializar el objeto que se está creando.

#### <a name="remarks"></a>Observaciones

La primera función miembro es equivalente a **New** (( `void` \* ) `ptr` ) **Type** ( `val` ).

#### <a name="example"></a>Ejemplo

```cpp
// allocator_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 6, kB = 7;
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The modified vector v1 is:
( 3 7 9 12 15 18 21 ).
```

### <a name="deallocate"></a><a name="deallocate"></a>desasignar

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(pointer ptr, size_type count);
```

#### <a name="parameters"></a>Parámetros

*anota*\
Un puntero al primer objeto que se va a desasignar del almacenamiento.

*contabiliza*\
El número de objetos que se van a desasignar del almacenamiento.

#### <a name="remarks"></a>Observaciones

La función miembro libera almacenamiento para la matriz de objetos de recuento de tipo `Type` que comienza en *ptr*, llamando a `operator delete(ptr)` . El puntero *ptr* debe haber sido devuelto anteriormente por una llamada [a allocate](#allocate) para un objeto de asignador que se compare con ** \* esto**, asignando un objeto de matriz del mismo tamaño y tipo. `deallocate` nunca inicia una excepción.

#### <a name="example"></a>Ejemplo

Para ver un ejemplo de uso de la función miembro, vea [allocator::allocate](#allocate).

### <a name="destroy"></a><a name="destroy"></a>borrar

Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.

```cpp
void destroy(pointer ptr);
```

#### <a name="parameters"></a>Parámetros

*anota*\
Puntero que designa la dirección del objeto que se va a destruir.

#### <a name="remarks"></a>Observaciones

La función miembro destruye el objeto designado por *ptr*, llamando al tipo de destructor `ptr->` **Type**::**~ Type**.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 12, kB = -99;
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The modified vector v1 is:
( 2 4 6 8 10 -99 14 ).
```

### <a name="difference_type"></a><a name="difference_type"></a>difference_type

Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.

```cpp
typedef ptrdiff_t difference_type;
```

#### <a name="remarks"></a>Observaciones

El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de una secuencia que un objeto de tipo `allocator` puede asignar.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_diff_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 0 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1PtrA, v1PtrB;
   const int kA = 4, kB =12;
   v1PtrA = v1Alloc.address( kA );
   v1PtrB = v1Alloc.address( kB );
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;

   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;
   cout << "The difference between the integer's addresses is: "
        << v1diff << "." << endl;
}
```

```Output
The original vector v1 is:
( 0 2 4 6 8 10 12 14 ).
Pointer v1PtrA addresses 4.
Pointer v1PtrB addresses 12.
The difference between the integer's addresses is: 8.
```

### <a name="max_size"></a><a name="max_size"></a>max_size

Devuelve el número de elementos de tipo `Type` que podría asignar un objeto de clase allocator antes de que la memoria libre se agote.

```cpp
size_type max_size() const;
```

#### <a name="return-value"></a>Valor devuelto

Número de elementos que se pueden asignar.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_max_size.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   vector <double> v2;
   vector <double> ::iterator v2Iter;
   vector <double> :: allocator_type v2Alloc;
   allocator<int>::size_type v1size;
   v1size = v1Alloc.max_size( );

   cout << "The number of integers that can be allocated before\n"
        << " the free memory in the vector v1 is used up is: "
        << v1size << "." << endl;

   int ii;
   for ( ii = 1 ; ii <= 7 ; ii++ )
   {
      v2.push_back( ii * 10.0 );
   }

   cout << "The original vector v2 is:\n ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )
      cout << *v2Iter << " ";
   cout << ")." << endl;
   allocator<double>::size_type v2size;
   v2size = v2Alloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v2 is used up is: "
        << v2size << "." << endl;
}
```

### <a name="operator"></a><a name="op_eq"></a>operador =

Asigna un objeto de asignador a otro objeto de asignador.

```cpp
template <class Other>
    allocator<Type>& operator=(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parámetros

*correcta*\
Un objeto de asignador que se va a asignar a otro de esos objetos.

#### <a name="return-value"></a>Valor devuelto

Referencia al objeto de asignador

#### <a name="remarks"></a>Observaciones

El operador de asignaciones de plantilla no hace nada. Pero, en general, un objeto de asignador asignado a otro objeto de asignador debe ser igual a él y permitir la mezcla de asignación de objetos y liberación entre los dos objetos de asignador.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_op_assign.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( ) {
      cout << "Destructing " << ( void* )this << endl;
      bIsConstructed = false;
   };
   Int &operator++( )
   {
      x++;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( )
{
   allocator<Int> Alloc;
   allocator<Int> cAlloc ;
   cAlloc = Alloc;
}
```

### <a name="pointer"></a>Puntero <a name="pointer"></a>

Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.

```cpp
typedef value_type *pointer;
```

#### <a name="remarks"></a>Observaciones

El tipo de puntero describe un objeto `ptr` que puede designar, a través de la expresión ** \* ptr**, cualquier objeto que pueda asignar un objeto de tipo `allocator` .

#### <a name="example"></a>Ejemplo

```cpp
// allocator_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 12;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.
```

### <a name="rebind"></a><a name="rebind"></a>reenlazar

Estructura que permite que un asignador de objetos de un tipo asigne almacenamiento para objetos de otro tipo.

```cpp
struct rebind { typedef allocator<_Other> other; };
```

#### <a name="parameters"></a>Parámetros

*distinta*\
Tipo de elemento para el que se está asignando memoria.

#### <a name="remarks"></a>Observaciones

Esta estructura es útil para asignar memoria para el tipo que difiere del tipo de elemento del contenedor que se va a implementar.

La plantilla de clase de miembro define el tipo. Su única finalidad es proporcionar el **asignador**de nombre de tipo \<_ **Other**> , dado el **asignador**de nombre de tipo \< **Type**> .

Por ejemplo, dado un objeto de asignador `al` de tipo `A` , puede asignar un objeto de tipo `_Other` con la expresión:

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

O bien, puede asignar el nombre de su tipo de puntero si escribe el tipo:

```cpp
A::rebind<Other>::other::pointer
```

#### <a name="example"></a>Ejemplo

```cpp
// allocator_rebind.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

typedef vector<int>::allocator_type IntAlloc;
int main( )
{
   IntAlloc v1Iter;
   vector<int> v1;

   IntAlloc::rebind<char>::other::pointer pszC =
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);

   int * pInt = v1Iter.allocate(10);
}
```

### <a name="reference"></a><a name="reference"></a>referencia

Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.

```cpp
typedef value_type& reference;
```

#### <a name="remarks"></a>Observaciones

El tipo de referencia describe un objeto que puede designar cualquier objeto que pueda asignar un objeto de tipo `allocator` .

#### <a name="example"></a>Ejemplo

```cpp
// allocator_reference.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::reference vref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vref << ",\n the first element in the vector." << endl;

   // nonconst references can have their elements modified
   vref = 150;
   cout << "The element referred to by vref after being modified is: "
        << vref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The element referred to by vref after being modified is: 150.
```

### <a name="size_type"></a><a name="size_type"></a>size_type

Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de tipo `allocator` puede asignar.

```cpp
typedef size_t size_type;
```

#### <a name="example"></a>Ejemplo

```cpp
// allocator_size_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   allocator<double>::size_type vsize;
   vsize = vAlloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v is used up is: "
        << vsize << "." << endl;
}
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Tipo administrado por el asignador.

```cpp
typedef Type value_type;
```

#### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Type`.

#### <a name="example"></a>Ejemplo

```cpp
// allocator_value_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::value_type vecVal = 150.0;
*vfIter = vecVal;
   cout << "The value of the element addressed by vfIter is: "
        << *vfIter << ",\n the first element in the vector." << endl;

   cout << "The modified vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element addressed by vfIter is: 150,
the first element in the vector.
The modified vector v is:
( 150 200 300 400 500 600 700 ).
```

## <a name="helpers"></a>Asistentes

### <a name="allocator_arg_t"></a><a name="allocator_arg_t"></a>allocator_arg_t

```cpp
struct allocator_arg_t { explicit allocator_arg_t() = default; };
inline constexpr allocator_arg_t allocator_arg{};
```

### <a name="uses_allocator"></a><a name="uses_allocator"></a>uses_allocator

```cpp
template <class T, class Alloc> struct uses_allocator;
```
