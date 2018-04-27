---
title: set (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 143dd9cf59da334fa6613434cf8b784ffa869a0b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="set-class"></a>set (Clase)

El conjunto de clases contenedoras de la biblioteca estándar de C++ se usa para el almacenamiento y la recuperación de datos de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave según los cuales se ordenan automáticamente los datos. El valor de un elemento de un conjunto no se puede cambiar directamente. Lo que se debe hacer es eliminar los valores antiguos e insertar elementos con nuevos valores.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Parámetros

`Key` El tipo de datos de elemento que se almacenará en el conjunto.

`Traits` El tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el conjunto. Este argumento es opcional y el predicado binario **less** *\<Key>* es el valor predeterminado.

En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).

`Allocator` El tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre el conjunto de la asignación y desasignación de memoria. Este argumento es opcional y el valor predeterminado es **asignador***\<clave>.*

## <a name="remarks"></a>Comentarios

Un conjunto de la biblioteca estándar de C++ es:

- Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado. Es más, es un contenedor asociativo simple porque los valores de elemento son sus valores de clave.

- Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.

- Ordenada, porque sus elementos se ordenan según los valores de clave dentro del contenedor de acuerdo con una función de comparación especificada.

- Único en el sentido de que cada uno de sus elementos debe tener una clave única. Puesto que el conjunto es también un contenedor asociativo simple, sus elementos también son únicos.

Un conjunto también se describe como una clase de plantilla, porque la funcionalidad que proporciona es genérica e independiente del tipo específico de datos contenidos como elementos. En su lugar, el tipo de datos que se usará se especifica como un parámetro en la plantilla de clase junto con la función de comparación y el asignador.

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten estas operaciones explícitamente las realizan de forma eficiente en un tiempo que es proporcional en promedio al logaritmo del número de elementos del contenedor. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.

El conjunto debe ser el contenedor asociativo elegido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves. Los elementos de un conjunto son únicos y actúan como sus propios criterios de ordenación. Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer solo una vez. Si se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería multiset. Si los valores necesitan estar asociados a una lista de palabras clave únicas, un mapa sería una estructura adecuada para contener estos datos. Si, por el contrario, las claves no son únicas, un multimap sería el contenedor preferido.

El conjunto ordena la secuencia que controla mediante la llamada a un objeto de función almacenado de tipo [key_compare](#key_compare). Este objeto almacenado es una función de comparación a la que se puede tener acceso mediante la llamada a la función miembro [key_comp](#key_comp). En general, los elementos deben ser meramente menos que comparables para establecer este orden de forma que, dados dos elementos cualesquiera, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario *f*( *x,y*) es un objeto de función que tiene dos objetos de argumento *x* e *y*, y un valor devuelto de **true** o **false**. Una ordenación impuesta en un conjunto es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos *x* e *y* se definen como equivalentes cuando tanto *f*( *x,y*) como *f*( *y,x*) son false. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.

En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers)

