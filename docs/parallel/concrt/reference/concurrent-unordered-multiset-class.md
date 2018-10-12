---
title: concurrent_unordered_multiset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::unsafe_erase
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_multiset class
ms.assetid: 219d7d67-1ff0-45f4-9400-e9cc272991a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3283707f53da37acc98a9d1645b8bb10f2114f77
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163366"
---
# <a name="concurrentunorderedmultiset-class"></a>concurrent_unordered_multiset (Clase)

La `concurrent_unordered_multiset` clase es un contenedor seguro para simultaneidad que controla una secuencia de longitud variable de elementos de tipo K. La secuencia se representa en una forma que permita segura para simultaneidad anexar, acceso de elemento, acceso de iterador y las operaciones de recorrido de iterador.

## <a name="syntax"></a>Sintaxis

```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_multiset : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    true>>;
```

#### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de clave.

*_Hasher*<br/>
El tipo de objeto de la función hash. Este argumento es opcional y el valor predeterminado es `std::hash<K>`.

*key_equality*<br/>
El tipo de objeto de función de comparación de igualdad. Este argumento es opcional y el valor predeterminado es `std::equal_to<K>`.

*_Allocator_type*<br/>
El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `std::allocator<K>`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`allocator_type`|El tipo de un asignador para administrar el almacenamiento.|
|`const_iterator`|El tipo de un iterador constante para la secuencia controlada.|
|`const_local_iterator`|El tipo de un iterador de depósito constante para la secuencia controlada.|
|`const_pointer`|El tipo de un puntero constante a un elemento.|
|`const_reference`|El tipo de una referencia constante a un elemento.|
|`difference_type`|El tipo de una distancia con signo entre dos elementos.|
|`hasher`|El tipo de la función hash.|
|`iterator`|El tipo de un iterador para la secuencia controlada.|
|`key_equal`|El tipo de la función de comparación.|
|`key_type`|El tipo de una clave de ordenación.|
|`local_iterator`|El tipo de un iterador de depósito para la secuencia controlada.|
|`pointer`|El tipo de un puntero a un elemento.|
|`reference`|El tipo de una referencia a un elemento.|
|`size_type`|El tipo de una distancia sin signo entre dos elementos.|
|`value_type`|El tipo de un elemento.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[concurrent_unordered_multiset](#ctor)|Sobrecargado. Construye un conjunto múltiple desordenado simultáneo.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[hash_function](#hash_function)|Devuelve el objeto almacenado de la función hash.|
|[insert](#insert)|Sobrecargado. Agrega elementos al objeto `concurrent_unordered_multiset`.|
|[key_eq](#key_eq)|El objeto de función de comparación de igualdad almacenado.|
|[swap](#swap)|Intercambia el contenido de dos objetos `concurrent_unordered_multiset`. Este método no es seguro para la simultaneidad.|
|[unsafe_erase](#unsafe_erase)|Sobrecargado. Quita los elementos de `concurrent_unordered_multiset` en las posiciones especificadas. Este método no es seguro para la simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_unordered_multiset` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Comentarios

Para obtener información detallada sobre la `concurrent_unordered_multiset` de clases, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_multiset`

## <a name="requirements"></a>Requisitos

**Encabezado:** concurrent_unordered_set.h

**Espacio de nombres:** simultaneidad

##  <a name="begin"></a> comenzar

Devuelve un iterador que apunta al primer elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador al primer elemento en el contenedor simultáneo.

##  <a name="cbegin"></a> cbegin

Devuelve un iterador constante que apunta al primer elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador constante al primer elemento en el contenedor simultáneo.

##  <a name="cend"></a> cend

Devuelve un iterador constante que apunta a la ubicación que sigue al último elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador const en la ubicación que sigue al último elemento en el contenedor simultáneo.

##  <a name="clear"></a> Borrar

Borra todos los elementos en el contenedor simultáneo. Esta función no es seguro para simultaneidad.

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_multiset)

Construye un conjunto múltiple desordenado simultáneo.

```
explicit concurrent_unordered_multiset(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multiset(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_multiset(
    concurrent_unordered_multiset&& _Uset);
```

### <a name="parameters"></a>Parámetros

*_Iterator*<br/>
El tipo de iterador de entrada.

*_Number_of_buckets*<br/>
El número inicial de depósitos para este conjunto múltiple desordenado.

*_Hasher*<br/>
La función hash para este conjunto múltiple desordenado.

*key_equality*<br/>
La función de comparación de igualdad para este conjunto múltiple desordenado.

*_Allocator*<br/>
El asignador para este conjunto múltiple desordenado.

*first*<br/>
*Último*<br/>
*_Uset*<br/>
El origen `concurrent_unordered_multiset` mover los elementos de objeto.

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto de asignador `_Allocator` e inicializar el conjunto múltiple desordenado.

El primer constructor especifica un conjunto múltiple inicial vacío y especifica explícitamente el número de depósitos, tipo de función hash, función de igualdad y el asignador para usarse.

El segundo constructor especifica un asignador para el conjunto múltiple desordenado.

El tercer constructor especifica los valores proporcionados por el rango de iterador [ `_Begin`, `_End`).

Los constructores cuarto y quinto especifican una copia del conjunto múltiple desordenado simultáneo `_Uset`.

El último constructor especifica un movimiento del conjunto múltiple desordenado simultáneo `_Uset`.

##  <a name="count"></a> recuento

Cuenta el número de elementos que coinciden con una clave especificada. Esta función es seguro para simultaneidad.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parámetros

*KVal*<br/>
Clave que se va a buscar.

### <a name="return-value"></a>Valor devuelto

El número de veces el número de veces que la clave aparece en el contenedor.

##  <a name="empty"></a> vacío

Comprueba si no hay ningún elemento presente. Este método es seguro para simultaneidad.

```
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si está vacío, el contenedor simultáneo **false** en caso contrario.

### <a name="remarks"></a>Comentarios

En presencia de inserciones simultáneas, o si no está vacío el contenedor simultáneo puede cambiar inmediatamente después de llamar a esta función, antes de que incluso se lee el valor devuelto.

##  <a name="end"></a> final

Devuelve un iterador que apunta a la ubicación que sigue al último elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador a la ubicación que sigue al último elemento en el contenedor simultáneo.

##  <a name="equal_range"></a> equal_range

Busca un intervalo que coincide con una clave especificada. Esta función es seguro para simultaneidad.

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parámetros

*KVal*<br/>
El valor de clave que se buscará.

### <a name="return-value"></a>Valor devuelto

Un [par](../../../standard-library/pair-structure.md) donde el primer elemento es un iterador al principio y el segundo elemento es un iterador al final del intervalo.

### <a name="remarks"></a>Comentarios

Es posible que las inserciones simultáneas hacer que claves adicionales para insertarse después el iterador inicial y antes el iterador de fin.

##  <a name="find"></a> Buscar

Busca un elemento que coincide con una clave especificada. Esta función es seguro para simultaneidad.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parámetros

*KVal*<br/>
El valor de clave que se buscará.

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta a la ubicación del primer elemento que coincide con la clave proporcionada, o el iterador `end()` si no existe ese elemento.

##  <a name="get_allocator"></a> get_allocator

Devuelve el objeto de asignador almacenado para este contenedor simultáneo. Este método es seguro para simultaneidad.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto de asignador almacenado para este contenedor simultáneo.

##  <a name="hash_function"></a> hash_function

Devuelve el objeto almacenado de la función hash.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto de función hash almacenado.

##  <a name="insert"></a> Insertar

Agrega elementos al objeto `concurrent_unordered_multiset`.

```
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parámetros

*_Iterator*<br/>
El tipo de iterador que se utiliza para la inserción.

*V*<br/>
El tipo del valor insertado.

*valor*<br/>
El valor que se va a insertar.

*_WHERE*<br/>
La ubicación inicial para buscar un punto de inserción.

*first*<br/>
El principio del intervalo que se va a insertar.

*Último*<br/>
Final del intervalo que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta a la ubicación de inserción.

### <a name="remarks"></a>Comentarios

La primera función miembro inserta el elemento `value` en la secuencia controlada, a continuación, devuelve el iterador que designa el elemento insertado.

La segunda función miembro devuelve insert ( `value`), con `_Where` como punto de partida dentro de la secuencia controlada que se busca el punto de inserción.

La tercera función miembro inserta la secuencia de valores de elemento del intervalo [ `first`, `last`).

Las dos últimas funciones miembro comportan igual que las dos primeras, salvo que `value` se utiliza para construir el valor insertado.

##  <a name="key_eq"></a> key_eq

El objeto de función de comparación de igualdad almacenado.

```
key_equal key_eq() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto de función de comparación de igualdad almacenado.

##  <a name="load_factor"></a> load_factor

Calcula y devuelve el factor de carga actual del contenedor. El factor de carga es el número de elementos del contenedor dividido por el número de depósitos.

```
float load_factor() const;
```

### <a name="return-value"></a>Valor devuelto

El factor de carga para el contenedor.

##  <a name="max_load_factor"></a> max_load_factor

Obtiene o establece el factor de carga máximo del contenedor. El factor de carga máxima es el número máximo de elementos que pueden estar en un cubo antes de que el contenedor aumenta su tabla interna.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parámetros

`_Newmax`

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve el factor de carga máxima almacenado. La segunda función miembro no devuelve un valor, pero se produce un [out_of_range](../../../standard-library/out-of-range-class.md) excepción si el factor de carga especificado no es válido..

##  <a name="max_size"></a> max_size

Devuelve el tamaño máximo del contenedor simultáneo, determinado por el asignador. Este método es seguro para simultaneidad.

```
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de elementos que se pueden insertar en este contenedor simultáneo.

### <a name="remarks"></a>Comentarios

Este valor de límite superior realmente puede ser superior a lo que realmente puede contener el contenedor.

##  <a name="operator_eq"></a> operator=

Asigna el contenido de otro objeto `concurrent_unordered_multiset` a este. Este método no es seguro para la simultaneidad.

```
concurrent_unordered_multiset& operator= (const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset& operator= (concurrent_unordered_multiset&& _Uset);
```

### <a name="parameters"></a>Parámetros

*_Uset*<br/>
Objeto `concurrent_unordered_multiset` de origen.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `concurrent_unordered_multiset` objeto.

### <a name="remarks"></a>Comentarios

Después de borrar todos los elementos existentes en un conjunto múltiple desordenado simultáneo `operator=` copia o mueve el contenido de `_Uset` en simultáneos desordenados multiset.

##  <a name="rehash"></a> rehash)

Recompila la tabla hash.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parámetros

*_Buckets*<br/>
El número deseado de cubos.

### <a name="remarks"></a>Comentarios

La función miembro modifica el número de depósitos para que sea al menos `_Buckets` y vuelve a generar la tabla hash según sea necesario. El número de depósitos debe ser una potencia de 2. Si no es una potencia de 2, se redondea a la siguiente mayor potencia de 2.

Produce un [out_of_range](../../../standard-library/out-of-range-class.md) excepción si el número de depósitos no es válido (0 o mayor que el número máximo de depósitos).

##  <a name="size"></a> Tamaño

Devuelve el número de elementos de este contenedor simultáneo. Este método es seguro para simultaneidad.

```
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el contenedor.

### <a name="remarks"></a>Comentarios

En presencia de inserciones simultáneas, puede cambiar el número de elementos en el contenedor simultáneo inmediatamente después de llamar a esta función, antes de que incluso se lee el valor devuelto.

##  <a name="swap"></a> intercambio

Intercambia el contenido de dos objetos `concurrent_unordered_multiset`. Este método no es seguro para la simultaneidad.

```
void swap(concurrent_unordered_multiset& _Uset);
```

### <a name="parameters"></a>Parámetros

*_Uset*<br/>
La `concurrent_unordered_multiset` objeto que se va a intercambiar.

##  <a name="unsafe_begin"></a> unsafe_begin

Devuelve un iterador al primer elemento de este contenedor para un depósito concreto.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parámetros

*_Bucket*<br/>
El índice de depósito.

### <a name="return-value"></a>Valor devuelto

Un iterador que señala al principio del depósito.

##  <a name="unsafe_bucket"></a> unsafe_bucket

Devuelve el índice de depósito que asigna una clave específica en este contenedor.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parámetros

*KVal*<br/>
La clave de elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

El índice de depósito para la clave en este contenedor.

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

Devuelve el número actual de depósitos en este contenedor.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Valor devuelto

El número actual de depósitos en este contenedor.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

Devuelve el número de elementos de un depósito concreto de este contenedor.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parámetros

*_Bucket*<br/>
El depósito que se buscará.

### <a name="return-value"></a>Valor devuelto

El número actual de depósitos en este contenedor.

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

Devuelve un iterador al primer elemento de este contenedor para un depósito concreto.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parámetros

*_Bucket*<br/>
El índice de depósito.

### <a name="return-value"></a>Valor devuelto

Un iterador que señala al principio del depósito.

##  <a name="unsafe_cend"></a> unsafe_cend

Devuelve un iterador a la ubicación que sigue al último elemento de un depósito concreto.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parámetros

*_Bucket*<br/>
El índice de depósito.

### <a name="return-value"></a>Valor devuelto

Un iterador que señala al principio del depósito.

##  <a name="unsafe_end"></a> unsafe_end

Devuelve un iterador al último elemento de este contenedor para un depósito concreto.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parámetros

*_Bucket*<br/>
El índice de depósito.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al final del depósito.

##  <a name="unsafe_erase"></a> unsafe_erase

Quita los elementos de `concurrent_unordered_multiset` en las posiciones especificadas. Este método no es seguro para la simultaneidad.

```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>Parámetros

*_WHERE*<br/>
La posición del iterador en la que borrar.

*first*<br/>
*Último*<br/>
*KVal*<br/>
Valor de clave que se va a borrar.

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [final](#end)() si no existe ese elemento. La tercera función miembro devuelve el número de elementos que se quitan.

### <a name="remarks"></a>Comentarios

La primera función miembro quita el elemento al que apunta `_Where`. La segunda función miembro quita los elementos en el intervalo [ `_Begin`, `_End`).

La tercera función miembro quita los elementos del intervalo delimitado por [equal_range](#equal_range)(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

Devuelve el número máximo de depósitos en este contenedor.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de depósitos en este contenedor.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)

