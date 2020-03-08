---
title: hash_multiset (Clase)
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 7881b1d6775206fbea40c3ba4b15572a6d4b3580
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865150"
---
# <a name="hash_multiset-class"></a>hash_multiset (Clase)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

La clase contenedora hash_multiset es una extensión de la biblioteca estándar de C++ y se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que los valores de los elementos contenidos actúan como valores clave y no es necesario que sean únicos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>Parámetros

\ *clave*
Tipo de datos de elemento que se almacenará en hash_multiset.

*Rasgos*\
Tipo que incluye dos objetos de función, uno de clase Compare que es un predicado binario capaz de comparar dos valores de elemento como claves de ordenación para determinar su orden relativo y una función hash que es un predicado unario que asigna valores de clave de los elementos a enteros sin signo de tipo `size_t`. Este argumento es opcional y `hash_compare<Key, less<Key> >` es el valor predeterminado.

\ de *asignador*
Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de hash_multiset. Este argumento es opcional y el valor predeterminado es `allocator<Key>`.

## <a name="remarks"></a>Observaciones

El hash_multiset es:

- Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado. Es más, es un contenedor asociativo simple porque los valores de elemento son sus valores de clave.

- Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.

- Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.

- Único en el sentido de que cada uno de sus elementos debe tener una clave única. Puesto que hash_multiset también es un contenedor asociativo simple, sus elementos también son únicos.

- Una plantilla de clase porque la funcionalidad que proporciona es genérica e independiente del tipo específico de datos contenido como elementos o claves. Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.

La principal ventaja de usar algoritmos hash en lugar de ordenar es su mayor eficacia: un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con el tiempo proporcional al logaritmo del número de elementos del contenedor de las técnicas de ordenación. El valor de un elemento de un conjunto no se puede cambiar directamente. Lo que se debe hacer es eliminar los valores antiguos e insertar elementos con nuevos valores.

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor. Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash. En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal).

La clase hash_multiset debe ser el contenedor asociativo preferido cuando la aplicación cumpla las condiciones que asocian los valores a sus claves. Los elementos de una clase hash_multiset pueden ser varios y actuar como sus propias claves de ordenación, por lo que las claves no son únicas. Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer más de una vez. Si no se permitieran varias repeticiones de las palabras, la estructura de contenedor adecuada sería un hash_set. Si se asociaron definiciones únicas como valores a la lista de palabras clave únicas, la estructura adecuada para contener estos datos sería una clase hash_map. Si, por el contrario, las definiciones no son únicas, un hash_multimap sería el contenedor preferido.

