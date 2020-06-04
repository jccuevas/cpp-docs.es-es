---
title: hash_multimap (Clase)
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: 2fe9056996876d24fba285c0c7aaec8607b2509c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375436"
---
# <a name="hash_multimap-class"></a>hash_multimap (Clase)

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

La clase contenedora hash_multimap es una extensión de la biblioteca estándar de C++ y se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor no necesita ser único y un valor de datos asociado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>Parámetros

*Clave*\
Tipo de datos de clave que se almacenará en hash_multimap.

*Tipo*\
Tipo de datos de elemento que se almacenará en hash_multimap.

*Rasgos*\
El tipo que incluye dos objetos de función, uno de la clase *Traits* que es capaz de comparar dos valores de elemento como claves `size_t`de ordenación para determinar su orden relativo y una función hash que es un predicado unario que asigna valores de clave de asignación de elementos a enteros sin signo de tipo . Este argumento es opcional y `hash_compare<Key, less<Key>>` es el valor predeterminado.

*Asignador*\
Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de hash_multimap. Este argumento es opcional y el valor predeterminado es `allocator<pair <const Key, Type>>`.

## <a name="remarks"></a>Observaciones

El hash_multimap es:

- Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.

- Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.

- Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.

- Múltiple, porque sus elementos no necesitan tener claves únicas, de modo que un valor de clave puede tener asociados varios valores de datos de elemento.

- Un contenedor asociativo de pares, ya que los valores de sus elementos son distintos de sus valores de clave.

- Una plantilla de clase, porque la funcionalidad que proporciona es genérica y, por lo tanto, independiente del tipo específico de datos contenidos como elementos o claves. Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.

La ventaja principal de los algoritmos hash sobre la ordenación es su mayor eficacia; un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con un tiempo proporcional al logaritmo del número de elementos del contenedor en el caso de las técnicas de ordenación. El valor de un elemento de hash_multimap se puede cambiar directamente, pero no su valor de clave asociado. En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos e insertar los nuevos valores de clave asociados a los elementos nuevos.

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor. Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash. En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal).

El hash_multimap debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves. Un modelo para este tipo de estructura es una lista ordenada de palabras clave con valores de cadena asociados que proporcionan por ejemplo definiciones, donde las palabras no siempre están definidas de forma única. Si por el contrario las palabras clave tienen una definición única, de modo que las claves son únicas, el contenedor más adecuado sería hash_map. Por otra parte, si solo se va a almacenar la lista de palabras, el contenedor correcto sería hash_set. Si se permiten varias repeticiones de las palabras, la estructura de contenedor adecuada sería hash_multiset.