El iterador proporcionado por la clase del conjunto es un iterador bidireccional, pero las funciones miembro de la clase [insert](#insert) y [set](#set) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores [ `First`, `Last`) en el contexto de las funciones miembro de la clase.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[set](#set)|Construye un conjunto que está vacío o que es una copia de todo o de parte de otro conjunto.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el conjunto.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en el conjunto.|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un elemento `const` en un conjunto.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento `const` almacenado en un conjunto para leer y realizar operaciones `const`.|
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` del conjunto.|
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de un conjunto en un intervalo entre elementos a los que apuntan los iteradores.|
|[iterator](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un conjunto.|
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el conjunto.|
|[key_type](#key_type)|El tipo describe un objeto almacenado como un elemento de un conjunto en su capacidad como criterio de ordenación.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de un conjunto.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un conjunto.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un conjunto invertido.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un conjunto.|
|[value_compare](#value_compare)|Tipo que proporciona un objeto de función que puede comparar dos elementos como criterios de ordenación para determinar su orden relativo en el conjunto.|
|[value_type](#value_type)|El tipo describe un objeto almacenado como un elemento de un conjunto en su capacidad como valor.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento del conjunto.|
|[cbegin](#cbegin)|Devuelve un iterador const que direcciona el primer elemento del conjunto.|
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de un conjunto.|
|[clear](#clear)|Borra todos los elementos de un conjunto.|
|[count](#count)|Devuelve el número de elementos de un conjunto cuya clave coincide con una clave especificada por un parámetro.|
|[crbegin](#rbegin)|Devuelve un iterador const que direcciona el primer elemento de un set invertido.|
|[crend](#rend)|Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un set invertido.|
|[emplace](#emplace)|Inserta un elemento construido en contexto dentro de un conjunto.|
|[emplace_hint](#emplace_hint)|Inserta un elemento construido en contexto dentro de un conjunto, con una sugerencia de colocación.|
|[empty](#empty)|Comprueba si un conjunto está vacío.|
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un conjunto.|
|[equal_range](#equal_range)|Devuelve un par de iteradores, respectivamente, al primer elemento de un conjunto cuya clave mayor es que una clave especificada y al primer elemento del conjunto cuya clave es igual o mayor que la clave especificada.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de un conjunto de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|
|[find](#find)|Devuelve un iterador que direcciona la ubicación de un elemento en un conjunto que tiene una clave equivalente a una clave especificada.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el conjunto.|
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un conjunto.|
|[key_comp](#key_comp)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un conjunto.|
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de un conjunto cuyo valor de clave es igual o mayor que el de una clave especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima del conjunto.|
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento en un conjunto invertido.|
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un conjunto invertido.|
|[size](#size)|Devuelve el número de elementos del conjunto.|
|[swap](#swap)|Intercambia los elementos de dos conjuntos.|
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de conjunto con un valor de clave que es mayor que una clave especificada.|
|[value_comp](#value_comp)|Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de un conjunto.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Reemplaza los elementos de un conjunto con una copia de otro conjunto.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<set>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  set::allocator_type

Un tipo que representa la clase de asignador para el objeto de conjunto.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Comentarios

**allocator_type** es sinónimo del parámetro de plantilla [Allocator](../standard-library/set-class.md).

Devuelve el objeto de función utilizado por un conjunto múltiple para ordenar sus elementos, que es el parámetro de plantilla `Allocator`.

Para más información sobre `Allocator`, vea la sección Comentarios del tema [set (Clase)](../standard-library/set-class.md).

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [get_allocator](#get_allocator) cómo se usa `allocator_type`.

## <a name="begin"></a>  set::begin

Devuelve un iterador que direcciona el primer elemento del conjunto.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador bidireccional que se dirige al primer elemento del conjunto o a la ubicación siguiente a un conjunto vacío.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de **begin** se asigna a un `const_iterator`, los elementos del objeto de conjunto no se pueden modificar. Si el valor devuelto de **begin** se asigna a un **iterador**, los elementos del objeto de conjunto se pueden modificar.

### <a name="example"></a>Ejemplo

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a>  set::cbegin

Devuelve un iterador `const` que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador `const` de acceso bidireccional que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  set::cend

Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador `const` de acceso bidireccional que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="clear"></a>  set::clear

Borra todos los elementos de un conjunto.

```cpp
void clear();
```

### <a name="example"></a>Ejemplo

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a>  set::const_iterator

Un tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del conjunto.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [begin](#begin) cómo se usa `const_iterator`.

## <a name="const_pointer"></a>  set::const_pointer

Un tipo que proporciona un puntero a un elemento **const** en un conjunto.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar un [const_iterator](#const_iterator) para obtener acceso a los elementos de un objeto de conjunto constante.

## <a name="const_reference"></a>  set::const_reference

Un tipo que proporciona una referencia a un elemento **const** almacenado en un conjunto para leer operaciones **const** y realizarlas.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Ejemplo

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a>  set::const_reverse_iterator

Un tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del conjunto.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento. Se usa para procesar una iteración en el conjunto en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar el `const_reverse_iterator`.

## <a name="count"></a>  set::count

Devuelve el número de elementos de un conjunto cuya clave coincide con una clave especificada por un parámetro.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

`key` La clave de los elementos que deben coincidir el conjunto.

### <a name="return-value"></a>Valor devuelto

Es 1 si el conjunto contiene un elemento cuyo criterio de ordenación coincide con la clave de parámetro. Es 0 si el conjunto no contiene ningún elemento con una clave coincidente.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos del intervalo siguiente:

[ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) ).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro set::count.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  set::crbegin

Devuelve un iterador const que direcciona el primer elemento de un set invertido.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador constante bidireccional inverso que se dirige al primer elemento de un conjunto invertido o a lo que fue el último elemento del conjunto sin invertir.

### <a name="remarks"></a>Comentarios

`crbegin` se usa con un conjunto invertido igual que [begin](#begin) se usa con un conjunto.

Con el valor devuelto de `crbegin`, el objeto de conjunto no se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a>  set::crend

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un set invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador constante bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un conjunto invertido (la ubicación que había precedido al primer elemento del conjunto sin invertir).

### <a name="remarks"></a>Comentarios

`crend` se usa con un conjunto invertido igual que [end](#end) se usa con un conjunto.

Con el valor devuelto de `crend`, el objeto de conjunto no se puede modificar. El valor devuelto por `crend` no se debe desreferenciar.

Se puede usar `crend` para comprobar si un iterador inverso llegó al final de su conjunto.

### <a name="example"></a>Ejemplo

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>  set::difference_type

Tipo entero con signo que se puede usar para representar el número de elementos de un conjunto en un intervalo entre elementos a los que apuntan los iteradores.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo *[ first,  last)* entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector, admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a>  set::emplace

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el conjunto, a menos que ya contenga un elemento cuyo valor esté ordenado de forma equivalente.|

### <a name="return-value"></a>Valor devuelto

Un [pair](../standard-library/pair-structure.md) cuyo componente bool devuelve true si se realizó una inserción y false si el mapa ya contenía un elemento cuyo valor tenía un valor equivalente en la ordenación. El componente iterator del valor devuelto pair devuelve la dirección donde se insertó un nuevo elemento (si el componente bool es true) o donde ya se encontraba el elemento (si el componente bool es false).

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.

### <a name="example"></a>Ejemplo

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}

```

## <a name="emplace_hint"></a>  set::emplace_hint

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el conjunto a menos que el conjunto ya contenga ese elemento o, más en general, a menos que ya contenga un elemento cuyo valor esté ordenado de manera equivalente.|
|`where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|

### <a name="return-value"></a>Valor devuelto

Iterador al elemento recién insertado.

Si se produjo un error en la inserción porque el elemento ya existe, devuelve un iterador al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.

### <a name="example"></a>Ejemplo

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}

```

## <a name="empty"></a>  set::empty

Comprueba si un conjunto está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el conjunto está vacío, o bien **false** si el conjunto no está vacío.

### <a name="example"></a>Ejemplo

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a>  set::end

Devuelve el iterador más allá del final.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>Valor devuelto

El iterador siguiente al final. Si el conjunto está vacío, `set::end() == set::begin()`.

### <a name="remarks"></a>Comentarios

**end** se usa para comprobar si un iterador sobrepasó el final de su conjunto.

El valor devuelto por **end** no se debe desreferenciar.

Para obtener un ejemplo de código, vea [set::find](#find).

## <a name="equal_range"></a>  set::equal_range

Devuelve un par de iteradores, respectivamente, al primer elemento de un conjunto con una clave mayor o igual que una clave especificada y al primer elemento del conjunto con una clave mayor que la clave especificada.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parámetros

`key` Clave de argumento que se va a comparar con el criterio de ordenación de un elemento del conjunto que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un par de iteradores donde el primero es el [lower_bound](#lower_bound) de la clave y el segundo es el [upper_bound](#upper_bound) de la clave.

Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).

### <a name="example"></a>Ejemplo

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  set::erase

Quita un elemento o un intervalo de elementos de un conjunto de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parámetros

`Where` Posición del elemento que se va a quitar.

`First` Posición del primer elemento va a quitar.

`Last` Posición situada más allá del último elemento que se va a quitar.

`Key` El valor de clave de los elementos que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final del conjunto si no existe ese elemento.

Para la tercera función miembro, devuelve el número de elementos que se han quitado del conjunto.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an intializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}

```

## <a name="find"></a>  set::find

Devuelve un iterador que hace referencia a la ubicación de un elemento en un conjunto que tiene una clave equivalente a una clave especificada.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

`key` El valor de clave que debe coincidir el criterio de ordenación de un elemento del conjunto que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un iterador que hace referencia a la ubicación de un elemento con una clave especificada, o la ubicación que sigue al último elemento del conjunto ( `set::end()`) si no hay coincidencias para la clave.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador que hace referencia a un elemento del conjunto cuya clave equivale al argumento `key` en un predicado binario que induce a una ordenación basada en una relación de comparabilidad menor que.

Si el valor devuelto de **find** se asigna a un **const_iterator**, no se puede modificar el objeto de conjunto establecido. Si el valor devuelto de **find** se asigna a un **iterador**, se puede modificar el objeto de conjunto establecido.

### <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}

```

## <a name="get_allocator"></a>  set::get_allocator

Devuelve una copia del objeto de asignador usado para construir el conjunto.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El asignador usado por el conjunto para administrar la memoria, que es el parámetro de plantilla `Allocator`.

Para más información sobre `Allocator`, vea la sección Comentarios del tema [set (Clase)](../standard-library/set-class.md).

### <a name="remarks"></a>Comentarios

Los asignadores de la clase de conjunto especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  set::insert

Inserta un elemento o un intervalo de elementos en un conjunto.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);


// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);


// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);


// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);


// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);


// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`Val`|Valor de un elemento que se va a insertar en el conjunto a menos que ya contenga un elemento cuyo valor se ordena de forma equivalente.|
|`Where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a `Where`, la inserción se puede realizar en tiempo constante amortizado en lugar de en tiempo logarítmico).|
|`ValTy`|Parámetro de plantilla que especifica el tipo de argumento que el conjunto puede usar para construir un elemento de [value_type](../standard-library/map-class.md#value_type) y realiza un reenvío directo de `Val` como argumento.|
|`First`|Posición del primer elemento que se va a copiar.|
|`Last`|Posición situada más allá del último elemento que se va a copiar.|
|`InputIterator`|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](../standard-library/map-class.md#value_type).|
|`IList`|El elemento [initializer_list](../standard-library/initializer-list.md) del que se van a copiar los elementos.|

### <a name="return-value"></a>Valor devuelto

Las funciones miembro de un solo elemento, (1) y (2), devuelven un [par](../standard-library/pair-structure.md) cuyo componente `bool` es true si se realizó una inserción y false si el conjunto ya contenía un elemento de valor equivalente en la ordenación. El componente de iterador del par de valor devuelto apunta al elemento recién insertado si el componente `bool` es true, o al elemento existente si el componente `bool` es false.

Las funciones miembro un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el conjunto, o bien, si ya existe un elemento con una clave equivalente, al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador, puntero o referencia.

Durante la inserción de un solo elemento, si se produce una excepción, no se modifica el estado del contenedor. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.

Para tener acceso al componente de iterador de un `pair` `pr` devuelto por la función miembro de un único elemento, utilice `pr.first`; para desreferenciar el iterador dentro del par devuelto, utilice `*pr.first`, especificando un elemento. Para tener acceso al componente `bool`, utilice `pr.second`. Para obtener un ejemplo, vea el código de ejemplo que se muestra más adelante en este artículo.

El [value_type](../standard-library/map-class.md#value_type) de un contenedor es una definición de tipos que pertenece al contenedor y, para set, `set<V>::value_type` es de tipo `const V`.

La función miembro de intervalo (5) inserta la secuencia de valores de elemento en un conjunto que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `s.insert(v.begin(), v.end());` intenta insertar todos los elementos de `v` en `s`. Solo se insertan los elementos que tienen valores únicos en el intervalo; se omiten los duplicados. Para observar qué elementos se rechazan, utilice las versiones de un solo elemento de `insert`.

La función miembro de lista de inicializadores (6) usa una [initializer_list](../standard-library/initializer-list.md) para copiar los elementos al conjunto.

Para la inserción de un elemento construido en contexto (es decir, no se realiza ninguna operación de copia o movimiento), vea [set::emplace](#emplace) y [set::emplace_hint](#emplace_hint).

### <a name="example"></a>Ejemplo

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}

```

