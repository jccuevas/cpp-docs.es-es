---
title: Clase hash_set | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8a89252039a253d66ec88cc44a9c1e23969b3c2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235885"
---
# <a name="hashset-class"></a>hash_set (Clase)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

La clase contenedora hash_set es una extensión de la biblioteca estándar de C++ y se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que los valores de los elementos contenidos son únicos y actúan como valores clave.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>Parámetros

*Key*<br/>
Tipo de datos de elemento que se almacenará en hash_set.

*Rasgos*<br/>
Tipo que incluye dos objetos de función, uno de clase que es comparar un predicado binario capaz de comparar dos valores de elemento como claves de ordenación para determinar su orden relativo y una función hash que es una clave asignación predicado unario valores de los elementos en tipos sin signo enteros de tipo `size_t`. Este argumento es opcional y `hash_compare<Key, less<Key> >` es el valor predeterminado.

*Asignador*<br/>
Tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria de hash_set. Este argumento es opcional y el valor predeterminado es `allocator<Key>`.

## <a name="remarks"></a>Comentarios

El hash_set es:

- Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado. Es más, es un contenedor asociativo simple porque los valores de elemento son sus valores de clave.

- Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.

- Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.

- Único en el sentido de que cada uno de sus elementos debe tener una clave única. Puesto que hash_set también es un contenedor asociativo simple, sus elementos también son únicos.

- Una clase de plantilla, porque la funcionalidad que proporciona es genérica y, por tanto, independiente del tipo específico de datos contenido como elementos o claves. Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.

La ventaja principal de los algoritmos hash sobre la ordenación es su mayor eficacia; un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con un tiempo proporcional al logaritmo del número de elementos del contenedor en el caso de las técnicas de ordenación. El valor de un elemento de un conjunto no se puede cambiar directamente. Lo que se debe hacer es eliminar los valores antiguos e insertar elementos con nuevos valores.

En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor. Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash. En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal).

El hash_set debe ser el contenedor asociativo preferido cuando la aplicación cumpla las condiciones que asocian los valores a sus claves. Los elementos de un hash_set son únicos y actúan como sus propios criterios de ordenación. Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer solo una vez. Si se permiten varias repeticiones de las palabras, la estructura de contenedor adecuada sería hash_multiset. Si los valores necesitan estar asociados a una lista de palabras clave únicas, un hash_map sería una estructura adecuada para contener estos datos. Si, por el contrario, las claves no son únicas, un hash_multimap sería el contenedor preferido.

