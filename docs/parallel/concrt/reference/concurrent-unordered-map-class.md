---
title: concurrent_unordered_map (clase)
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: a43e52edfe223dae51737d7d2cde37e3b8238f08
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298693"
---
# <a name="concurrent_unordered_map-class"></a>concurrent_unordered_map (clase)

La clase `concurrent_unordered_map` es un contenedor seguro para simultaneidad que controla una secuencia de variación de longitud de elementos del tipo `std::pair<const K, _Element_type>`. La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado.

## <a name="syntax"></a>Sintaxis

```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

#### <a name="parameters"></a>Parameters

*K*<br/>
El tipo de clave.

*_Element_type*<br/>
El tipo asignado.

*_Hasher*<br/>
El tipo de objeto de la función hash. Este argumento es opcional y el valor predeterminado es `std::hash<K>`.

*key_equality*<br/>
El tipo de objeto de función de comparación de igualdad. Este argumento es opcional y el valor predeterminado es `std::equal_to<K>`.

*_Allocator_type*<br/>
Tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria para el mapa no ordenado simultáneo. Este argumento es opcional y el valor predeterminado es `std::allocator<std::pair<K`, `_Element_type>>`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

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
|`mapped_type`|El tipo de un valor asignado asociado a cada clave.|
|`pointer`|El tipo de un puntero a un elemento.|
|`reference`|El tipo de una referencia a un elemento.|
|`size_type`|El tipo de una distancia sin signo entre dos elementos.|
|`value_type`|El tipo de un elemento.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|Sobrecargado. Construye un mapa no ordenado simultáneo.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[at](#at)|Sobrecargado. Busca un elemento en `concurrent_unordered_map` con un valor de clave especificado. Este método es seguro para simultaneidad.|
|[hash_function](#hash_function)|Obtiene el objeto de función hash almacenado.|
|[insert](#insert)|Sobrecargado. Agrega elementos al objeto `concurrent_unordered_map`.|
|[key_eq](#key_eq)|Obtiene el objeto de función de comparación de igualdad almacenado.|
|[swap](#swap)|Intercambia el contenido de dos objetos `concurrent_unordered_map`. Este método no es seguro para la simultaneidad.|
|[unsafe_erase](#unsafe_erase)|Sobrecargado. Quita los elementos de `concurrent_unordered_map` en las posiciones especificadas. Este método no es seguro para la simultaneidad.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator\[\]](#operator_at)|Sobrecargado. Busca o inserta un elemento con la clave especificada. Este método es seguro para simultaneidad.|
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_unordered_map` a este. Este método no es seguro para la simultaneidad.|

## <a name="remarks"></a>Notas

Para obtener información detallada sobre la clase `concurrent_unordered_map`, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>Requisitos de

**Encabezado:** concurrent_unordered_map. h

**Espacio de nombres:** simultaneidad

##  <a name="at"></a>Veamos

Busca un elemento en `concurrent_unordered_map` con un valor de clave especificado. Este método es seguro para simultaneidad.

```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
Valor de clave que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Una referencia al valor de datos del elemento encontrado.

### <a name="remarks"></a>Notas

Si el valor de clave de argumento no se encuentra, la función produce un objeto de clase `out_of_range`.

##  <a name="begin"></a>inicia

Devuelve un iterador que apunta al primer elemento del contenedor simultáneo. Este método es seguro para simultaneidad.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador al primer elemento del contenedor simultáneo.

##  <a name="cbegin"></a>cbegin (

Devuelve un iterador constante que apunta al primer elemento del contenedor simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador const al primer elemento del contenedor simultáneo.

##  <a name="cend"></a>cend

Devuelve un iterador constante que apunta a la ubicación que sigue al último elemento del contenedor simultáneo. Este método es seguro para simultaneidad.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador const a la ubicación que sigue al último elemento del contenedor simultáneo.

##  <a name="clear"></a>claridad

Borra todos los elementos del contenedor simultáneo. Esta función no es segura para simultaneidad.

```
void clear();
```

##  <a name="ctor"></a>concurrent_unordered_map

Construye un mapa no ordenado simultáneo.

```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parameters

*_Iterator*<br/>
El tipo de iterador de entrada.

*_Number_of_buckets*<br/>
Número inicial de cubos para este mapa desordenado.

*_Hasher*<br/>
Función hash para este mapa no ordenado.

*key_equality*<br/>
Función de comparación de igualdad para este mapa no ordenado.

*_Allocator*<br/>
Asignador de este mapa desordenado.

*_Begin*<br/>
Posición del primer elemento en el intervalo de elementos que se va a copiar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a copiar.

*_Umap*<br/>
El objeto de origen `concurrent_unordered_map` del que copiar o mover elementos.

### <a name="remarks"></a>Notas

Todos los constructores almacenan un objeto de asignador `_Allocator` e inicializan el mapa no ordenado.

El primer constructor especifica un mapa inicial vacío y especifica explícitamente el número de cubos, la función hash, la función de igualdad y el tipo de asignador que se va a usar.