El objeto hash_multimap ordena la secuencia que controla mediante una llamada a un objeto `Traits` hash almacenado de tipo [value_compare](../standard-library/value-compare-class.md). Se puede obtener acceso a este objeto almacenado mediante una llamada a la función miembro [key_comp](../standard-library/hash-map-class.md#key_comp). Dicho objeto de función debe comportarse igual que un objeto de clase [hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>`. En concreto, para todos los valores `Key` de tipo `Key`, la llamada a `Traits (Key)` produce una distribución de valores de tipo `size_t`.

En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario f(x, y) es `x` un `y` objeto de función que tiene dos objetos de argumento y un valor devuelto de **true** o **false**. Un orden impuesto a un hash_multimap es un orden débil estricto si el predicado binario es irreflexivo, `x` `y` antisimétrico y transitivo y si la equivalencia es transitiva, donde dos objetos y se definen como equivalentes cuando f(x, y) y f(y, x) son **false.** Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.

El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor. No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.

El iterador proporcionado por la clase hash_multimap es un iterador bidireccional, pero las funciones miembro de clase [insert](#insert) y [hash_multimap](#hash_multimap) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio hash_multimap de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un hash_multimap mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores `[First, Last)` en el contexto de las funciones miembro.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[hash_multimap](#hash_multimap)|Crea una lista de un tamaño concreto o con elementos de un valor concreto o con un `allocator` específico o como copia de algún otro `hash_multimap`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `hash_multimap`.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `hash_multimap`.|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un `hash_multimap`elemento **const** en un archivo .|
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento `hash_multimap` **const** almacenado en a para leer y realizar operaciones **const.**|
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede `hash_multimap`leer cualquier elemento **const** en el archivo .|
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de un `hash_multimap` en un intervalo entre elementos a los que apuntan los iteradores.|
|[Iterador](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_multimap`.|
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_multimap`.|
|[key_type](#key_type)|Tipo que describe el objeto de clave de ordenación que constituye cada elemento de `hash_multimap`.|
|[mapped_type](#mapped_type)|Tipo que representa el tipo de datos almacenados en un `hash_multimap`.|
|[puntero](#pointer)|Tipo que proporciona un puntero a un elemento de `hash_multimap`.|
|[Referencia](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_multimap`.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_multimap` invertido.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `hash_multimap`.|
|[value_type](#value_type)|Tipo que proporciona un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `hash_multimap`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Comenzar](#begin)|Devuelve un iterador que direcciona el primer elemento del `hash_multimap`.|
|[cbegin](#cbegin)|Devuelve un iterador constante que direcciona el primer elemento del `hash_multimap`.|
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_multimap`.|
|[Claro](#clear)|Borra todos los elementos de un `hash_multimap`.|
|[count](#count)|Devuelve el número de elementos de un `hash_multimap` cuya clave coincide con una clave especificada por un parámetro.|
|[crbegin](#crbegin)|Devuelve un iterador constante que direcciona el primer elemento de `hash_multimap` invertido.|
|[crend](#crend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_multimap` invertido.|
|[emplace](#emplace)|Inserta en un `hash_multimap` un elemento construido en contexto.|
|[emplace_hint](#emplace_hint)|Inserta en un `hash_multimap` un elemento construido en contexto, con una sugerencia de colocación.|
|[Vacío](#empty)|Comprueba si un `hash_multimap` está vacío.|
|[Final](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_multimap`.|
|[equal_range](#equal_range)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_multimap`.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de un `hash_multimap` de las posiciones especificadas.|
|[find](#find)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_multimap` que tiene una clave equivalente a una clave especificada.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_multimap`.|
|[insertar](#insert)|Inserta un elemento o un intervalo de elementos en el `hash_multimap` en una posición especificada.|
|[key_comp](#key_comp)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `hash_multimap`.|
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de `hash_multimap` cuyo valor de clave es igual o mayor que el de una clave especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima del `hash_multimap`.|
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento de `hash_multimap` invertido.|
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_multimap` invertido.|
|[Tamaño](#size)|Especifica un nuevo tamaño para un `hash_multimap`.|
|[swap](#swap)|Intercambia los elementos de dos `hash_multimap`.|
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de `hash_multimap` cuyo valor de clave es mayor que el de una clave especificada.|
|[value_comp](#value_comp)|Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de `hash_multimap`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[hash_multimap::operator=](#op_eq)|Reemplaza los elementos de un `hash_multimap` con una copia de otro `hash_multimap`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_map>

**Espacio de nombres:** stdext

## <a name="hash_multimapallocator_type"></a><a name="allocator_type"></a>hash_multimap::allocator_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que representa la clase de asignador para el objeto hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Observaciones

`allocator_type` es un sinónimo del parámetro de plantilla `Allocator`.

Para obtener más información sobre `Allocator`, vea la sección Comentarios del tema [Clase hash_multimap](../standard-library/hash-multimap-class.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get_allocator](#get_allocator) para obtener un ejemplo que usa `allocator_type`.

## <a name="hash_multimapbegin"></a><a name="begin"></a>hash_multimap::comenzar

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador que direcciona el primer elemento del objeto hash_multimap.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona el primer elemento del objeto hash_multimap o la ubicación siguiente a un objeto hash_multimap vacío.

### <a name="remarks"></a>Observaciones

Si el valor `begin` devuelto de `const_iterator`se asigna a un , los elementos del objeto hash_multimap no se pueden modificar. Si el valor `begin` devuelto de `iterator`se asigna a un , los elementos del objeto hash_multimap se pueden modificar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="hash_multimapcbegin"></a><a name="cbegin"></a>hash_multimap::cbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador const que direcciona el primer elemento del objeto hash_multimap.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona el primer elemento del objeto [hash_multimap](../standard-library/hash-multimap-class.md) o la ubicación siguiente a un `hash_multimap` vacío.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="hash_multimapcend"></a><a name="cend"></a>hash_multimap::cend

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_multimap.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona la ubicación que sigue al último elemento de un objeto [hash_multimap](../standard-library/hash-multimap-class.md). Si el `hash_multimap` está vacío, `hash_multimap::cend == hash_multimap::begin`.

### <a name="remarks"></a>Observaciones

`cend` se usa para comprobar si un iterador ha llegado al final de su objeto hash_multimap.

El valor devuelto por `cend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="hash_multimapclear"></a><a name="clear"></a>hash_multimap::claro

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Borra todos los elementos de una asignación hash_multimap.

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se describe el uso de la función miembro hash_multimap::clear.

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="hash_multimapconst_iterator"></a><a name="const_iterator"></a>hash_multimap::const_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del objeto hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

El `const_iterator` definido por hash_multimap apunta a objetos `pair<const Key, Type>`de [value_type](#value_type), que son de tipo . El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.

Para desreferenciar un `const_iterator` `cIter` apuntamiento a `->` un elemento de un hash_multimap, utilice el operador.

Para tener acceso al valor de `cIter->first`la clave para `(*cIter).first`el elemento, utilice , que es equivalente a . Para tener acceso al valor de la `cIter->second`referencia asignada `(*cIter).second`para el elemento, utilice , que es equivalente a .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo que usa `const_iterator`.

## <a name="hash_multimapconst_pointer"></a><a name="const_pointer"></a>hash_multimap::const_pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un puntero a un elemento **const** en un objeto hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto hash_multimap.

## <a name="hash_multimapconst_reference"></a><a name="const_reference"></a>hash_multimap::const_reference

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona una referencia a un elemento **const** almacenado en un objeto hash_multimap para leer operaciones **const** y realizarlas.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="hash_multimapconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>hash_multimap::const_reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del objeto hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar el objeto hash_multimap en orden inverso.

El `const_reverse_iterator` definido por hash_multimap apunta a objetos `pair<const Key, Type>`de [value_type](#value_type), que son de tipo , cuyo primer miembro es la clave del elemento y cuyo segundo miembro es el datum asignado que tiene el elemento.

Para desreferenciar un `const_reverse_iterator` `crIter` apuntamiento a `->` un elemento de un hash_multimap, utilice el operador.

Para tener acceso al valor de `crIter->first`la clave para `(*crIter).first`el elemento, utilice , que es equivalente a . Para tener acceso al valor de la `crIter->second`referencia asignada `(*crIter).second`para el elemento, utilice , que es equivalente a .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar el `const_reverse_iterator`.

## <a name="hash_multimapcount"></a><a name="count"></a>hash_multimap::conde

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve el número de elementos de un objeto hash_multimap cuya clave coincide con una clave especificada por un parámetro.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*Clave*\
La clave de los elementos cuya coincidencia debe buscarse a partir del objeto hash_multimap.

### <a name="return-value"></a>Valor devuelto

1 si el objeto hash_multimap contiene un elemento cuya clave de ordenación coincide con la clave del parámetro; 0 si el objeto hash_multimap no contiene ningún elemento con la misma clave.

### <a name="remarks"></a>Observaciones

La función miembro devuelve el número de elementos del intervalo

**[lower_bound (** `key` **), upper_bound (** `key` **) )**

que tienen una *clave*de valor de clave .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función de miembro hash_multimap::count.

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="hash_multimapcrbegin"></a><a name="crbegin"></a>hash_multimap::crbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador const que direcciona el primer elemento de un objeto hash_multimap invertido.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional invertido const que direcciona el primer elemento de un objeto [hash_multimap](../standard-library/hash-multimap-class.md) invertido o lo que fue el último elemento del objeto `hash_multimap` sin invertir.

### <a name="remarks"></a>Observaciones

`crbegin` se usa con un hash_multimap invertido del mismo modo que [hash_multimap::begin](#begin) se usa con un `hash_multimap`.

Con el valor devuelto de `crbegin`, el objeto `hash_multimap` no se puede modificar.

`crbegin` puede usarse para iterar un objeto `hash_multimap` hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapcrend"></a><a name="crend"></a>hash_multimap::crend

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_multimap invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona la ubicación siguiente al último elemento de un objeto [hash_multimap](../standard-library/hash-multimap-class.md) invertido (la ubicación que había precedido al primer elemento del objeto `hash_multimap` sin invertir).

### <a name="remarks"></a>Observaciones

`crend` se usa con un hash_multimap invertido del mismo modo que [hash_multimap::end](#end) se usa con un hash_multimap.

Con el valor devuelto de `crend`, el objeto `hash_multimap` no se puede modificar.

Se puede usar `crend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_multimap.

El valor devuelto por `crend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="hash_multimapdifference_type"></a><a name="difference_type"></a>hash_multimap::difference_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo entero con signo que se puede usar para representar el número de elementos de un objeto hash_multimap en un intervalo entre elementos a los que apuntan los iteradores.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo *[ first,  last)* entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector, admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="hash_multimapemplace"></a><a name="emplace"></a>hash_multimap::emplace

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_multimap.

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor usado para construir con movimiento un elemento que se va a insertar en el objeto [hash_multimap](../standard-library/hash-multimap-class.md).|

### <a name="return-value"></a>Valor devuelto

La función miembro `emplace` devuelve un iterador que apunta a la posición en la que se insertó el nuevo elemento.

### <a name="remarks"></a>Observaciones

El objeto [hash_multimap::value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapemplace_hint"></a><a name="emplace_hint"></a>hash_multimap::emplace_hint

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_multimap, con una sugerencia de colocación.

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor usado para construir con movimiento un elemento que se va a insertar en el objeto [hash_multimap](../standard-library/hash-multimap-class.md) a menos que `hash_multimap` ya contenga ese elemento (o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente).|
|*_Where*|Sugerencia con respecto al lugar donde se va a empezar a buscar el punto correcto de inserción.|

### <a name="return-value"></a>Valor devuelto

La función miembro [hash_multimap::emplace](#emplace) devuelve un iterador que apunta a la posición donde se insertó el nuevo elemento en el objeto `hash_multimap`.

### <a name="remarks"></a>Observaciones

El objeto [hash_multimap::value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

La inserción puede ocurrir en tiempo constante amortizado, en lugar de tiempo logarítmico, si el punto de inserción sigue inmediatamente *_Where*.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="hash_multimapempty"></a><a name="empty"></a>hash_multimap::vacío

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Prueba si un objeto hash_multimap está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_multimap está vacío; **False** si el objeto hash_multimap no está vacío.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="hash_multimapend"></a><a name="end"></a>hash_multimap::fin

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un objeto hash_multimap.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona la ubicación que sigue al último elemento de un objeto hash_multimap. Si el objeto hash_multimap está vacío, hash_multimap::end == hash_multimap::begin.

### <a name="remarks"></a>Observaciones

`end` se usa para comprobar si un iterador ha llegado al final de su objeto hash_multimap.

El valor devuelto por `end` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="hash_multimapequal_range"></a><a name="equal_range"></a>hash_multimap::equal_range

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un par de iteradores, respectivamente, al primer elemento de un objeto hash_multimap cuya clave es mayor que una clave especificada y al primer elemento del objeto hash_multimap cuya clave es igual o mayor que la clave especificada.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parámetros

*Clave*\
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multimap que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un par de iteradores donde el primero es el elemento [lower_bound](#lower_bound) de la clave y el segundo es el elemento [upper_bound](#upper_bound) de la clave.

Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **primero** y para desreferenciar \*el `pr`iterador de límite inferior, utilice ( . **primero**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **segundo** y para desreferenciar \*el `pr`iterador de límite superior, utilice ( . **segundo**).

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="hash_multimaperase"></a><a name="erase"></a>hash_multimap::borrar

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Quita un elemento o un intervalo de elementos de un hash_multimap de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parámetros

*_Where*\
Posición del elemento que se va a quitar del hash_multimap.

*Primero*\
Posición del primer elemento que se quitó del hash_multimap.

*Última*\
Posición inmediatamente siguiente al último elemento que se quitó del hash_multimap.

*Clave*\
Clave del elemento que se va a quitar del hash_multimap.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados o, si no existe ese elemento, un puntero al final del hash_multimap.

Para la tercera función miembro, devuelve el número de elementos que se han quitado del hash_multimap.

### <a name="remarks"></a>Observaciones

Las funciones miembro nunca producen una excepción.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro hash_multimap::erase.

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="hash_multimapfind"></a><a name="find"></a>hash_multimap::encontrar

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador que direcciona la primera ubicación de un elemento de un objeto hash_multimap que tiene una clave equivalente a una clave especificada.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*Clave*\
Valor de la clave con el que debe coincidir el criterio de ordenación de un elemento del objeto hash_multimap en el que se buscará.

### <a name="return-value"></a>Valor devuelto

Iterador que direcciona la primera ubicación de un elemento con una clave especificada, o la ubicación siguiente al último elemento del objeto hash_multimap si no se encuentra ninguna coincidencia con la clave.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador que `equivalent` direcciona un elemento en el hash_multimap cuya clave de ordenación es a la clave de argumento en un predicado binario que induce un orden basado en una relación de comparabilidad menor que.

Si el valor devuelto de `find` se asigna a `const_iterator`, no se puede modificar el objeto hash_multimap. Si el valor `find` devuelto de `iterator`se asigna a un , se puede modificar el objeto hash_multimap.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapget_allocator"></a><a name="get_allocator"></a>hash_multimap::get_allocator

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve una copia del objeto de asignador usado para construir el objeto hash_multimap.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El asignador usado por el objeto hash_multimap.

### <a name="remarks"></a>Observaciones

Los asignadores de la clase hash_multimap especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_multimaphash_multimap"></a><a name="hash_multimap"></a>hash_multimap::hash_multimap

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Construye un hash_multimap que está vacío o es una copia de todo o de parte de otro hash_multimap.

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Al*|Clase de asignador de almacenamiento que se utilizará para este objeto hash_multimap, que de forma predeterminada es `Allocator`.|
|*Comp*|Función de comparación de tipo `const Traits` que se utiliza para ordenar los elementos del mapa, que de forma predeterminada es `Traits`.|
|*Right*|Asignación de la que el conjunto construido va a ser una copia.|
|*Primero*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Última*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|
|*IList*|initializer_list de la que se va a copiar.|

### <a name="remarks"></a>Observaciones

Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del objeto hash_multimap y que se puede devolver más adelante mediante una llamada a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y se utilizan macros de preprocesamiento para sustituir asignadores alternativos.

Todos los constructores inicializan sus hash_multimap.

Todos los constructores almacenan un objeto de función de tipo `Traits` que se usa para establecer un orden entre las claves del objeto hash_multimap y que se puede devolver más adelante mediante una llamada a [key_comp](#key_comp).

Los tres primeros constructores especifican un hash_multimap inicial vacío; el segundo especifica el tipo de función de comparación (*Comp*) que se utilizará para establecer`_Al`el orden de los elementos y el tercero especifica explícitamente el tipo de asignador ( ) que se utilizará. La palabra clave `explicit` suprime ciertas clases de conversión automática de tipos.

El cuarto constructor especifica una copia del hash_multimap `Right`.

Los tres constructores siguientes copian el intervalo `First, Last)` de un mapa especificando de forma cada vez más explícita el tipo de función de comparación de clase `Traits` y el asignador.

El octavo constructor mueve el hash_multimap `Right`.

Los tres últimos constructores utilizan una initializer_list.

## <a name="hash_multimapinsert"></a><a name="insert"></a>hash_multimap::insertar

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Inserta un elemento o un intervalo de elementos en un hash_multimap.

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor de un elemento que se va a insertar en el hash_multimap a menos que ya contenga ese elemento o, más en general, a menos que ya contenga un elemento cuya clave se ordena de forma equivalente.|
|*Where*|Sugerencia sobre dónde empezar a buscar el punto correcto de inserción.|
|*Primero*|Posición del primer elemento que se va a copiar de un mapa.|
|*Última*|Posición situada más allá del último elemento que se va a copiar de un mapa.|

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones miembro `insert` devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento.

La tercera función miembro utiliza una initializer_list para los elementos que se van a insertar.

La cuarta función miembro inserta la secuencia de valores de elemento en un mapa que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)` de un conjunto especificado.

Las dos últimas funciones miembro `insert` se comportan igual que las dos primeras, salvo que construyen con movimiento el valor insertado.

### <a name="remarks"></a>Observaciones

El [value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

La inserción puede producirse en tiempo `insert`constante amortizado para la versión de sugerencia de , en lugar de tiempo logarítmico, si el punto de inserción sigue inmediatamente *A Dónde*.

## <a name="hash_multimapiterator"></a><a name="iterator"></a>hash_multimap::iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un objeto hash_multimap.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Observaciones

El `iterator` definido por hash_multimap apunta a objetos `pair` \< de [value_type](#value_type), que son de tipo **const Key, Type**>, cuyo primer miembro es la clave del elemento y cuyo segundo miembro es el datum asignado que tiene el elemento.

Para desreferenciar un **iterador** `Iter` que `->` apunta a un elemento de un hash_multimap, utilice el operador.

Para tener acceso al valor de clave del elemento, use `Iter` -> **first**, que es equivalente a (\* `Iter`). **primero**. Para tener acceso al valor de la referencia asignada del elemento, use `Iter` -> **second**, que es equivalente a (\* `Iter`). **primero**.

Un `iterator` tipo se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar `iterator`.

## <a name="hash_multimapkey_comp"></a><a name="key_comp"></a>hash_multimap::key_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Recupera una copia del objeto de comparación que se ha usado para ordenar claves de un objeto hash_multimap.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que usa un objeto hash_multimap para ordenar sus elementos.

### <a name="remarks"></a>Observaciones

El objeto almacenado define la función miembro

**bool operator(const Key&** `left` **, const Key&** `right` **);**

que **true** devuelve `left` true si precede `right` y no es igual a en el criterio de ordenación.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="hash_multimapkey_compare"></a><a name="key_compare"></a>hash_multimap::key_compare

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el objeto hash_multimap.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Observaciones

`key_compare`es un sinónimo del parámetro de plantilla *Traits*.

Para obtener más información sobre *los rasgos,* consulte el [tema hash_multimap clase.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="hash_multimapkey_type"></a><a name="key_type"></a>hash_multimap::key_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que describe el objeto de clave de ordenación que constituye cada elemento del objeto hash_multimap.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Observaciones

`key_type`es un sinónimo del parámetro de plantilla *Key*.

Para obtener más información sobre *Key*, vea la sección Comentarios del [tema clase hash_multimap.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="hash_multimaplower_bound"></a><a name="lower_bound"></a>hash_multimap::lower_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador al primer elemento de un objeto hash_multimap cuyo valor de clave es igual o mayor que el de una clave especificada.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*Clave*\
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multimap que se está buscando.

### <a name="return-value"></a>Valor devuelto

[Iterator](#iterator) o [const_iterator](#const_iterator) que direcciona la ubicación de un elemento en un objeto hash_multimap que tiene un valor de clave igual o mayor que la clave de argumento, o que direcciona la ubicación siguiente al último elemento del objeto hash_multimap si no se encuentra ninguna coincidencia con la clave.

Si el valor devuelto de `lower_bound` se asigna a `const_iterator`, no se puede modificar el objeto hash_multimap. Si el valor `lower_bound` devuelto de `iterator`se asigna a un , se puede modificar el objeto hash_multimap.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="hash_multimapmapped_type"></a><a name="mapped_type"></a>hash_multimap::mapped_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que representa el tipo de datos almacenado en un objeto hash_multimap.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Observaciones

`mapped_type` es un sinónimo del parámetro de plantilla *Type*.

Para obtener más información sobre *Tipo,* consulte el [tema clase hash_multimap.](../standard-library/hash-multimap-class.md)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.

## <a name="hash_multimapmax_size"></a><a name="max_size"></a>hash_multimap::max_size

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve la longitud máxima del objeto hash_multimap.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud máxima posible del objeto hash_multimap.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="hash_multimapoperator"></a><a name="op_eq"></a>hash_multimap::operador ?

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Reemplaza los elementos del objeto hash_multimap por una copia de otro objeto hash_multimap.

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Correcto*|Objeto [hash_multimap](../standard-library/hash-multimap-class.md) que se copia a `hash_multimap`.|

### <a name="remarks"></a>Observaciones

Después de borrar cualquier `hash_multimap`elemento `operator=` existente en un , copia `hash_multimap`o mueve el contenido del *derecho* en el archivo .

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
}
```

## <a name="hash_multimappointer"></a><a name="pointer"></a>hash_multimap::pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un puntero a un elemento de un objeto hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Observaciones

Un `pointer` tipo se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar un elemento [iterator](#iterator) para obtener acceso a los elementos de un objeto hash_multimap.

## <a name="hash_multimaprbegin"></a><a name="rbegin"></a>hash_multimap::rbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador que direcciona el primer elemento en un objeto hash_multimap invertido.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional invertido que direcciona el primer elemento de un objeto hash_multimap invertido o lo que fue el último elemento del objeto hash_multimap sin invertir.

### <a name="remarks"></a>Observaciones

`rbegin` se usa con un objeto hash_multimap invertido del mismo modo que [begin](#begin) se usa con un hash_multimap.

Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, no se puede modificar el objeto hash_multimap. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, se puede modificar el objeto hash_multimap.

`rbegin` puede usarse para iterar un objeto hash_multimap hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreference"></a><a name="reference"></a>hash_multimap::referencia

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona una referencia a un elemento almacenado en un objeto hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="hash_multimaprend"></a><a name="rend"></a>hash_multimap::rend

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un objeto hash_multimap invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona la ubicación siguiente al último elemento de un objeto hash_multimap invertido (la ubicación que había precedido al primer elemento del objeto hash_multimap sin invertir).

### <a name="remarks"></a>Observaciones

`rend` se usa con un objeto hash_multimap invertido del mismo modo que [end](#end) se usa con un hash_multimap.

Si el valor devuelto de `rend` se asigna a [const_reverse_iterator](#const_reverse_iterator), no se puede modificar el objeto hash_multimap. Si el valor devuelto de `rend` se asigna a [reverse_iterator](#reverse_iterator), se puede modificar el objeto hash_multimap.

Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_multimap.

El valor devuelto por `rend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="hash_multimapreverse_iterator"></a><a name="reverse_iterator"></a>hash_multimap::reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un objeto hash_multimap invertido.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Observaciones

Un tipo `reverse_iterator` se usa para iterar el objeto hash_multimap en orden inverso.

El `reverse_iterator` definido mediante el objeto hash_multimap apunta a objetos de [value_type](#value_type), que son de tipo `pair`\< **const Key, Type**>. El valor de la clave está disponible mediante el primer miembro del par y el valor del elemento asignado está disponible mediante el segundo miembro del par.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="hash_multimapsize"></a><a name="size"></a>hash_multimap::tamaño

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve el número de elementos de hash_multimap.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud actual de hash_multimap.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro hash_multimap::size.

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="hash_multimapsize_type"></a><a name="size_type"></a>hash_multimap::size_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo entero sin signo que cuenta el número de elementos de un objeto hash_multimap.

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="hash_multimapswap"></a><a name="swap"></a>hash_multimap::swap

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Intercambia los elementos de dos objetos hash_multimap.

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Objeto hash_multimap que proporciona los elementos que se van a intercambiar o el objeto hash_multimap cuyos elementos se van a intercambiar con los del objeto hash_multimap.

### <a name="remarks"></a>Observaciones

La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos objetos hash_multimap cuyos elementos se intercambian.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="hash_multimapupper_bound"></a><a name="upper_bound"></a>hash_multimap::upper_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Devuelve un iterador al primer elemento de un objeto hash_multimap con un valor de clave que es mayor que una clave especificada.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*Clave*\
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_multimap que se está buscando.

### <a name="return-value"></a>Valor devuelto

[Iterator](#iterator) o [const_iterator](#const_iterator) que direcciona la ubicación de un elemento en un objeto hash_multimap que tiene un valor de clave mayor que la clave de argumento, o que direcciona la ubicación siguiente al último elemento del objeto hash_multimap si no se encuentra ninguna coincidencia con la clave.

Si el valor devuelto de `upper_bound` se asigna a `const_iterator`, no se puede modificar el objeto hash_multimap. Si el valor `upper_bound` devuelto de `iterator`se asigna a un , se puede modificar el objeto hash_multimap.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="hash_multimapvalue_comp"></a><a name="value_comp"></a>hash_multimap::value_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

La función miembro devuelve un objeto de función que determina el orden de los elementos de un objeto hash_multimap mediante la comparación de sus valores de clave.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función de comparación que un objeto hash_multimap usa para ordenar sus elementos.

### <a name="remarks"></a>Observaciones

Por un hash_multimap *m*, si dos elementos *e1* (*k1*, *d1*) y *e2*(*k2*, *d2*) son objetos de tipo [value_type](#value_type), `m.key_comp()(k1, k2)`donde *k1* y *k2* son sus claves de tipo [key_type](#key_type) y *d1* y *d2* son sus datos de tipo [mapped_type,](#mapped_type)entonces `m.value_comp()(e1, e2)` es equivalente a . Un objeto almacenado define la función miembro

`bool operator( value_type& left, value_type& right);`

que devuelve **True** si el valor de clave de `left` precede y no es igual al valor de clave de `right` en el criterio de ordenación.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="hash_multimapvalue_type"></a><a name="value_type"></a>hash_multimap::value_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Tipo que representa el tipo de objeto almacenado en un objeto hash_multimap.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Observaciones

`value_type`se declara pair\<const [key_type](#key_type), [mapped_type](#mapped_type)> y no emparejar\<key_type, mapped_type> porque las claves de un contenedor asociativo no se pueden cambiar mediante un iterador o referencia no constante.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