El objeto hash_multiset ordena la secuencia que controla mediante una llamada a un objeto traits hash almacenado de tipo [value_compare](#value_compare). Se puede obtener acceso a este objeto almacenado mediante una llamada a la función miembro [key_comp](#key_comp). Este tipo de objeto de función debe comportarse igual que un objeto de clase `hash_compare<Key, less<Key> >`. En concreto, para todos los valores *clave* de tipo `Key`, la llamada `Trait(Key)` produce una distribución de valores de tipo `size_t`.

En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario *f*( *x*, *y*) es un objeto de función que tiene dos objetos de argumento x e y, y un valor devuelto de True o False. Una ordenación impuesta en un objeto hash_multiset es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuando tanto *f*( *x*, *y*) como *f*( *y*, *x*) son False. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.

El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor. No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.

El iterador proporcionado por la clase hash_multiset es un iterador bidireccional, pero las funciones miembro de clase insert y hash_multiset tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio hash_multiset de requisitos y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un objeto hash_multiset mínimo de funcionalidad, pero es suficiente para poder comunicarse en un intervalo de iteradores [ `first`, `last`) en el contexto de las funciones miembro de clase.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[hash_multiset](#hash_multiset)|Construye un `hash_multiset` que está vacío o que es una copia de todo o de parte de otro `hash_multiset`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `hash_multiset`.|
|[const_iterator](#const_iterator)|Un tipo que proporciona un iterador bidireccional que puede leer un elemento **const** en el `hash_multiset`.|
|[const_pointer](#const_pointer)|Un tipo que proporciona un puntero a un elemento **const** en un `hash_multiset`.|
|[const_reference](#const_reference)|Un tipo que proporciona una referencia a un elemento **const** almacenado en un `hash_multiset` para leer y realizar operaciones **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Un tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** en el `hash_multiset`.|
|[difference_type](#difference_type)|Tipo entero con signo que proporciona la diferencia entre dos iteradores que direccionan elementos dentro del mismo `hash_multiset`.|
|[iterator](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_multiset`.|
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_multiset`.|
|[key_type](#key_type)|Tipo que describe un objeto almacenado como un elemento de un `hash_set` en su capacidad como criterio de ordenación.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de `hash_multiset`.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_multiset`.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_multiset` invertido.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `hash_multiset`.|
|[value_compare](#value_compare)|Tipo que proporciona dos objetos de función, un predicado binario de la clase compare que puede comparar dos valores de elementos de un `hash_multiset` para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.|
|[value_type](#value_type)|Tipo que describe un objeto almacenado como un elemento de un `hash_multiset` en su capacidad como valor.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento del `hash_multiset`.|
|[cbegin](#cbegin)|Devuelve un iterador constante que direcciona el primer elemento del `hash_multiset`.|
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_multiset`.|
|[clear](#clear)|Borra todos los elementos de un `hash_multiset`.|
|[count](#count)|Devuelve el número de elementos de un `hash_multiset` cuya clave coincide con una clave especificada por un parámetro|
|[crbegin](#crbegin)|Devuelve un iterador constante que direcciona el primer elemento de `hash_multiset` invertido.|
|[crend](#crend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_multiset` invertido.|
|[emplace](#emplace)|Inserta en un `hash_multiset` un elemento construido en contexto.|
|[emplace_hint](#emplace_hint)|Inserta en un `hash_multiset` un elemento construido en contexto, con una sugerencia de colocación.|
|[empty](#empty)|Comprueba si un `hash_multiset` está vacío.|
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_multiset`.|
|[equal_range](#equal_range)|Devuelve un par de iteradores respectivamente al primer elemento de `hash_multiset` cuya clave mayor es que una clave especificada y al primer elemento del `hash_multiset` cuya clave es igual o mayor que la clave especificada.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una clase `hash_multiset` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|
|[find](#find)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_multiset` que tiene una clave equivalente a una clave especificada.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_multiset`.|
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un `hash_multiset`.|
|[key_comp](#key_compare)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `hash_multiset`.|
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de un `hash_multiset` cuya clave es igual o mayor que una clave especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima del `hash_multiset`.|
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento de `hash_multiset` invertido.|
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_multiset` invertido.|
|[size](#size)|Devuelve el número de elementos de `hash_multiset`.|
|[swap](#swap)|Intercambia los elementos de dos `hash_multiset`.|
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de `hash_multiset` cuyo valor de clave es igual o mayor que el de una clave especificada.|
|[value_comp](#value_comp)|Recupera una copia del objeto traits hash usado para aplicar un algoritmo hash y ordenar valores de claves de elementos en un `hash_multiset`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[hash_multiset::operator=](#op_eq)|Reemplaza los elementos del hash_multiset por una copia de otro hash_multiset.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_set >

**Espacio de nombres:** stdext

## <a name="allocator_type"></a>  hash_multiset::allocator_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que representa la clase de asignador para el objeto hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_allocator](#get_allocator) para obtener un ejemplo que usa `allocator_type`.

## <a name="begin"></a>  hash_multiset::begin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador que direcciona el primer elemento del objeto hash_multiset.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona el primer elemento del objeto hash_multiset o la ubicación siguiente a un objeto hash_multiset vacío.

### <a name="remarks"></a>Observaciones

Si el valor devuelto de `begin` se asigna a un `const_iterator`, no se pueden modificar los elementos del objeto hash_multiset. Si el valor devuelto de `begin` se asigna a un `iterator`, se pueden modificar los elementos del objeto hash_multiset.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>  hash_multiset::cbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador const que direcciona el primer elemento del objeto hash_multiset.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona el primer elemento del objeto [hash_multiset](../standard-library/hash-multiset-class.md) o la ubicación siguiente a un `hash_multiset` vacío.

### <a name="remarks"></a>Observaciones

Con el valor devuelto de `cbegin`, los elementos del objeto `hash_multiset` no se pueden modificar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>  hash_multiset::cend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_multiset.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona la ubicación que sigue al último elemento de un objeto [hash_multiset](../standard-library/hash-multiset-class.md). Si el `hash_multiset` está vacío, `hash_multiset::cend == hash_multiset::begin`.

### <a name="remarks"></a>Observaciones

`cend` se usa para comprobar si un iterador ha llegado al final de su `hash_multiset`. El valor devuelto por `cend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>  hash_multiset::clear

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Borra todos los elementos de un objeto hash_multiset.

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multiset::const_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del objeto hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo que usa `const_iterator`.

## <a name="const_pointer"></a>  hash_multiset::const_pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un puntero a un elemento **const** en un objeto hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [const_iterator](#const_iterator) para obtener acceso a los elementos de un objeto hash_multiset **const**.

## <a name="const_reference"></a>  hash_multiset::const_reference

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona una referencia a un elemento **const** almacenado en un objeto hash_multiset para leer operaciones **const** y realizarlas.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del objeto hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar el objeto hash_multiset en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.

## <a name="count"></a>  hash_multiset::count

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve el número de elementos de un objeto hash_multiset cuyo criterio coincide con un criterio especificado por un parámetro.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

\ *clave*
El criterio de los elementos cuya coincidencia debe buscarse a partir del objeto hash_multiset.

### <a name="return-value"></a>Valor devuelto

El número de elementos del objeto hash_multiset con el criterio especificado por un parámetro.

### <a name="remarks"></a>Observaciones

La función miembro devuelve el número de elementos del intervalo siguiente:

\[ lower_bound (*clave*), upper_bound (*clave*)).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro hash_multiset::count.

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_multiset::crbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador const que direcciona el primer elemento de un objeto hash_multiset invertido.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional invertido const que direcciona el primer elemento de un objeto [hash_multiset](../standard-library/hash-multiset-class.md) invertido o lo que fue el último elemento del objeto `hash_multiset` sin invertir.

### <a name="remarks"></a>Observaciones

`crbegin` se usa con un `hash_multiset` invertido igual que [hash_multiset::begin](#begin) se usa con un `hash_multiset`.

Con el valor devuelto de `crbegin`, el objeto `hash_multiset` no se puede modificar.

`crbegin` puede usarse para iterar `hash_multiset` hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>  hash_multiset::crend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_multiset invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona la ubicación siguiente al último elemento de un objeto [hash_multiset](../standard-library/hash-multiset-class.md) invertido (la ubicación que había precedido al primer elemento del objeto `hash_multiset` sin invertir).

### <a name="remarks"></a>Observaciones

`crend` se usa con un `hash_multiset` invertido igual que [hash_multiset::end](#end) se usa con un `hash_multiset`.

Con el valor devuelto de `crend`, el objeto `hash_multiset` no se puede modificar.

Se puede usar `crend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_multiset.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>  hash_multiset::difference_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo entero con signo que proporciona la diferencia entre dos iteradores que direccionan elementos dentro del mismo objeto hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo [ `first`, `last`) entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como la clase vector o deque, admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>  hash_multiset::emplace

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_multiset.

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*val*|Valor de un elemento que se va a insertar en el objeto [hash_multiset](../standard-library/hash-multiset-class.md) a menos que `hash_multiset` ya contenga ese elemento o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente.|

### <a name="return-value"></a>Valor devuelto

La función miembro `emplace` devuelve un iterador que apunta a la posición en la que se insertó el nuevo elemento.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>  hash_multiset::emplace_hint

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_multiset, con una sugerencia de colocación.

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>Parámetros

\ *Val*
Valor de un elemento que se va a insertar en el objeto [hash_multiset](../standard-library/hash-multiset-class.md) a menos que `hash_multiset` ya contenga ese elemento o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente.

*dónde*\
Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (La inserción se puede realizar en tiempo constante amortizado, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a *Where*).

### <a name="return-value"></a>Valor devuelto

La función miembro [hash_multiset::emplace](#emplace) devuelve un iterador que apunta a la posición donde se insertó el nuevo elemento en el objeto `hash_multiset`.

### <a name="remarks"></a>Observaciones

La inserción se puede realizar en tiempo constante amortizado, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a *Where*.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>  hash_multiset::empty

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Prueba si un objeto hash_multiset está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_multiset está vacío; **False** si el objeto hash_multiset no está vacío.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>  hash_multiset::end

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un objeto hash_multiset.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona la ubicación que sigue al último elemento de un objeto hash_multiset. Si el objeto hash_multiset está vacío, hash_multiset::end == hash_multiset::begin.

### <a name="remarks"></a>Observaciones

`end` se usa para comprobar si un iterador ha llegado al final de su hash_multiset. El valor devuelto por `end` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>  hash_multiset::equal_range

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un par de iteradores, respectivamente, al primer elemento de un objeto hash_multiset cuya clave es mayor que una clave especificada y al primer elemento del objeto hash_multiset cuya clave es igual o mayor que la clave especificada.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parámetros

\ *clave*
La clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multiset que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un par de iteradores donde el primero es el [lower_bound](#lower_bound) de la clave y el segundo es el [upper_bound](#upper_bound) de la clave.

Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_multiset::erase

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Quita un elemento o un intervalo de elementos de un hash_multiset de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parámetros

*dónde*\
Posición del elemento que se va a quitar de hash_multiset.

*primer*\
Posición del primer elemento que se quitó de hash_multiset.

*última*\
Posición inmediatamente siguiente al último elemento que se quitó de hash_multiset.

\ *clave*
Clave del elemento que se va a quitar de hash_multiset.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un puntero al final del hash_multiset si no existe ese elemento. Para la tercera función miembro, número de elementos que se quitaron del hash_multiset.

### <a name="remarks"></a>Observaciones

Las funciones miembro nunca producen una excepción.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro hash_multiset::erase.

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>  hash_multiset::find

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador que direcciona la ubicación de un elemento en un objeto hash_multiset que tiene una clave equivalente a una clave especificada.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

\ *clave*
Clave de argumento que debe coincidir con la clave de ordenación de un elemento del objeto hash_multiset que se está buscando.

### <a name="return-value"></a>Valor devuelto

[iterator](#iterator) o [const_iterator](#const_iterator) que direcciona la ubicación de un elemento equivalente a una clave especificada o que dirige la ubicación siguiente al último elemento del objeto hash_multiset si no se encuentra ninguna coincidencia con la clave.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador que direcciona un elemento en el hash_multiset cuya clave de ordenación se `equivalent` a la clave de argumento en un predicado binario que induce a una ordenación basada en una relación de comparabilidad menor que.

Si el valor devuelto de `find` se asigna a un `const_iterator`, no se puede modificar el objeto hash_multiset. Si el valor devuelto de `find` se asigna a un `iterator`, el objeto de hash_multiset se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_multiset::get_allocator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve una copia del objeto de asignador usado para construir el objeto hash_multiset.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Asignador usado por el objeto hash_multiset para administrar la memoria, que es el parámetro de plantilla de clase `Allocator`.

Para obtener más información sobre `Allocator`, vea la sección Comentarios del tema [Clase hash_multiset](../standard-library/hash-multiset-class.md).

### <a name="remarks"></a>Observaciones

Los asignadores de la clase hash_multiset especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="hash_multiset"></a>  hash_multiset::hash_multiset

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Construye un `hash_multiset` que está vacío o que es una copia de todo o de parte de otro `hash_multiset`.

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

*Al*\
Clase de asignador de almacenamiento que se va a utilizar para este objeto `hash_multiset`, que toma como valor predeterminado `Allocator`.

\ *COMP*
Función de comparación de tipo `const Traits` que se utiliza para ordenar los elementos de `hash_multiset`, que toma como valor predeterminado `hash_compare`.

\ *derecha*
`hash_multiset` del que el `hash_multiset` construido va a ser una copia.

*primer*\
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*última*\
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

*IList*\
initializer_list que contiene los elementos que se van a copiar.

### <a name="remarks"></a>Observaciones

Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del objeto `hash_multiset` y que se puede devolver más adelante mediante una llamada a [hash_multiset::get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.

Todos los constructores inicializan sus hash_multisets.

Todos los constructores almacenan un objeto de función de tipo `Traits` que se usa para establecer un orden entre las claves del objeto `hash_multiset` y que se puede devolver más adelante mediante una llamada a [hash_multiset::key_comp](#key_comp). Para obtener más información sobre `Traits`, vea el tema [Clase hash_multiset](../standard-library/hash-multiset-class.md).

Los tres primeros constructores especifican un `hash_multiset`inicial vacío, el segundo especifica el tipo de función de comparación (*COMP*) que se va a usar para establecer el orden de los elementos y el tercero especifica explícitamente el tipo de asignador (*al*) que se va a usar. La palabra clave **explicit** suprime ciertos tipos de conversión automática de tipos.

El cuarto constructor mueve el `Right`de `hash_multiset`.

El quinto, el sexto y el séptimo constructores utilizan una initializer_list.

Los tres últimos constructores copian el intervalo [ `first`, `last`) de un objeto `hash_multiset` especificando de forma cada vez más explícita el tipo de función de comparación de clase Compare y el asignador.

El orden real de los elementos de un contenedor de conjuntos al que se aplica el algoritmo hash depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash y, en general, no se puede predecir como se haría con el contenedor de conjuntos, donde se determina mediante la función de ordenación únicamente.

## <a name="insert"></a>  hash_multiset::insert

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Inserta un elemento o un intervalo de elementos en un hash_multiset.

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>Parámetros

*value*\
Valor de un elemento que se va a insertar en el hash_multiset a menos que el hash_multiset ya contenga ese elemento o, más en general, un elemento cuya clave esté ordenada de manera equivalente.

*dónde*\
Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (La inserción se puede realizar en tiempo constante amortizado, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a *Where*).

*primer*\
Posición del primer elemento que se va a copiar de un hash_multiset.

*última*\
Posición situada más allá del último elemento que se va a copiar de un hash_multiset.

*IList*\
initializer_list que contiene los elementos que se van a copiar.

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones miembro insert devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento.

Las tres funciones miembro siguientes utilizan una initializer_list.

La tercera función miembro inserta la secuencia de valores de elemento en un objeto hash_multiset correspondiente a cada elemento direccionado por un iterador en el intervalo [ `first`, `last`) de un objeto hash_multiset especificado.

### <a name="remarks"></a>Observaciones

La inserción se puede realizar en tiempo constante amortizado para la versión de sugerencia de INSERT, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a *Where*.

## <a name="iterator"></a>  hash_multiset::iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un objeto hash_multiset.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Observaciones

Se puede utilizar un tipo `iterator` para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [Begin](#begin) para obtener un ejemplo de cómo declarar y usar `iterator`.

## <a name="key_comp"></a>  hash_multiset::key_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Recupera una copia del objeto de comparación que se ha usado para ordenar claves de un objeto hash_multiset.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el hash_multiset *rasgos*del parámetro de plantilla, que contiene objetos de función que se usan para aplicar un algoritmo hash y para ordenar los elementos del contenedor.

Para obtener más información sobre los *rasgos* , vea el tema [hash_multiset clase](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Observaciones

El objeto almacenado define una función miembro:

`bool operator<(const Key& _xVal, const Key& _yVal);`

que devuelve **true** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla *Traits*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multiset::key_compare

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona dos objetos de función: un predicado binario de la clase compare que puede comparar dos valores de elementos de un objeto hash_multiset para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Observaciones

`key_compare` es un sinónimo del parámetro de plantilla *traits*.

Para obtener más información sobre los *rasgos* , vea el tema [hash_multiset clase](../standard-library/hash-multiset-class.md) .

Tenga en cuenta que `key_compare` y value_compare son sinónimos para el parámetro de plantilla *Traits*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="key_type"></a>  hash_multiset::key_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un objeto de función que puede comparar criterios de ordenación para determinar el orden relativo de dos elementos en el objeto hash_multiset.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Observaciones

`key_type` es un sinónimo de la *clave*de parámetro de plantilla.

Tenga en cuenta que `key_type` y [value_type](../standard-library/hash-set-class.md#value_type) son sinónimos para el parámetro de plantilla *Key*. Ambos tipos se proporcionan para las clases de conjunto y conjunto múltiple, donde son idénticos, para la compatibilidad con las clases de mapa y mapa múltiple, donde son distintos.

Para obtener más información sobre la *clave*, consulte la sección Comentarios del tema [hash_multiset clase](../standard-library/hash-multiset-class.md) .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.

## <a name="lower_bound"></a>  hash_multiset::lower_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador al primer elemento de un objeto hash_multiset cuyo valor de clave es igual o mayor que el de una clave especificada.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

\ *clave*
La clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multiset que se está buscando.

### <a name="return-value"></a>Valor devuelto

[Iterator](#iterator) o [const_iterator](#const_iterator) que direcciona la ubicación del primer elemento en un objeto hash_multiset que tiene un valor de clave igual o mayor que la clave de argumento, o que direcciona la ubicación siguiente al último elemento del objeto hash_multiset si no se encuentra ninguna coincidencia con la clave.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>  hash_multiset::max_size

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve la longitud máxima del objeto hash_multiset.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud máxima posible del objeto hash_multiset.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multiset::operator=

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Reemplaza los elementos del hash_multiset por una copia de otro hash_multiset.

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*right*|Objeto [hash_multiset](../standard-library/hash-multiset-class.md) que se copia en el objeto `hash_multiset`.|

### <a name="remarks"></a>Observaciones

Después de borrar los elementos existentes en un `hash_multiset`, `operator=` copia o mueve el contenido de la *derecha* al `hash_multiset`.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_multiset::pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un puntero a un elemento de un objeto hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Observaciones

Se puede utilizar un tipo `pointer` para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto multiset.

## <a name="rbegin"></a>  hash_multiset::rbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador que direcciona el primer elemento en un objeto hash_multiset invertido.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional invertido que direcciona el primer elemento de un objeto hash_multiset invertido o lo que fue el último elemento del objeto hash_multiset sin invertir.

### <a name="remarks"></a>Observaciones

`rbegin` se usa con un hash_multiset invertido igual que [begin](#begin) se usa con un hash_multiset.

Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, el objeto hash_multiset no puede modificarse. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, el objeto hash_multiset puede modificarse.

`rbegin` puede usarse para iterar un objeto hash_multiset hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>  hash_multiset::reference

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona una referencia a un elemento almacenado en un objeto hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>  hash_multiset::rend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un objeto hash_multiset invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona la ubicación siguiente al último elemento de un objeto hash_multiset invertido (la ubicación que había precedido al primer elemento del objeto hash_multiset sin invertir).

### <a name="remarks"></a>Observaciones

`rend` se usa con un hash_multiset invertido igual que [end](#end) se usa con un hash_multiset.

Si el valor devuelto de `rend` se asigna a `const_reverse_iterator`, el objeto hash_multiset no puede modificarse. Si el valor devuelto de `rend` se asigna a `reverse_iterator`, el objeto hash_multiset puede modificarse. El valor devuelto por `rend` no se debe desreferenciar.

Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_multiset.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un objeto hash_multiset invertido.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `reverse_iterator` se usa para iterar el objeto hash_multiset en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="size"></a>  hash_multiset::size

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve el número de elementos del objeto hash_multiset.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud actual del objeto hash_multiset.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>  hash_multiset::size_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo entero sin signo que puede representar el número de elementos de un objeto hash_multiset.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="swap"></a>  hash_multiset::swap

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Intercambia los elementos de dos objetos hash_multiset.

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Objeto hash_multiset de argumentos que proporciona los elementos que se van a intercambiar con el objeto hash_multiset de destino.

### <a name="remarks"></a>Observaciones

La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos objetos hash_multiset cuyos elementos se intercambian.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>  hash_multiset::upper_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Devuelve un iterador al primer elemento de un objeto hash_multiset con un valor de clave que es mayor que una clave especificada.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

\ *clave*
La clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multiset que se está buscando.

### <a name="return-value"></a>Valor devuelto

[Iterator](#iterator) o [const_iterator](#const_iterator) que direcciona la ubicación del primer elemento en un objeto hash_multiset que tiene un valor de clave mayor que la clave de argumento, o que direcciona la ubicación siguiente al último elemento del objeto hash_multiset si no se encuentra ninguna coincidencia con la clave.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>  hash_multiset::value_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Recupera una copia del objeto de comparación usado para ordenar valores de elemento de un objeto hash_multiset.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el hash_multiset *rasgos*del parámetro de plantilla, que contiene objetos de función que se usan para aplicar un algoritmo hash y para ordenar los elementos del contenedor.

Para obtener más información sobre los *rasgos* , vea el tema [hash_multiset clase](../standard-library/hash-multiset-class.md) .

### <a name="remarks"></a>Observaciones

El objeto almacenado define una función miembro:

**operador bool**( **constKey &** `_xVal`, **& de claves const** *_yVal*);

que devuelve **true** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla *Traits*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>  hash_multiset::value_compare

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que proporciona dos objetos de función: un predicado binario de la clase compare que puede comparar dos valores de elementos de un objeto hash_multiset para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Observaciones

`value_compare` es un sinónimo del parámetro de plantilla *traits*.

Para obtener más información sobre los *rasgos* , vea el tema [hash_multiset clase](../standard-library/hash-multiset-class.md) .

Tenga en cuenta que tanto [key_compare](#key_compare) como `value_compare` son sinónimos para el parámetro de plantilla *traits*. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map y multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_comp](#value_comp) para obtener un ejemplo de cómo declarar y usar `value_compare`.

## <a name="value_type"></a>  hash_multiset::value_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multiset](../standard-library/unordered-multiset-class.md).

Tipo que describe un objeto almacenado como un elemento de un objeto hash_multiset en su capacidad como valor.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>Consulte también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