## <a name="iterator"></a>  set::iterator

Un tipo que proporciona un [iterador bidireccional](../standard-library/bidirectional-iterator-tag-struct.md) constante que puede leer cualquier elemento de un conjunto.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar un **iterador**.

## <a name="key_comp"></a>  set::key_comp

Recupera una copia del objeto de comparación utilizado para ordenar claves de un conjunto.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que usa un conjunto para ordenar sus elementos, que es el parámetro de plantilla `Traits`.

Para más información sobre `Traits`, vea el tema [set (Clase)](../standard-library/set-class.md).

### <a name="remarks"></a>Comentarios

El objeto almacenado define la función miembro:

**bool operator()**( **const Key&**`_xVal`, **const Key&**`_yVal`);

que devuelve **true** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla **Traits**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a>  set::key_compare

Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el conjunto.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Comentarios

`key_compare` es un sinónimo del parámetro de plantilla `Traits`.

Para más información sobre `Traits`, vea el tema [set (Clase)](../standard-library/set-class.md).

Tenga en cuenta que `key_compare` y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla **Traits**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="key_type"></a>  set::key_type

Un tipo que describe un objeto almacenado como un elemento de un conjunto en su capacidad como criterio de ordenación.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

`key_type` es un sinónimo del parámetro de plantilla `Key`.

