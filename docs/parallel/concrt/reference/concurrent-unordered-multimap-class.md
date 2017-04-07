---
title: concurrent_unordered_multimap (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::unsafe_erase
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_multimap class
ms.assetid: 4dada5d7-15df-4382-b9c9-348e75b2f3c1
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 1efbaf805cef529eb444fc1e496fc5e60c715130
ms.lasthandoff: 03/17/2017

---
# <a name="concurrentunorderedmultimap-class"></a>concurrent_unordered_multimap (Clase)
La clase `concurrent_unordered_multimap` es un contenedor seguro para simultaneidad que controla una secuencia de elementos de longitud variable del tipo `std::pair<const K, _Element_type>`. La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.  
  
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
    _Element_type>>> class concurrent_unordered_multimap : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
 details::_Hash_compare<K,
    _Hasher,
 key_equality>,
    _Allocator_type,
 true>>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de clave.  
  
 `_Element_type`  
 El tipo asignado.  
  
 `_Hasher`  
 El tipo de objeto de la función hash. Este argumento es opcional y el valor predeterminado es `std::hash<``K``>`.  
  
 `key_equality`  
 El tipo de objeto de función de comparación de igualdad. Este argumento es opcional y el valor predeterminado es `std::equal_to<``K``>`.  
  
 `_Allocator_type`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para el vector simultáneo. Este argumento es opcional y el valor predeterminado es `std::allocator<std::pair<``K`, `_Element_type``>>`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[concurrent_unordered_multimap)](#ctor)|Sobrecargado. Construye un mapa múltiple desordenado simultáneo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[hash_function](#hash_function)|Devuelve el objeto almacenado de la función hash.|  
|[insert](#insert)|Sobrecargado. Agrega elementos al objeto `concurrent_unordered_multimap`.|  
|[key_eq](#key_eq)|Devuelve el objeto de función de comparación de igualdad almacenado.|  
|[swap](#swap)|Intercambia el contenido de dos objetos `concurrent_unordered_multimap`. Este método no es seguro para la simultaneidad.|  
|[unsafe_erase](#unsafe_erase)|Sobrecargado. Quita los elementos de `concurrent_unordered_multimap` en las posiciones especificadas. Este método no es seguro para la simultaneidad.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Sobrecargado. Asigna el contenido de otro objeto `concurrent_unordered_multimap` a este. Este método no es seguro para la simultaneidad.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener información detallada sobre la `concurrent_unordered_multimap` de clases, consulte [objetos y contenedores paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_multimap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concurrent_unordered_map.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="begin"></a>comenzar 

 Devuelve un iterador que apunta al primer elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador al primer elemento en el contenedor simultáneo.  
  
##  <a name="cbegin"></a>cbegin 

 Devuelve un iterador constante que apunta al primer elemento en el contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador const en el primer elemento en el contenedor simultáneo.  
  
##  <a name="cend"></a>cend 

 Devuelve un iterador constante que apunta a la ubicación que sigue al último elemento del contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador const en la ubicación que sigue al último elemento del contenedor simultáneo.  
  
##  <a name="clear"></a>Borrar 

 Borra todos los elementos en el contenedor simultáneo. Esta función no es seguro para simultaneidad.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_unordered_multimap) 

 Construye un mapa múltiple desordenado simultáneo.  
  
```
explicit concurrent_unordered_multimap(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multimap(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_multimap(
    concurrent_unordered_multimap&& _Umap);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Iterator`  
 El tipo de iterador de entrada.  
  
 `_Number_of_buckets`  
 El número inicial de depósitos para este mapa múltiple desordenado.  
  
 `_Hasher`  
 La función hash para este mapa múltiple desordenado.  
  
 `key_equality`  
 La función de comparación de igualdad para este mapa múltiple desordenado.  
  
 `_Allocator`  
 El asignador para este mapa múltiple desordenado.  
  
 `_Begin`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar.  
  
 `_End`  
 Posición del primer elemento más allá del intervalo de elementos que se va a copiar.  
  
 `_Umap`  
 El origen de `concurrent_unordered_multimap` objeto que se va a copiar los elementos.  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un objeto de asignador `_Allocator` e inicializar el mapa múltiple desordenado.  
  
 El primer constructor especifica un multimap inicial vacío y especifica explícitamente el número de depósitos, escriba función hash, función de igualdad y el asignador para usarse.  
  
 El segundo constructor especifica un asignador para el mapa múltiple desordenado.  
  
 El tercer constructor especifica los valores proporcionados por el intervalo de iterador [ `_Begin`, `_End`).  
  
 Los constructores cuarto y quinto especifican una copia del mapa de múltiple desordenado simultáneo `_Umap`.  
  
 El último constructor especifica un movimiento del mapa múltiple desordenado simultáneo `_Umap`.  
  
##  <a name="count"></a>recuento 

 Cuenta el número de elementos que coinciden con una clave especificada. Esta función es seguro para simultaneidad.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 Clave que se va a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de veces el número de veces que la clave aparece en el contenedor.  
  
##  <a name="empty"></a>vacía 

 Comprueba si no hay ningún elemento presente. Este método es seguro para simultaneidad.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si está vacío, el contenedor simultáneo `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 En presencia de inserciones simultáneas, o no está vacío el contenedor simultáneo puede cambiar inmediatamente después de llamar a esta función, antes incluso de leer el valor devuelto.  
  
##  <a name="end"></a>final 

 Devuelve un iterador que apunta a la ubicación siguiente al último elemento del contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador a la ubicación siguiente al último elemento del contenedor simultáneo.  
  
##  <a name="equal_range"></a>equal_range 

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
 El valor de clave para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [par](http://msdn.microsoft.com/en-us/32e72d66-3020-4cb9-92c3-f7a5fa7998ff) donde el primer elemento es un iterador al principio y el segundo elemento es un iterador al final del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 Es posible que las inserciones simultáneas provocar que se inserten después el iterador inicial y antes el iterador de fin de claves adicionales.  
  
##  <a name="find"></a>Buscar 

 Busca un elemento que coincide con una clave especificada. Esta función es seguro para simultaneidad.  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 El valor de clave para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta a la ubicación del primer elemento que coincide con la clave especificada o el iterador `end()` si no existe ese elemento.  
  
##  <a name="get_allocator"></a>get_allocator 

 Devuelve el objeto de asignador almacenado para este contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de asignador almacenado para este contenedor simultáneo.  
  
##  <a name="hash_function"></a>hash_function 

 Devuelve el objeto almacenado de la función hash.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de función hash almacenado.  
  
##  <a name="insert"></a>Insertar 

 Agrega elementos al objeto `concurrent_unordered_multimap`.  
  
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
 El final del intervalo que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta a la ubicación de inserción.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro inserta el elemento `value` en la secuencia controlada, a continuación, devuelve el iterador que designa el elemento insertado.  
  
 La segunda función miembro devuelve insert ( `value`), con `_Where` como punto de partida dentro de la secuencia controlada para buscar el punto de inserción.  
  
 La tercera función miembro inserta la secuencia de valores de elemento del intervalo [ `first`, `last`).  
  
 Las dos últimas funciones miembro comportan igual que las dos primeras, salvo que `value` se utiliza para construir el valor insertado.  
  
##  <a name="key_eq"></a>key_eq 

 Devuelve el objeto de función de comparación de igualdad almacenado.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de función de comparación de igualdad almacenado.  
  
##  <a name="load_factor"></a>load_factor 

 Calcula y devuelve el factor de carga actual del contenedor. El factor de carga es el número de elementos en el contenedor dividido por el número de depósitos.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El factor de carga para el contenedor.  
  
##  <a name="max_load_factor"></a>max_load_factor 

 Obtiene o establece el factor de carga máxima del contenedor. El factor de carga máxima es el número máximo de elementos que pueden estar en cualquier depósito antes de que el contenedor aumenta su tabla interna.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Newmax`  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función miembro devuelve el factor de carga máxima almacenado. La segunda función miembro no devuelve un valor, pero produce una [out_of_range](../../../standard-library/out-of-range-class.md) excepción si el factor de carga proporcionada no es válido...  
  
##  <a name="max_size"></a>max_size 

 Devuelve el tamaño máximo del contenedor simultáneo, determinado por el asignador. Este método es seguro para simultaneidad.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de elementos que se pueden insertar en este contenedor simultáneo.  
  
### <a name="remarks"></a>Comentarios  
 Este valor de límite superior realmente puede ser superior a lo que realmente puede contener el contenedor.  
  
##  <a name="operator_eq"></a>operador = 

 Asigna el contenido de otro objeto `concurrent_unordered_multimap` a este. Este método no es seguro para la simultaneidad.  
  
```
concurrent_unordered_multimap& operator= (const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap& operator= (concurrent_unordered_multimap&& _Umap);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Umap`  
 Objeto `concurrent_unordered_multimap` de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `concurrent_unordered_multimap` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar todos los elementos existentes en un mapa múltiple desordenado simultáneo `operator=` copia o mueve el contenido de `_Umap` en el mapa múltiple desordenado simultáneo.  
  
##  <a name="rehash"></a>rehash) 

 Recompila la tabla hash.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Buckets`  
 El número deseado de depósitos.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro modifica el número de depósitos para que sea al menos `_Buckets` y vuelve a generar la tabla hash según sea necesario. El número de depósitos debe ser una potencia de 2. Si no es una potencia de 2, se redondea a la siguiente mayor potencia de 2.  
  
 Se produce un [out_of_range](../../../standard-library/out-of-range-class.md) excepción si el número de depósitos no es válido (0 o mayor que el número máximo de depósitos).  
  
##  <a name="size"></a>tamaño 

 Devuelve el número de elementos de este contenedor simultáneo. Este método es seguro para simultaneidad.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el contenedor.  
  
### <a name="remarks"></a>Comentarios  
 En presencia de inserciones simultáneas, puede cambiar el número de elementos en el contenedor simultáneo inmediatamente después de llamar a esta función, antes incluso de leer el valor devuelto.  
  
##  <a name="swap"></a>intercambio 

 Intercambia el contenido de dos objetos `concurrent_unordered_multimap`. Este método no es seguro para la simultaneidad.  
  
```
void swap(concurrent_unordered_multimap& _Umap);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Umap`  
 La `concurrent_unordered_multimap` objeto intercambiar con.  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 Devuelve un iterador al primer elemento en este contenedor para un depósito concreto.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que señala al principio del depósito.  
  
##  <a name="unsafe_bucket"></a>unsafe_bucket 

 Devuelve el índice de depósitos que se asigna una clave específica en este contenedor.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `KVal`  
 La clave del elemento que se está buscada.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de depósito para la clave en este contenedor.  
  
##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count 

 Devuelve el número actual de depósitos en este contenedor.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número actual de depósitos en este contenedor.  
  
##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size 

 Devuelve el número de elementos de un depósito concreto de este contenedor.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El depósito para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número actual de depósitos en este contenedor.  
  
##  <a name="unsafe_cbegin"></a>unsafe_cbegin 

 Devuelve un iterador al primer elemento en este contenedor para un depósito concreto.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que señala al principio del depósito.  
  
##  <a name="unsafe_cend"></a>unsafe_cend 

 Devuelve un iterador a la ubicación siguiente al último elemento de un depósito concreto.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que señala al principio del depósito.  
  
##  <a name="unsafe_end"></a>unsafe_end 

 Devuelve un iterador al último elemento en este contenedor para un depósito concreto.  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Bucket`  
 El índice de depósito.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta al final del depósito.  
  
##  <a name="unsafe_erase"></a>unsafe_erase 

 Quita los elementos de `concurrent_unordered_multimap` en las posiciones especificadas. Este método no es seguro para la simultaneidad.  
  
```
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Where`  
 La posición del iterador en la que borrar.  
  
 `KVal`  
 Valor de clave que se va a borrar.  
  
 `first`  
 `last`  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `concurrent_unordered_multimap::end`() si no existe ese elemento. La tercera función miembro devuelve el número de elementos que se quitan.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada señalada por `_Where`. La segunda función miembro quita los elementos en el intervalo [ `_Begin`, `_End`).  
  
 La tercera función miembro quita los elementos del intervalo delimitado por `concurrent_unordered_multimap::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count 

 Devuelve el número máximo de depósitos en este contenedor.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de depósitos en este contenedor.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)