El segundo constructor especifica un asignador para el mapa no ordenado.

El tercer constructor especifica los valores proporcionados por el intervalo de iterador [`_Begin`, `_End`).

Los constructores cuarto y quinto especifican una copia del mapa no ordenado simultáneo `_Umap`.

El último constructor especifica un movimiento del `_Umap`del mapa no ordenado simultáneo.

##  <a name="count"></a>contabiliza

Cuenta el número de elementos que coinciden con una clave especificada. Esta función es segura para simultaneidad.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
Clave que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Número de veces que aparece la clave en el contenedor.

##  <a name="empty"></a>vacía

Comprueba si no hay ningún elemento presente. Este método es seguro para simultaneidad.

```
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el contenedor simultáneo está vacío; de lo contrario, **false** .

### <a name="remarks"></a>Notas

En la presencia de inserciones simultáneas, tanto si el contenedor simultáneo está vacío como si no, puede cambiar inmediatamente después de llamar a esta función, antes de que el valor devuelto sea incluso lectura.

##  <a name="end"></a>extremo

Devuelve un iterador que apunta a la ubicación que sigue al último elemento del contenedor simultáneo. Este método es seguro para simultaneidad.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador a la ubicación que sigue al último elemento del contenedor simultáneo.

##  <a name="equal_range"></a>equal_range

Busca un intervalo que coincide con una clave especificada. Esta función es segura para simultaneidad.

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
Valor de clave en el que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un [par](../../../standard-library/pair-structure.md) donde el primer elemento es un iterador al principio y el segundo elemento es un iterador al final del intervalo.

### <a name="remarks"></a>Notas

Es posible que las inserciones simultáneas hagan que se inserten claves adicionales después del iterador Begin y antes del iterador end.

##  <a name="find"></a>localización

Busca un elemento que coincide con una clave especificada. Esta función es segura para simultaneidad.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
Valor de clave en el que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta a la ubicación del primer elemento que coincide con la clave proporcionada, o al iterador `end()` si no existe ese elemento.

##  <a name="get_allocator"></a> get_allocator

Devuelve el objeto de asignador almacenado para este contenedor simultáneo. Este método es seguro para simultaneidad.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto de asignador almacenado para este contenedor simultáneo.

##  <a name="hash_function"></a>hash_function

Obtiene el objeto de función hash almacenado.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto de función hash almacenado.

##  <a name="insert"></a>introducir

Agrega elementos al objeto `concurrent_unordered_map`.

```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parameters

*_Iterator*<br/>
Tipo de iterador que se usa para la inserción.

*V*<br/>
Tipo del valor insertado en el mapa.

*valor*<br/>
Valor que se va a insertar.

*_Where*<br/>
Ubicación inicial en la que se va a buscar un punto de inserción.

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Un par que contiene un iterador y un valor booleano. Para obtener información más detallada, consulte la sección Comentarios.

### <a name="remarks"></a>Notas

La primera función miembro determina si existe un elemento X en la secuencia cuya clave tiene una ordenación equivalente a la de `value`. En caso contrario, crea este elemento X y lo inicializa con `value`. A continuación, la función determina el iterador `where` que designa X. Si se produjo una inserción, la función devuelve `std::pair(where, true)`. De lo contrario, devuelve `std::pair(where, false)`.

La segunda función miembro devuelve Insert (`value`), usando `_Where` como un lugar de inicio dentro de la secuencia controlada para buscar el punto de inserción.

La tercera función miembro inserta la secuencia de valores de elemento del intervalo [`first`, `last`).

Las dos últimas funciones miembro se comportan igual que las dos primeras, salvo que se usa `value` para construir el valor insertado.

##  <a name="key_eq"></a>key_eq

Obtiene el objeto de función de comparación de igualdad almacenado.

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

Factor de carga del contenedor.

##  <a name="max_load_factor"></a> max_load_factor

Obtiene o establece el factor de carga máximo del contenedor. El factor de carga máximo es el mayor número de elementos que puede estar en cualquier depósito antes de que el contenedor crezca su tabla interna.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parameters

`_Newmax`

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve el factor de carga máxima almacenado. La segunda función miembro no devuelve un valor, sino que produce una excepción [out_of_range](../../../standard-library/out-of-range-class.md) si el factor de carga proporcionado no es válido.

##  <a name="max_size"></a> max_size

Devuelve el tamaño máximo del contenedor simultáneo, determinado por el asignador. Este método es seguro para simultaneidad.

```
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Número máximo de elementos que se pueden insertar en este contenedor simultáneo.

### <a name="remarks"></a>Notas

Este valor de límite superior puede ser realmente mayor de lo que el contenedor puede contener realmente.

##  <a name="operator_at"></a> operator[]

Busca o inserta un elemento con la clave especificada. Este método es seguro para simultaneidad.

```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
El valor de clave para

buscar o insertar.

### <a name="return-value"></a>Valor devuelto

Referencia al valor de datos del elemento encontrado o insertado.

### <a name="remarks"></a>Notas

