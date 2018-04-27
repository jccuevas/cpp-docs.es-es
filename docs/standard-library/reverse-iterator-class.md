---
title: reverse_iterator (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
dev_langs:
- C++
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6bd2f74919ba757f7154d534e8dbca91510cdeb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="reverseiterator-class"></a>reverse_iterator (Clase)

La clase de plantilla es un adaptador de iterador que describe un objeto iterador inverso que se comporta como un iterador de acceso aleatorio o bidireccional, pero en orden inverso. Habilita el recorrido hacia atrás de un intervalo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Parámetros

RandomIterator el tipo que representa el iterador que se adaptará para trabajar en orden inverso.

## <a name="remarks"></a>Comentarios

Los contenedores existentes en la Biblioteca estándar de C++ también definen los tipos `reverse_iterator` y `const_reverse_iterator`, y tienen las funciones miembro `rbegin` y `rend` que devuelven iteradores inversos. Estos iteradores tienen semántica de sobrescritura. El `reverse_iterator` adaptador complementa esta funcionalidad, ya que ofrecen una semántica de inserción y también puede usarse con secuencias.

El `reverse_iterator` que requiere un iterador bidireccional no debe llamar a cualquiera de los miembros funciones `operator+=`, `operator+`, `operator-=`, `operator-`, o `operator[]`, que solo se puede usar con los iteradores de acceso aleatorio.

El intervalo de iterador es [*primer*, *última*), donde el corchete de la izquierda indica la inclusión de *primera* y los paréntesis de la derecha indica el inclusión de elementos hasta sin incluirla *última* propio. Se incluyen los mismos elementos en la secuencia inversa [ **rev** - *primer*, **rev** - *última*) para ese if *última* es el elemento de uno más allá-el final de una secuencia, a continuación, el primer elemento **rev** - *primer* en los puntos de secuencia inversa para \*(*última* - 1). La identidad que relaciona todos los iteradores inversos con sus iteradores subyacentes es:

&\*( **reverse_iterator** ( *i* )) == &\*( *i* - 1).

En la práctica esto significa que, en la secuencia inversa, reverse_iterator hará referencia al elemento situado una posición más allá (a la derecha) del elemento al que el iterador se había referido en la secuencia original. Así pues, si un iterador señaló el elemento 6 en la secuencia (2, 4, 6, 8), entonces `reverse_iterator` señalará el elemento 4 en la secuencia inversa (8, 6, 4, 2).

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[reverse_iterator](#reverse_iterator)|Construye un `reverse_iterator` predeterminado o un `reverse_iterator` a partir de un iterador subyacente.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|Tipo que proporciona la diferencia entre dos `reverse_iterator` que hacen referencia a elementos del mismo contenedor.|
|[iterator_type](#iterator_type)|Tipo que proporciona el iterador subyacente para `reverse_iterator`.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento direccionado por `reverse_iterator`.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento direccionado por `reverse_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[base](#base)|Recupera el iterador subyacente de su `reverse_iterator`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator_star](#op_star)|Devuelve el elemento que direcciona un `reverse_iterator`.|
|[operator+](#op_add)|Agrega un desplazamiento a un iterador y devuelve el nuevo `reverse_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|
|[operator++](#op_add_add)|Incrementa el `reverse_iterator` al elemento siguiente.|
|[operator+=](#op_add_eq)|Agrega un desplazamiento especificado desde un `reverse_iterator`.|
|[operator-](#operator-)|Resta un desplazamiento a `reverse_iterator` y devuelve un `reverse_iterator` que señala el elemento en la posición desplazada.|
|[operator--](#operator--)|Disminuye el `reverse_iterator` al elemento anterior.|
|[operator-=](#operator-_eq)|Resta un desplazamiento especificado a un `reverse_iterator`.|
|[operator->](#operator-_gt)|Devuelve un puntero al elemento direccionado por `reverse_iterator`.|
|[operator&#91;&#93;](#op_at)|Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `reverse_iterator` un número especificado de posiciones.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="base"></a>  reverse_iterator::base

Recupera el iterador subyacente de su `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Valor devuelto

El iterador subyacente de `reverse_iterator`.

### <a name="remarks"></a>Comentarios

La identidad que relaciona todos los iteradores inversos con sus iteradores subyacentes es:

&\*( `reverse_iterator` ( *i* )) == &\*( *i* - 1).

En la práctica esto significa que, en la secuencia inversa, el `reverse_iterator` hará referencia al elemento situado una posición más allá (a la derecha) del elemento al que el iterador se había referido en la secuencia original. Así pues, si un iterador señaló el elemento 6 en la secuencia (2, 4, 6, 8), entonces `reverse_iterator` señalará el elemento 4 en la secuencia inversa (8, 6, 4, 2).

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="difference_type"></a>  reverse_iterator::difference_type

Tipo que proporciona la diferencia entre dos `reverse_iterator` que hacen referencia a elementos del mismo contenedor.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo de diferencia `reverse_iterator` es el mismo que el tipo de diferencia del iterador.

El tipo es un sinónimo del nombre de tipo de rasgo del iterador `iterator_traits`\< **RandomIterator**> **::pointer**.

### <a name="example"></a>Ejemplo

Vea [reverse_iterator::operator&#91;&#93;](#op_at) para obtener un ejemplo de cómo declarar y usar `difference_type`.

## <a name="iterator_type"></a>  reverse_iterator::iterator_type

Tipo que proporciona el iterador subyacente para `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Iterator`.

### <a name="example"></a>Ejemplo

Vea [reverse_iterator::base](#base) para obtener un ejemplo de cómo declarar y usar `iterator_type`.

## <a name="op_star"></a>  reverse_iterator::operator*

Devuelve el elemento al que se dirige un iterador reverse_iterator.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El valor de los elementos a los que se dirige el reverse_iterator.

### <a name="remarks"></a>Comentarios

El operador devuelve \*( **actual** - 1).

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="op_add"></a>  reverse_iterator::operator+

Agrega un desplazamiento a un iterador y devuelve el nuevo `reverse_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Parámetros

`Off` El desplazamiento a agregarse para el iterador inverso.

### <a name="return-value"></a>Valor devuelto

Un `reverse_iterator` que se dirige al elemento de desplazamiento.

### <a name="remarks"></a>Comentarios

Solo se puede usar esta función miembro si el `reverse_iterator` cumple los requisitos de un iterador de acceso aleatorio.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
 to the 3rd element in the reversed sequence: 6.
```

## <a name="op_add_add"></a>  reverse_iterator::operator++

Incrementa el reverse_iterator al elemento anterior.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve el `reverse_iterator` preincrementado y el segundo, el operador de postincremento, devuelve una copia del `reverse_iterator` incrementado.

### <a name="remarks"></a>Comentarios

Solo se puede usar esta función miembro si el `reverse_iterator` cumple los requisitos de un iterador bidireccional.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
 to the second element in the reversed sequence: 7.
```

## <a name="op_add_eq"></a>  reverse_iterator::operator+=

Agrega un desplazamiento especificado desde un reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Parámetros

`Off` El desplazamiento que se incrementa el iterador.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento al que se dirige el `reverse_iterator`.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
 in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
 to the third element in the reversed sequence: 6.
```

## <a name="reverse_iterator__operator-"></a>  reverse_iterator::operator-

Resta un desplazamiento a `reverse_iterator` y devuelve un `reverse_iterator` que señala el elemento en la posición desplazada.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Parámetros

`Off` El desplazamiento que se va a restar reverse_iterator.

### <a name="return-value"></a>Valor devuelto

Un `reverse_iterator` que se dirige al elemento de desplazamiento.

### <a name="remarks"></a>Comentarios

Solo se puede usar esta función miembro si el `reverse_iterator` cumple los requisitos de un iterador de acceso aleatorio.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
 in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
 to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iterator__operator--"></a>  reverse_iterator::operator--

Disminuye el reverse_iterator al elemento anterior.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve el `reverse_iterator` prereducido y el segundo, el operador de posdecremento, devuelve una copia del `reverse_iterator` reducido.

### <a name="remarks"></a>Comentarios

Solo se puede usar esta función miembro si el `reverse_iterator` cumple los requisitos de un iterador bidireccional.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
 in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
 to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iterator__operator-_eq"></a>  reverse_iterator::operator-=

Resta un desplazamiento especificado a un `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Parámetros

`Off` El desplazamiento que se va a restar el `reverse_iterator`.

### <a name="remarks"></a>Comentarios

Solo se puede usar esta función miembro si el `reverse_iterator` cumple los requisitos de un iterador de acceso aleatorio.

El operador evalúa **current** + _ *Off*. Después, devuelve **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
 in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
 to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="op_arrow"></a>  reverse_iterator::operator-&gt;

Devuelve un puntero al elemento direccionado por `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento al que se dirige el `reverse_iterator`.

### <a name="remarks"></a>Comentarios

El operador devuelve **&\*\*this**.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="op_at"></a>  reverse_iterator::operator[]

Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `reverse_iterator` un número especificado de posiciones.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Parámetros

`Off` El desplazamiento desde el `reverse_iterator` dirección.

### <a name="return-value"></a>Valor devuelto

La referencia al desplazamiento del elemento.

### <a name="remarks"></a>Comentarios

El operador devuelve **\***( **\*this** + `Off`).

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="pointer"></a>  reverse_iterator::pointer

Tipo que proporciona un puntero a un elemento direccionado por `reverse_iterator`.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del nombre de tipo de rasgo del iterador `iterator_traits`\< *RandomIterator*> **::pointer**.

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reference"></a>  reverse_iterator::reference

Un tipo que proporciona una referencia a un elemento al que se dirige un reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del nombre de tipo de rasgo del iterador `iterator_traits`\< *RandomIterator*> **::reference**.

### <a name="example"></a>Ejemplo

Vea [reverse_iterator::operator&#91;&#93;](#op_at) o [reverse_iterator::operator*](#op_star) para obtener ejemplos de cómo declarar y usar **reference**.

## <a name="reverse_iterator"></a>  reverse_iterator::reverse_iterator

Construye un `reverse_iterator` predeterminado o un `reverse_iterator` a partir de un iterador subyacente.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Parámetros

`right` El iterador que se puede adaptar a un `reverse_iterator`.

### <a name="return-value"></a>Valor devuelto

Un `reverse_iterator` predeterminado o un `reverse_iterator` que adapta un iterador subyacente.

### <a name="remarks"></a>Comentarios

La identidad que relaciona todos los iteradores inversos con sus iteradores subyacentes es:

&\*( `reverse_iterator` ( *i* )) == &\*( *i* - 1).

En la práctica esto significa que, en la secuencia inversa, reverse_iterator hará referencia al elemento situado una posición más allá (a la derecha) del elemento al que el iterador se había referido en la secuencia original. Así pues, si un iterador señaló el elemento 6 en la secuencia (2, 4, 6, 8), entonces `reverse_iterator` señalará el elemento 4 en la secuencia inversa (8, 6, 4, 2).

### <a name="example"></a>Ejemplo

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