El hash_set ordena la secuencia que controla mediante una llamada a un valor hash almacenado `Traits` objeto de tipo [value_compare](#value_compare). Se puede obtener acceso a este objeto almacenado mediante una llamada a la función miembro [key_comp](#key_comp). Este tipo de objeto de función debe comportarse igual que un objeto de clase *hash_compare<Key, less\<Key> >.* En concreto, para todos los valores `key` de tipo Key, la llamada Trait (`key`) produce una distribución de valores de tipo size_t.

En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario *f*( *x*, *y*) es un objeto de función que tiene dos objetos de argumento x e y, y un valor devuelto de True o False. Una ordenación impuesta en un hash_set es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos *x* e *y* se definen como equivalentes cuando *f*( *x*, *y*) y *f*( *y*, *x*) son False. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.

El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor. No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.

El iterador proporcionado por la clase hash_set es un iterador bidireccional, pero las funciones miembro de clase [insert](#insert) y [hash_set](#hash_set) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores [ `first`, `last`) en el contexto de las funciones miembro de clase.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[hash_set](#hash_set)|Construye un `hash_set` que está vacío o que es una copia de todo o de parte de otro `hash_set`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `hash_set`.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `hash_set`.|
|[const_pointer](#const_pointer)|Un tipo que proporciona un puntero a un **const** elemento en un `hash_set`.|
|[const_reference](#const_reference)|Un tipo que proporciona una referencia a un **const** elemento almacenado en un `hash_set` para leer y realizar **const** operaciones.|
|[const_reverse_iterator](#const_reverse_iterator)|Un tipo que proporciona un iterador bidireccional que puede leer cualquier **const** elemento en el `hash_set`.|
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de un `hash_set` en un intervalo entre elementos a los que apuntan los iteradores.|
|[iterator](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_set`.|
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_set`.|
|[key_type](#key_type)|Tipo que describe un objeto almacenado como un elemento de un `hash_set` en su capacidad como criterio de ordenación.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de `hash_set`.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_set`.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_set` invertido.|
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `hash_set`.|
|[value_compare](#value_compare)|Tipo que proporciona dos objetos de función, un predicado binario de la clase compare que puede comparar dos valores de elementos de un `hash_set` para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.|
|[value_type](#value_type)|Tipo que describe un objeto almacenado como un elemento de un `hash_set` en su capacidad como valor.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento del `hash_set`.|
|[cbegin](#cbegin)|Devuelve un iterador constante que direcciona el primer elemento del `hash_set`.|
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_set`.|
|[clear](#clear)|Borra todos los elementos de un `hash_set`.|
|[count](#count)|Devuelve el número de elementos de un `hash_set` cuya clave coincide con una clave especificada por un parámetro.|
|[crbegin](#crbegin)|Devuelve un iterador constante que direcciona el primer elemento de `hash_set` invertido.|
|[crend](#crend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_set` invertido.|
|[emplace](#emplace)|Inserta en un `hash_set` un elemento construido en contexto.|
|[emplace_hint](#emplace_hint)|Inserta en un `hash_set` un elemento construido en contexto, con una sugerencia de colocación.|
|[empty](#empty)|Comprueba si un `hash_set` está vacío.|
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_set`.|
|[equal_range](#equal_range)|Devuelve un par de iteradores respectivamente al primer elemento de `hash_set` cuya clave mayor es que una clave especificada y al primer elemento del `hash_set` cuya clave es igual o mayor que la clave especificada.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una clase `hash_set` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|
|[find](#find)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_set` que tiene una clave equivalente a una clave especificada.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_set`.|
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un `hash_set`.|
|[key_comp](#key_comp)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `hash_set`.|
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de un `hash_set` cuya clave es igual o mayor que una clave especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima del `hash_set`.|
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento de `hash_set` invertido.|
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_set` invertido.|
|[size](#size)|Devuelve el número de elementos de `hash_set`.|
|[swap](#swap)|Intercambia los elementos de dos `hash_set`.|
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de `hash_set` cuyo valor de clave es igual o mayor que el de una clave especificada.|
|[value_comp](#value_comp)|Recupera una copia del objeto traits hash usado para aplicar un algoritmo hash y ordenar valores de claves de elementos en un `hash_set`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[hash_set::operator=](#op_eq)|Reemplaza los elementos de un `hash_set` con una copia de otro `hash_set`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<hash_set>

**Espacio de nombres:** stdext

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que representa la clase de asignador para el objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Comentarios

`allocator_type` es un sinónimo del parámetro de plantilla *asignador*.

Para obtener más información sobre *asignador*, vea la sección Comentarios de la [hash_set (clase)](../standard-library/hash-set-class.md) tema.

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [get_allocator](#get_allocator) cómo se usa `allocator_type`.

## <a name="begin"></a>  hash_set::begin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador que direcciona el primer elemento del objeto hash_set.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona el primer elemento del objeto hash_set o la ubicación siguiente a un objeto hash_set vacío.

### <a name="remarks"></a>Comentarios

Si el valor devuelto de `begin` se asigna a un `const_iterator`, no se puede modificar los elementos del objeto hash_set. Si el valor devuelto de `begin` se asigna a un `iterator`, los elementos del objeto hash_set pueden modificarse.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador const que direcciona el primer elemento del objeto hash_set.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona el primer elemento del objeto [hash_set](../standard-library/hash-set-class.md) o la ubicación siguiente a un `hash_set` vacío.

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del objeto `hash_set` no se pueden modificar.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_set.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional const que direcciona la ubicación que sigue al último elemento de un objeto [hash_set](../standard-library/hash-set-class.md). Si el `hash_set` está vacío, `hash_set::cend == hash_set::begin`.

### <a name="remarks"></a>Comentarios

`cend` se usa para comprobar si un iterador ha llegado al final de su `hash_set`. El valor devuelto por `cend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="clear"></a>  hash_set::clear

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Borra todos los elementos de un objeto hash_set.

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [begin](#begin) cómo se usa `const_iterator`.

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un puntero a un elemento **const** en un objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [const_iterator](#const_iterator) para obtener acceso a los elementos de un objeto hash_set **const**.

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona una referencia a un elemento **const** almacenado en un objeto hash_set para leer operaciones **const** y realizarlas.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento. Se usa para iterar el objeto hash_set en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.

## <a name="count"></a>  hash_set::count

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve el número de elementos de un objeto hash_set cuya clave coincide con una clave especificada por un parámetro.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave de los elementos cuya coincidencia debe buscarse a partir del objeto hash_set.

### <a name="return-value"></a>Valor devuelto

Es 1 si el objeto hash_set contiene un elemento cuyo criterio de ordenación coincide con la clave de parámetro.

Es 0 si el objeto hash_set no contiene ningún elemento con una clave coincidente.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos del intervalo siguiente:

[ **lower_bound** (_ *Key* ), **upper_bound** (\_ *Key* ) ).

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo debe usarse la función miembro hash_set::count.

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador const que direcciona el primer elemento de un objeto hash_set invertido.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona el primer elemento de un objeto [hash_set](../standard-library/hash-set-class.md) invertido o lo que fue el último elemento del objeto `hash_set` sin invertir.

### <a name="remarks"></a>Comentarios

`crbegin` se usa con un hash_set invertido igual que [hash_set::begin](#begin) se usa con un objeto hash_set.

Con el valor devuelto de `crbegin`, el objeto `hash_set` no se puede modificar.

`crbegin` puede usarse para iterar `hash_set` hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un objeto hash_set invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona la ubicación siguiente al último elemento de un objeto [hash_set](../standard-library/hash-set-class.md) invertido (la ubicación que había precedido al primer elemento del objeto `hash_set` sin invertir).

### <a name="remarks"></a>Comentarios

`crend` se usa con un `hash_set` invertido igual que [hash_set::end](#end) se usa con un objeto `hash_set`.

Con el valor devuelto de `crend`, el objeto `hash_set` no se puede modificar.

Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `hash_set`.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo entero con signo que se puede usar para representar el número de elementos de un objeto hash_set en un intervalo entre elementos a los que apuntan los iteradores.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo [ `first`, `last`) entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector o deque, admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_set.

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor de un elemento que se va a insertar en el objeto [hash_set](../standard-library/hash-set-class.md) a menos que `hash_set` ya contenga ese elemento o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente.|

### <a name="return-value"></a>Valor devuelto

El `emplace` función miembro devuelve un par cuyo **bool** componente devuelve **true** si hizo una inserción y **false** si el `hash_set` ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación y cuyo componente de iterador devuelve la dirección donde se insertó un nuevo elemento o donde ya se encontraba el elemento.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Inserta un elemento construido en contexto dentro de un objeto hash_set.

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor de un elemento que se va a insertar en el objeto [hash_set](../standard-library/hash-set-class.md) a menos que `hash_set` ya contenga ese elemento o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente.|
|*_WHERE*|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Inserción se puede realizar en tiempo constante amortizado, en lugar de tiempo logarítmico, si el punto de inserción sigue inmediatamente a *_Where*.)|

### <a name="return-value"></a>Valor devuelto

La función miembro [hash_set::emplace](#emplace) devuelve un iterador que apunta a la posición donde se insertó el nuevo elemento en el objeto `hash_set` o donde se encuentra el elemento existente con una ordenación equivalente.

### <a name="remarks"></a>Comentarios

Inserción se puede realizar en tiempo constante amortizado, en lugar de tiempo logarítmico, si el punto de inserción sigue inmediatamente a *_Where*.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a>  hash_set::empty

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Comprueba si un objeto hash_set está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_set está vacío; **False** si el objeto hash_set no está vacío.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a>  hash_set::end

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un objeto hash_set.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona la ubicación que sigue al último elemento de un objeto hash_set. Si el objeto hash_set está vacío, hash_set::end == hash_set::begin.

### <a name="remarks"></a>Comentarios

`end` se usa para comprobar si un iterador ha llegado al final de su objeto hash_set. El valor devuelto por `end` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un par de iteradores, respectivamente, al primer elemento de un objeto hash_set cuya clave sea igual que una clave especificada y al primer elemento del objeto hash_set cuya clave sea mayor que la clave especificada.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_set que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un par de iteradores donde el primero es el [lower_bound](../standard-library/set-class.md#lower_bound) de la clave y el segundo es el [upper_bound](../standard-library/set-class.md#upper_bound) de la clave.

Para tener acceso al primer iterador de un par pr devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a>  hash_set::erase

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Quita un elemento o un intervalo de elementos de un hash_set de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>Parámetros

*_WHERE*<br/>
Posición del elemento que se quita del hash_set.

*first*<br/>
Posición del primer elemento que se quita del hash_set.

*Último*<br/>
Posición inmediatamente siguiente al último elemento que se quita del hash_set.

*key*<br/>
Clave de los elementos que se van a quitar del hash_set.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un puntero al final del hash_set si no existe ese elemento. Para la tercera función miembro, el número de elementos que se han quitado del hash_set.

### <a name="remarks"></a>Comentarios

Las funciones miembro nunca producen una excepción.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro hash_set::erase.

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a>  hash_set::find

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador que direcciona la ubicación de un elemento en un objeto hash_set que tiene una clave equivalente a una clave especificada.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de argumento que debe coincidir con la clave de ordenación de un elemento del objeto hash_set que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un `iterator` o `const_iterator` que direcciona la ubicación de un elemento equivalente a una clave especificada o que direcciona la ubicación siguiente al último elemento del objeto hash_set si no se encuentra ninguna coincidencia para la clave.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador que direcciona un elemento del objeto hash_set cuyo criterio de ordenación es `equivalent` para el argumento de clave de un predicado binario que induce una ordenación basada en un menor-que la relación de comparabilidad.

Si el valor devuelto de `find` se asigna a un `const_iterator`, no se puede modificar el objeto hash_set. Si el valor devuelto de `find` se asigna a un `iterator`, se puede modificar el objeto hash_set.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve una copia del objeto de asignador usado para construir el objeto hash_set.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El asignador usado por el objeto hash_set para administrar la memoria, que es el parámetro de plantilla *asignador*.

Para obtener más información sobre *asignador*, vea la sección Comentarios de la [hash_set (clase)](../standard-library/hash-set-class.md) tema.

### <a name="remarks"></a>Comentarios

Los asignadores de la clase del objeto hash_set especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Construye un `hash_set` que está vacío o que es una copia de todo o de parte de otro `hash_set`.

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Al*|Clase de asignador de almacenamiento que se va a utilizar para este objeto `hash_set`, que toma como valor predeterminado `Allocator`.|
|*Comp.*|Función de comparación de tipo `const Traits` que se utiliza para ordenar los elementos de `hash_set`, que toma como valor predeterminado `hash_compare`.|
|*Derecha*|`hash_set` del que el `hash_set` construido va a ser una copia.|
|*Primero*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del objeto `hash_set` y que se puede devolver más adelante mediante una llamada a [hash_set::get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.

Todos los constructores inicializan sus hash_sets.

Todos los constructores almacenan un objeto de función de tipo `Traits` que se usa para establecer un orden entre las claves del objeto `hash_set` y que se puede devolver más adelante mediante una llamada a [hash_set::key_comp](#key_comp). Para obtener más información sobre `Traits`, vea el tema [Clase hash_set](../standard-library/hash-set-class.md).

El primer constructor crea un objeto `hash_set` inicial vacío, el segundo especifica el tipo de función de comparación (`Comp`) que se usará para establecer el orden de los elementos y el tercero especifica explícitamente el tipo de asignador (`Al`) que se va a usar. La palabra clave `explicit` suprime ciertas clases de conversión automática de tipos.

Los constructores cuarto y quinto especifican una copia del `hash_set` `Right`.

Los constructores sexto, séptimo y octavo utilizan una initializer_list para los elementos.

Los últimos constructores copian el intervalo [ `First`, `Last`) de un objeto `hash_set` especificando de forma cada vez más explícita el tipo de función de comparación de clase Traits y el asignador.

El octavo constructor mueve el `hash_set` `Right`.

El orden real de los elementos de un contenedor `hash_set` depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash y, en general, no se puede predecir como se haría con el contenedor de conjuntos, donde se determina mediante la función de ordenación únicamente.

## <a name="insert"></a>  hash_set::insert

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Inserta un elemento o un intervalo de elementos en un `hash_set`.

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor de un elemento que se va a insertar en el `hash_set` a menos que `hash_set` ya contenga ese elemento o, más general, un elemento cuya clave esté ordenada de manera equivalente.|
|*Where*|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (La inserción se puede realizar en tiempo constante amortizado, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a `_Where`).|
|*Primero*|Posición del primer elemento que se va a copiar de un `hash_set`.|
|*Último*|Posición situada más allá del último elemento que se va a copiar de un `hash_set`.|
|*IList*|initializer_list de la que se van a copiar los elementos.|

### <a name="return-value"></a>Valor devuelto

La primera `insert` función miembro devuelve un par cuyo **bool** componente devuelve **true** si hizo una inserción y **false** si el `hash_set` ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación y cuyo componente de iterador devuelve la dirección donde se insertó un nuevo elemento o donde ya se encontraba el elemento.

Para tener acceso al componente de iterador de un par `pr` devuelto por esta función miembro, use `pr.first` y, para desreferenciarlo, use `*(pr.first)`. Para tener acceso a la **bool** componente de un par `pr` devuelto por esta función miembro, utilice `pr.second`y para desreferenciarla, use `*(pr.second)`.

La segunda función miembro `insert` devuelve un iterador que apunta a la posición donde se insertó el nuevo elemento en el `hash_set`.

### <a name="remarks"></a>Comentarios

La tercera función miembro inserta los elementos en una initializer_list.

La tercera función miembro inserta la secuencia de valores de elemento en un objeto `hash_set` correspondiente a cada elemento direccionado por un iterador en el intervalo [ `First`, `Last`) de un objeto `hash_set` especificado.

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `iterator` puede usarse para modificar el valor de un elemento.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar `iterator`.

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Recupera una copia del objeto traits hash usado para aplicar un algoritmo hash y ordenar valores de claves de elementos en un objeto hash_set.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que usa un objeto hash_set para ordenar sus elementos, que es el parámetro de plantilla *rasgos*.

Para obtener más información sobre *rasgos* vea el [hash_set (clase)](../standard-library/hash-set-class.md) tema.

### <a name="remarks"></a>Comentarios

El objeto almacenado define la función miembro:

**bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);

que devuelve **True** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que [key_compare](#key_compare) y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla *Traits*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos en el objeto hash_set.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Comentarios

`key_compare` es un sinónimo del parámetro de plantilla *rasgos*.

Para obtener más información sobre *rasgos* vea el [hash_set (clase)](../standard-library/hash-set-class.md) tema.

Tenga en cuenta que `key_compare` y [value_compare](#value_compare) son sinónimos para el parámetro de plantilla *Traits*. Ambos tipos se proporcionan para las clases set y multiset, donde son idénticos, para la compatibilidad con las clases map and multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que describe un objeto almacenado como un elemento de un objeto hash_set en su capacidad como criterio de ordenación.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

`key_type` es un sinónimo del parámetro de plantilla *clave*.

Para obtener más información sobre *clave*, vea la sección Comentarios de la [hash_set (clase)](../standard-library/hash-set-class.md) tema.

Tenga en cuenta que `key_type` y [value_type](#value_type) son sinónimos para el parámetro de plantilla *Key*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador al primer elemento de un objeto hash_set cuyo valor de clave es igual o mayor que el de una clave especificada.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_set que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un `iterator` o `const_iterator` que se dirige la ubicación de un elemento de un objeto hash_set que tiene una clave que es igual o mayor que la clave de argumento o que direcciona la ubicación siguiente al último elemento del objeto hash_set si no coinciden con se encuentra para la clave.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve la longitud máxima del objeto hash_set.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud máxima posible del objeto hash_set.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_set::operator=

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Reemplaza los elementos del objeto hash_set por una copia de otro objeto hash_set.

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*right*|Objeto [hash_set](../standard-library/hash-set-class.md) que se copia en el objeto `hash_set`.|

### <a name="remarks"></a>Comentarios

Después de borrar todos los elementos existentes en un `hash_set`, `operator=` copia o mueve el contenido de *derecho* en el `hash_set`.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="pointer"></a>  hash_set::pointer

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un puntero a un elemento de un objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `pointer` puede usarse para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto hash_set.

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador que direcciona el primer elemento en un objeto hash_set invertido.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona el primer elemento de un objeto hash_set invertido o lo que fue el último elemento del objeto hash_set sin invertir.

### <a name="remarks"></a>Comentarios

`rbegin` se usa con un hash_set invertido igual que [begin](#begin) se usa con un hash_set.

Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, el objeto hash_set no puede modificarse. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, el objeto hash_set puede modificarse.

`rbegin` puede usarse para iterar un objeto hash_set hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // throught a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a>  hash_set::reference

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona una referencia a un elemento almacenado en un objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador que direcciona la ubicación que sigue al último elemento en un objeto hash_set invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona la ubicación siguiente al último elemento de un objeto hash_set invertido (la ubicación que había precedido al primer elemento del objeto hash_set sin invertir).

### <a name="remarks"></a>Comentarios

`rend` se usa con un hash_set invertido igual que [end](#end) se usa con un objeto hash_set.

Si el valor devuelto de `rend` se asigna a `const_reverse_iterator`, el objeto hash_set no puede modificarse. Si el valor devuelto de `rend` se asigna a `reverse_iterator`, el objeto hash_set puede modificarse. El valor devuelto por `rend` no se debe desreferenciar.

Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_set.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // throught a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un objeto hash_set invertido.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `reverse_iterator` se usa para iterar el objeto hash_set en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="size"></a>  hash_set::size

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve el número de elementos en el objeto hash_set.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud actual del objeto hash_set.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo entero sin signo que puede representar el número de elementos de un objeto hash_set.

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Intercambia los elementos de dos objetos hash_set.

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
Objeto hash_set de argumentos que proporciona los elementos que se van a intercambiar con el objeto hash_set de destino.

### <a name="remarks"></a>Comentarios

La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos objetos hash_set cuyos elementos se intercambian.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Devuelve un iterador al primer elemento de un objeto hash_set con una clave que es mayor que una clave especificada.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_set que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un `iterator` o `const_iterator` que se dirige la ubicación de un elemento de un objeto hash_set que tiene una clave que es igual o mayor que la clave de argumento o que direcciona la ubicación siguiente al último elemento del objeto hash_set si no coinciden con se encuentra para la clave.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Recupera una copia del objeto de comparación usado para ordenar valores de elemento de un objeto hash_set.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que usa un objeto hash_set para ordenar sus elementos, que es el parámetro de plantilla *comparar*.

Para obtener más información sobre *comparar*, vea la sección Comentarios de la [hash_set (clase)](../standard-library/hash-set-class.md) tema.

### <a name="remarks"></a>Comentarios

El objeto almacenado define la función miembro:

**bool operator**( **const Key&** _ *xVal*, **const Key&** \_ `yVal`);

que devuelve **True** si `_xVal` precede y no es igual a `_yVal` en el criterio de ordenación.

Tenga en cuenta que ambos [value_compare](../standard-library/set-class.md#value_compare) y [key_compare](../standard-library/set-class.md#key_compare) son sinónimos para el parámetro de plantilla *comparar*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que proporciona dos objetos de función: un predicado binario de la clase compare que puede comparar dos valores de elementos de un objeto hash_set para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Comentarios

`value_compare` es un sinónimo del parámetro de plantilla *rasgos*.

Para obtener más información sobre *rasgos* vea el [hash_set (clase)](../standard-library/hash-set-class.md) tema.

Tenga en cuenta que ambos [key_compare](#key_compare) y `value_compare` son sinónimos para el parámetro de plantilla *rasgos*. Ambos tipos se proporcionan para las clases hash_set y hash_multiset, donde son idénticos, para la compatibilidad con las clases hash_map y hash_multimap, donde son distintos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_comp](#value_comp) para ver cómo se declara y usa `value_compare`.

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Tipo que describe un objeto almacenado como un elemento de un objeto hash_set en su capacidad como un valor.

```cpp
typedef Key value_type;
```

### <a name="example"></a>Ejemplo

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