Si el valor de clave de argumento no se encuentra, se inserta junto con el valor predeterminado del tipo de datos.

`operator[]` se puede usar para insertar elementos en un mapa `m` mediante `m[key] = DataValue;`, donde `DataValue` es el valor del `mapped_type` del elemento con un valor de clave de `key`.

Cuando se emplea `operator[]` para insertar elementos, la referencia devuelta no indica si una inserción cambia un elemento ya existente o crea uno nuevo. Las funciones miembro `find` e [Insert](#insert) se pueden usar para determinar si ya existe un elemento con una clave especificada antes de una inserción.

##  <a name="operator_eq"></a> operator=

Asigna el contenido de otro objeto `concurrent_unordered_map` a este. Este método no es seguro para la simultaneidad.

```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parameters

*_Umap*<br/>
Objeto `concurrent_unordered_map` de origen.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `concurrent_unordered_map`.

### <a name="remarks"></a>Notas

Después de borrar los elementos existentes de un vector simultáneo, `operator=` copia o mueve el contenido de `_Umap` al vector simultáneo.

##  <a name="rehash"></a>rehash (

Recompila la tabla hash.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parameters

*_Buckets*<br/>
El número deseado de cubos.

### <a name="remarks"></a>Notas

La función miembro modifica el número de depósitos para que sea al menos `_Buckets` y vuelve a generar la tabla hash según sea necesario. El número de depósitos debe ser una potencia de 2. Si no es una potencia de 2, se redondeará a la siguiente potencia más grande de 2.

Produce una excepción [out_of_range](../../../standard-library/out-of-range-class.md) si el número de depósitos no es válido (0 o mayor que el número máximo de depósitos).

##  <a name="size"></a>ajusta

Devuelve el número de elementos de este contenedor simultáneo. Este método es seguro para simultaneidad.

```
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del contenedor.

### <a name="remarks"></a>Notas

En la presencia de inserciones simultáneas, el número de elementos del contenedor simultáneo puede cambiar inmediatamente después de llamar a esta función, antes de que el valor devuelto sea incluso lectura.

##  <a name="swap"></a>pasar

Intercambia el contenido de dos objetos `concurrent_unordered_map`. Este método no es seguro para la simultaneidad.

```
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>Parameters

*_Umap*<br/>
`concurrent_unordered_map` objeto con el que se va a intercambiar.

##  <a name="unsafe_begin"></a>unsafe_begin

Devuelve un iterador al primer elemento de este contenedor para un depósito específico.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameters

*_Bucket*<br/>
Índice de cubo.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al principio del cubo.

##  <a name="unsafe_bucket"></a>unsafe_bucket

Devuelve el índice de cubo al que se asigna una clave específica en este contenedor.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameters

*KVal*<br/>
Clave de elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Índice de cubo de la clave de este contenedor.

##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count

Devuelve el número actual de cubos de este contenedor.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Valor devuelto

Número actual de cubos de este contenedor.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

Devuelve el número de elementos de un depósito específico de este contenedor.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parameters

*_Bucket*<br/>
Depósito que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Número actual de cubos de este contenedor.

##  <a name="unsafe_cbegin"></a>unsafe_cbegin

Devuelve un iterador al primer elemento de este contenedor para un depósito específico.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameters

*_Bucket*<br/>
Índice de cubo.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al principio del cubo.

##  <a name="unsafe_cend"></a>unsafe_cend

Devuelve un iterador a la ubicación que sigue al último elemento de un depósito concreto.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameters

*_Bucket*<br/>
Índice de cubo.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al principio del cubo.

##  <a name="unsafe_end"></a>unsafe_end

Devuelve un iterador al último elemento de este contenedor para un depósito específico.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameters

*_Bucket*<br/>
Índice de cubo.

### <a name="return-value"></a>Valor devuelto

Iterador que apunta al final del depósito.

##  <a name="unsafe_erase"></a>unsafe_erase

Quita los elementos de `concurrent_unordered_map` en las posiciones especificadas. Este método no es seguro para la simultaneidad.

```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>Parameters

*_Where*<br/>
La posición del iterador en la que borrar.

*_Begin*<br/>
Posición del primer elemento del intervalo de elementos que se va a borrar.

*_End*<br/>
Posición del primer elemento más allá del intervalo de elementos que se va a borrar.

*KVal*<br/>
Valor de clave que se va a borrar.

### <a name="return-value"></a>Valor devuelto

Las dos primeras funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `concurrent_unordered_map::end`() si no existe ese elemento. La tercera función miembro devuelve el número de elementos que se quitan.

### <a name="remarks"></a>Notas

La primera función miembro quita el elemento de la secuencia controlada a la que apunta `_Where`. La segunda función miembro quita los elementos del intervalo [`_Begin`, `_End`).

La tercera función miembro quita los elementos del intervalo delimitados por `concurrent_unordered_map::equal_range`(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

Devuelve el número máximo de depósitos de este contenedor.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Valor devuelto

Número máximo de depósitos de este contenedor.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)