Para más información sobre `Key`, vea la sección Comentarios del tema [set (Clase)](../standard-library/set-class.md).

Tenga en cuenta que `key_type` y [value_type](#value_type) son sinónimos para el parámetro de plantilla **Key**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.

## <a name="lower_bound"></a>  set::lower_bound

Devuelve un iterador al primer elemento de un conjunto cuyo valor de clave es igual o mayor que el de una clave especificada.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

`key` Clave de argumento que se va a comparar con el criterio de ordenación de un elemento del conjunto que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un iterador o `const_iterator` que se dirige a la ubicación de un elemento de un conjunto que tiene una clave igual o mayor que la clave de argumento o que se dirige a la ubicación siguiente al último elemento del conjunto si no se encuentra ninguna coincidencia con la clave.

### <a name="example"></a>Ejemplo

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  set::max_size

Devuelve la longitud máxima del conjunto.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud máxima posible del conjunto.

### <a name="example"></a>Ejemplo

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  set::operator=

Reemplaza los elementos de este `set` con elementos de otro `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`right`|El `set` que proporciona los nuevos elementos que se asignarán a este `set`.|

### <a name="remarks"></a>Comentarios

La primera versión de `operator=` usa una [referencia de lvalue](../cpp/lvalue-reference-declarator-amp.md) para `right`, para copiar los elementos de `right` a este `set`.

La segunda versión usa una [referencia de rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) para right. Mueve los elementos de `right` a este `set`.

Antes de que se ejecute la función de operador, se descartan todos los elementos en este `set`.

### <a name="example"></a>Ejemplo

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  set::pointer

Tipo que proporciona un puntero a un elemento de un conjunto.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Comentarios

Se puede usar un **puntero** de tipo para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar un [iterador](#iterator) para obtener acceso a los elementos de un objeto de conjunto.

## <a name="rbegin"></a>  set::rbegin

Devuelve un iterador que direcciona el primer elemento en un conjunto invertido.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Un iterador bidireccional inverso que se dirige al primer elemento de un conjunto invertido o a lo que fue el último elemento del conjunto sin invertir.

### <a name="remarks"></a>Comentarios

`rbegin` se usa con un conjunto invertido igual que [begin](#begin) se usa con un conjunto.

Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, el objeto de conjunto no puede modificarse. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto de conjunto se puede modificar.

`rbegin` puede usarse para recorrer en iteración un conjunto hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a>  set::reference

Tipo que proporciona una referencia a un elemento almacenado en un conjunto.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Ejemplo

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a>  set::rend

Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un conjunto invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Un iterador bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un conjunto invertido (la ubicación que había precedido al primer elemento del conjunto sin invertir).

### <a name="remarks"></a>Comentarios

`rend` se usa con un conjunto invertido igual que [end](#end) se usa con un conjunto.

Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, el objeto de conjunto no puede modificarse. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto de conjunto se puede modificar. El valor devuelto por `rend` no se debe desreferenciar.

Se puede usar `rend` para comprobar si un iterador inverso llegó al final de su conjunto.

### <a name="example"></a>Ejemplo

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // throught a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // throught a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>  set::reverse_iterator

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un conjunto invertido.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `reverse_iterator` se usa para procesar una iteración en el conjunto en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="set"></a>  set::set

Construye un conjunto que está vacío o que es una copia de todo o de parte de otro conjunto.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);


template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`Al`|La clase de asignador de almacenamiento que se usará para este objeto de conjunto, que de forma predeterminada es **Allocator**.|
|`Comp`|Función de comparación de tipo `const Traits` que se utiliza para ordenar los elementos del conjunto, que de forma predeterminada es `Compare`.|
|`Rght`|Conjunto del que el conjunto construido va a ser una copia.|
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|
|`IList`|initializer_list de la que se van a copiar los elementos.|

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del conjunto y que se puede devolver más adelante mediante una llamada a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.

Todos los constructores inicializan sus conjuntos.

Todos los constructores almacenan un objeto de función de tipo **Traits** que se usa para establecer un orden entre las claves del conjunto y que se puede devolver más adelante mediante una llamada a [key_comp](#key_comp).

Los tres primeros constructores especifican un conjunto inicial vacío, el segundo especifica el tipo de función de comparación ( `comp`) que se usará para establecer el orden de los elementos y el tercero especifica explícitamente el tipo de asignador ( `al`) que se va a usar. La palabra clave **explicit** suprime ciertas clases de conversión automática de tipos.

El cuarto constructor especifica una copia del conjunto `right`.

Los tres constructores siguientes utilizan una initializer_list para especificar los elementos.

Los tres constructores siguientes copian el intervalo [ `first`, `last`) de un conjunto especificando de forma cada vez más explícita el tipo de función de comparación de clase **Traits** y **Allocator**.

El octavo constructor especifica una copia del conjunto moviendo `right`.

### <a name="example"></a>Ejemplo

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}

```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a>  set::size

Devuelve el número de elementos del conjunto.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud actual del conjunto.

### <a name="example"></a>Ejemplo

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a>  set::size_type

Tipo entero sin signo que puede representar el número de elementos de un conjunto.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="swap"></a>  set::swap

Intercambia los elementos de dos conjuntos.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`right` Establezca el argumento establecido proporciona los elementos deben intercambiar con el destino.

### <a name="remarks"></a>Comentarios

La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos conjuntos cuyos elementos se intercambian.

### <a name="example"></a>Ejemplo

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a>  set::upper_bound

Devuelve un iterador al primer elemento de un conjunto con una clave que es mayor que una clave especificada.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

`key` Clave de argumento que se va a comparar con el criterio de ordenación de un elemento del conjunto que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un **iterador** o `const_iterator` que se dirige a la ubicación de un elemento de un conjunto que tiene una clave mayor que la clave de argumento o que se dirige a la ubicación siguiente al último elemento del conjunto si no se encuentra ninguna coincidencia con la clave.

### <a name="example"></a>Ejemplo

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a>  set::value_comp

Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de un conjunto.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que usa un conjunto para ordenar sus elementos, que es el parámetro de plantilla `Traits`.

Para más información sobre `Traits`, vea el tema [set (Clase)](../standard-library/set-class.md).

### <a name="remarks"></a>Comentarios

El objeto almacenado define la función miembro:

**bool operator**( **const Key&**`_xVal`, **const Key&**`_yVal`);

que devuelve **True** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que [value_compare](#value_compare) y [key_compare](#key_compare) son sinónimos para el parámetro de plantilla **Traits**. Ambos tipos se proporcionan para las clases de conjunto y conjunto múltiple, donde son idénticos, para la compatibilidad con las clases de mapa y mapa múltiple, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a>  set::value_compare

Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento para determinar su orden relativo en el conjunto.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Comentarios

`value_compare` es un sinónimo del parámetro de plantilla `Traits`.

Para más información sobre `Traits`, vea el tema [set (Clase)](../standard-library/set-class.md).

Tenga en cuenta que [key_compare](#key_compare) y **value_compare** son sinónimos para el parámetro de plantilla **Traits**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_comp](#value_comp) para ver cómo se declara y usa `value_compare`.

## <a name="value_type"></a>  set::value_type

Un tipo que describe un objeto almacenado como un elemento de un conjunto en su capacidad como valor.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Comentarios

`value_type` es un sinónimo del parámetro de plantilla `Key`.

Para más información sobre `Key`, vea la sección Comentarios del tema [set (Clase)](../standard-library/set-class.md).

Tenga en cuenta que [key_type](#key_type) y `value_type` son sinónimos para el parámetro de plantilla **Key**. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```

## <a name="see-also"></a>Vea también

[\<set>](../standard-library/set.md)<br/>
[Contenedores](../cpp/containers-modern-cpp.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
