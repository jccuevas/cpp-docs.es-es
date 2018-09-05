---
title: concurrent_unordered_map (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6fddd90eaa6259cd2552dddbeafb405d90580ac
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684357"
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map (Clase)
La clase `concurrent_unordered_map` es un contenedor seguro para simultaneidad que controla una secuencia de variación de longitud de elementos del tipo `std::pair<const K, _Element_type>`. La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de clave.  
  
 `_Element_type`  
 El tipo asignado.  
  
 `_Hasher`  
 El tipo de objeto de la función hash. Este argumento es opcional y el valor predeterminado es `std::hash<K>`.  
  
 `key_equality`  
 El tipo de objeto de función de comparación de igualdad. Este argumento es opcional y el valor predeterminado es `std::equal_to<K>`.  
  
 `_Allocator_type`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria para el mapa no ordenado simultáneo. Este argumento es opcional y el valor predeterminado es `std::allocator<std::pair<K`, `_Element_type>>`.  
  
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
|[operator[]](#operator_at)|Sobrecargado. Busca o inserta un elemento con la clave especificada. Este método es seguro para simultaneidad.|  
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_unordered_map` a este. Este método no es seguro para la simultaneidad.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información detallada sobre la `concurrent_unordered_map` de clases, vea [contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concurrent_unordered_map.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="at"></a> en el 

 Busca un elemento en `concurrent_unordered_map` con un valor de clave especificado. Este método es seguro para simultaneidad.  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 Valor de clave que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al valor de datos del elemento encontrado.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de clave de argumento no se encuentra, la función produce un objeto de clase `out_of_range`.  
  
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
  
##  <a name="ctor"></a> concurrent_unordered_map) 

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
  
### <a name="parameters"></a>Parámetros  
 `_Iterator`  
 El tipo de iterador de entrada.  
  
 `_Number_of_buckets`  
 El número inicial de depósitos para esta asignación no ordenada.  
  
 `_Hasher`  
 La función hash para esta asignación no ordenada.  
  
 `key_equality`  
 La función de comparación de igualdad para esta asignación no ordenada.  
  
 `_Allocator`  
 El asignador para esta asignación no ordenada.  
  
 `_Begin`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar.  
  
 `_End`  
 Posición del primer elemento más allá del intervalo de elementos que se va a copiar.  
  
 `_Umap`  
 El objeto de origen `concurrent_unordered_map` del que copiar o mover elementos.  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un objeto de asignador `_Allocator` e inicializar el objeto unorderedmap.  
  
 El primer constructor especifica un mapa inicial vacío y especifica explícitamente el número de depósitos, tipo de función hash, función de igualdad y el asignador para usarse.  
  
 El segundo constructor especifica un asignador para el mapa no ordenado.  
  
 El tercer constructor especifica los valores proporcionados por el rango de iterador [ `_Begin`, `_End`).  
  
 Los constructores cuarto y quinto especifican una copia del mapa no ordenado simultáneo `_Umap`.  
  
 El último constructor especifica un movimiento del mapa no ordenado simultáneo `_Umap`.  
  
##  <a name="count"></a> recuento 

 Cuenta el número de elementos que coinciden con una clave especificada. Esta función es seguro para simultaneidad.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 Clave que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de veces el número de veces que la clave aparece en el contenedor.  
  
##  <a name="empty"></a> vacío 

 Comprueba si no hay ningún elemento presente. Este método es seguro para simultaneidad.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si está vacío, el contenedor simultáneo `false` en caso contrario.  
  
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
 `KVal`  
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
 `KVal`  
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

 Obtiene el objeto de función hash almacenado.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de función hash almacenado.  
  
##  <a name="insert"></a> Insertar 

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
  
### <a name="parameters"></a>Parámetros  
 `_Iterator`  
 El tipo de iterador que se utiliza para la inserción.  
  
 `V`  
 El tipo del valor insertado en el mapa.  
  
 `value`  
 El valor que se va a insertar.  
  
 `_Where`  
 La ubicación inicial para buscar un punto de inserción.  
  
 `first`  
 El principio del intervalo que se va a insertar.  
  
 `last`  
 Final del intervalo que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un par que contiene un iterador y un valor booleano. Vea la sección Comentarios para obtener más detalles.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro determina si existe un elemento X en la secuencia cuyo criterio de ordenación es equivalente a de `value`. Si no, crea ese elemento X y la inicializa con `value`. La función, a continuación, determina el iterador `where` que designa X. Si se ha producido una inserción, la función devuelve `std::pair(where, true)`. De lo contrario, devuelve `std::pair(where, false)`.  
  
 La segunda función miembro devuelve insert ( `value`), con `_Where` como punto de partida dentro de la secuencia controlada que se busca el punto de inserción.  
  
 La tercera función miembro inserta la secuencia de valores de elemento del intervalo [ `first`, `last`).  
  
 Las dos últimas funciones miembro comportan igual que las dos primeras, salvo que `value` se utiliza para construir el valor insertado.  
  
##  <a name="key_eq"></a> key_eq 

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
  
##  <a name="operator_at"></a> operator] 

 Busca o inserta un elemento con la clave especificada. Este método es seguro para simultaneidad.  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 El valor de clave para  
  
 Buscar o insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al valor de datos del elemento insertado o se encuentra.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de clave de argumento no se encuentra, se inserta junto con el valor predeterminado del tipo de datos.  
  
 `operator[]` puede utilizarse para insertar elementos en un mapa `m` mediante `m[key] = DataValue;`, donde `DataValue` es el valor de la `mapped_type` del elemento con un valor de clave de `key`.  
  
 Cuando se emplea `operator[]` para insertar elementos, la referencia devuelta no indica si una inserción cambia un elemento ya existente o crea uno nuevo. Las funciones miembro `find` y [insertar](#insert) puede usarse para determinar si un elemento con una clave especificada ya está presente antes de una inserción.  
  
##  <a name="operator_eq"></a> operator= 

 Asigna el contenido de otro objeto `concurrent_unordered_map` a este. Este método no es seguro para la simultaneidad.  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Umap`  
 Objeto `concurrent_unordered_map` de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `concurrent_unordered_map` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar todos los elementos existentes en un vector simultáneo, `operator=` copia o mueve el contenido de `_Umap` en el vector simultáneo.  
  
##  <a name="rehash"></a> rehash) 

 Recompila la tabla hash.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Buckets`  
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

 Intercambia el contenido de dos objetos `concurrent_unordered_map`. Este método no es seguro para la simultaneidad.  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Umap`  
 La `concurrent_unordered_map` objeto que se va a intercambiar.  
  
##  <a name="unsafe_begin"></a> unsafe_begin 

 Devuelve un iterador al primer elemento de este contenedor para un depósito concreto.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que señala al principio del depósito.  
  
##  <a name="unsafe_bucket"></a> unsafe_bucket 

 Devuelve el índice de depósito que asigna una clave específica en este contenedor.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
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
 `_Bucket`  
 El depósito que se buscará.  
  
### <a name="return-value"></a>Valor devuelto  
 El número actual de depósitos en este contenedor.  
  
##  <a name="unsafe_cbegin"></a> unsafe_cbegin 

 Devuelve un iterador al primer elemento de este contenedor para un depósito concreto.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que señala al principio del depósito.  
  
##  <a name="unsafe_cend"></a> unsafe_cend 

 Devuelve un iterador a la ubicación que sigue al último elemento de un depósito concreto.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
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
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador que apunta al final del depósito.  
  
##  <a name="unsafe_erase"></a> unsafe_erase 

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
  
### <a name="parameters"></a>Parámetros  
 `_Where`  
 La posición del iterador en la que borrar.  
  
 `_Begin`  
 La posición del primer elemento del intervalo de elementos que va a borrar.  
  
 `_End`  
 La posición del primer elemento más allá del intervalo de elementos que va a borrar.  
  
 `KVal`  
 Valor de clave que se va a borrar.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `concurrent_unordered_map::end`() si no existe ese elemento. La tercera función miembro devuelve el número de elementos que se quitan.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada señalada por `_Where`. La segunda función miembro quita los elementos en el intervalo [ `_Begin`, `_End`).  
  
 La tercera función miembro quita los elementos del intervalo delimitado por `concurrent_unordered_map::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count 

 Devuelve el número máximo de depósitos en este contenedor.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de depósitos en este contenedor.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)



