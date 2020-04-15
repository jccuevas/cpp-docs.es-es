---
title: Platform::Collections::UnorderedMap (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354423"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap (Clase)

Representa un *mapa*no ordenado, que es una colección de pares clave-valor.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Parámetros

*K*<br/>
Tipo de la clave del par clave-valor.

*Ⅴ*<br/>
Tipo del valor del par clave-valor.

*C*<br/>
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std::equal_to\<K>](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Observaciones

Los tipos permitidos son:

- enteros

- clase de interfaz ?

- clase ref pública^

- value struct

- clase de enumeración pública

**UnorderedMap** es básicamente un contenedor para [std::unordered_map](../standard-library/unordered-map-class.md) que admite el almacenamiento de tipos de Windows Runtime. Es la implementación concreta de los tipos [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) e [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) que se pasan a través de interfaces públicas de Windows Runtime. Si intentas usar un tipo `Platform::Collections::UnorderedMap` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puedes corregir el error si cambias el tipo del parámetro o el valor devuelto a [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Para obtener más información, consulte [Colecciones](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Inicializa una nueva instancia de la clase Map.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|Quita todos los pares clave-valor del objeto Map actual.|
|[UnorderedMap::First](#first)|Devuelve un iterador que especifica el primer elemento del objeto Map.|
|[UnorderedMap::GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, una clase Platform::Collections::UnorderedMapView.|
|[UnorderedMap::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[UnorderedMap::Insertar](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[UnorderedMap::Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|
|[UnorderedMap::Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
|[UnorderedMap::Tamaño](#size)|Devuelve el número de elementos del objeto Map actual.|

### <a name="events"></a>Events

|||
|-|-|
|Nombre|Descripción|
|[Evento Map::MapChanged](#mapchanged)|Se produce cuando cambia la asignación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`UnorderedMap`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap::Clear Método

Quita todos los pares clave-valor del objeto UnorderedMap actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap::Primer método

Devuelve un iterador que especifica el primer elemento [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) en el mapa desordenado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del mapa.

### <a name="remarks"></a>Observaciones

Una forma cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo, `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap::GetView Método

Devuelve una vista de solo lectura del UnorderedMap actual; es decir, una [clase Platform::Collections::UnorderedMapView](../cppcx/platform-collections-unorderedmapview-class.md) que implementa la interfaz [Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Objeto `UnorderedMapView`.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap::HasKey Método

Determina si el objeto UnorderedMap actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave usada para buscar el elemento UnorderedMap. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra la clave; de lo contrario, **false**.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap::Insert Método

Agrega el par clave-valor especificado al objeto UnorderedMap actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

*value*<br/>
La parte de valor del par clave-valor. El tipo de *valor* es typename *V*.

### <a name="return-value"></a>Valor devuelto

**true** si la clave de un elemento existente en la clave Map actual coincide con la *clave* y la parte del valor de ese elemento se establece en *value*. **false** si ningún elemento existente en el mapa actual *coincide* con clave y los parámetros *de clave* y *valor* se convierten en un par clave-valor y, a continuación, se agregan al UnorderedMap actual.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap::Método de búsqueda

Recupera el valor de tipo V asociado a la clave especificada de tipo K.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave usada para buscar un elemento en el objeto UnorderedMap. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con la *clave*. El tipo del valor devuelto es typename *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UnorderedMap::MapChanged

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un [MapChangedEventHandler\<K,V>](/uwp/api/windows.foundation.collections.mapchangedeventhandler) que contiene información sobre el objeto que generó el evento y el tipo de cambio que se produjo. Vea también [IMapChangedEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) y [CollectionChange (enumeración).](/uwp/api/windows.foundation.collections.collectionchange)

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Aplicaciones de Windows en tiempo de ejecución\<que nos c\<o Visual Basic proyecto IMap K,V> como IDictionary K,V>.

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap::Remove Método

Elimina el par clave-valor especificado del objeto UnorderedMap.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap::Método size

Devuelve el número de [elementos Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) en UnorderedMap.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto UnorderedMap.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap::UnorderedMap Constructor

Inicializa una nueva instancia de la clase UnorderedMap.

### <a name="syntax"></a>Sintaxis

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Parámetros

*Init*<br/>
El typename del objeto UnorderedMap actual.

*P*<br/>
Un objeto de función que puede comparar dos claves para determinar si son iguales. El valor predeterminado de este parámetro es [std::equal_to\<K>](../standard-library/equal-to-struct.md).

*H*<br/>
Un objeto de función que genera un valor hash para una clave. Este parámetro tiene como valor predeterminado [hash Clase 1](../standard-library/hash-class.md) para los tipos de clave que admite la clase.

*M*<br/>
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [std::unordered_map](../standard-library/unordered-map-class.md) que se utiliza para inicializar el Actual UnorderedMap.

*Il*<br/>
Un [std::initializer_list](../standard-library/initializer-list-class.md) de [std::pair](../standard-library/pair-structure.md) objetos que se utiliza para inicializar el mapa.

*Primero*<br/>
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.

*Última*<br/>
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Platform::Collections (Espacio de nombres)](../cppcx/platform-collections-namespace.md)<br/>
[clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView (Clase)](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Colecciones](../cppcx/collections-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
