---
title: Unorderedmap (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d86e5e36c7219a79b77d79fe02e6b2ae811ccabc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612723"
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

*K*  
Tipo de la clave del par clave-valor.

*V*  
Tipo del valor del par clave-valor.

*C*  
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std:: equal_to\<K >](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

- enteros

- clase de interfaz ^

- clase ref pública^

- value struct

- clase de enumeración pública

**UnorderedMap** es básicamente un contenedor de [std:: unordered_map](../standard-library/unordered-map-class.md) que admite el almacenamiento de tipos en tiempo de ejecución de Windows. Es la implementación concreta de la [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) y [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) tipos que se pasan a través de interfaces de Windows en tiempo de ejecución. Si intentas usar un tipo `Platform::Collections::UnorderedMap` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error cambiando el tipo del valor devuelto o parámetro a [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Para obtener más información, consulte [colecciones](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Unorderedmap](#ctor)|Inicializa una nueva instancia de la clase Map.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Unorderedmap](#clear)|Quita todos los pares clave-valor del objeto Map actual.|
|[UnorderedMap::First](#first)|Devuelve un iterador que especifica el primer elemento del objeto Map.|
|[GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, una clase Platform::Collections::UnorderedMapView.|
|[UnorderedMap::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[UnorderedMap::Insert](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[UnorderedMap::Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|
|[UnorderedMap::Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
|[UnorderedMap::Size](#size)|Devuelve el número de elementos del objeto Map actual.|

### <a name="events"></a>Eventos

|||
|-|-|
|nombre|Descripción|
|[Mapchanged](#mapchanged) eventos|Se produce cuando cambia la asignación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`UnorderedMap`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="clear"></a>  Método unorderedmap:: Clear

Quita todos los pares clave-valor del objeto UnorderedMap actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="first"></a>  Método unorderedmap:: First

Devuelve un iterador que especifica el primer [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elemento del mapa no ordenado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ 
   First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del mapa.

### <a name="remarks"></a>Comentarios

Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myUnorderedMap->First();`.

## <a name="getview"></a>  GetView (método)

Devuelve una vista de solo lectura de UnorderedMap actual; es decir, un [unorderedmapview (clase)](../cppcx/platform-collections-unorderedmapview-class.md) que implementa la [interfaz Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_).

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Un objeto `UnorderedMapView`.

## <a name="haskey"></a>  Haskey (método)

Determina si el objeto UnorderedMap actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parámetros

*key*  
Clave usada para buscar el elemento UnorderedMap. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

`true` si se encuentra la clave; de lo contrario, `false`.

## <a name="insert"></a>  UnorderedMap::Insert Method

Agrega el par clave-valor especificado al objeto UnorderedMap actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parámetros

*key*  
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

*valor*  
La parte de valor del par clave-valor. El tipo de *valor* es typename *V*.

### <a name="return-value"></a>Valor devuelto

`true` Si la clave de un elemento existente en el mapa actual coincide con *clave* y la parte del valor de ese elemento se establece en *valor*. `false` Si ningún elemento existente en el mapa actual coincide con *clave* y *clave* y *valor* parámetros se crean en un par de clave-valor y, a continuación, se agrega al objeto UnorderedMap actual.

## <a name="lookup"></a>  Método unorderedmap:: Lookup

Recupera el valor de tipo V asociado a la clave especificada de tipo K.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parámetros

*key*  
Clave usada para buscar un elemento en el objeto UnorderedMap. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con el *clave*. El tipo del valor devuelto es typename *V*.

## <a name="mapchanged"></a>  Unorderedmap:: Mapchanged

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) que contiene información sobre el objeto que provocó el evento y el tipo de cambio producido. Vea también [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) y [CollectionChange (enumeración)](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Las aplicaciones de Windows en tiempo de ejecución que C# o Visual Basic del proyecto IMap\<K, V > como IDictionary\<K, V >.

## <a name="remove"></a>  Método unorderedmap:: Remove

Elimina el par clave-valor especificado del objeto UnorderedMap.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parámetros

*key*  
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

## <a name="size"></a>  Método unorderedmap:: Size

Devuelve el número de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementos de UnorderedMap.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del objeto UnorderedMap.

## <a name="ctor"></a>  UnorderedMap::UnorderedMap (Constructor)

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

*InIt*  
El typename del objeto UnorderedMap actual.

*P*  
Un objeto de función que puede comparar dos claves para determinar si son iguales. Este parámetro tiene como valor predeterminado [std:: equal_to\<K >](../standard-library/equal-to-struct.md).

*H*  
Un objeto de función que genera un valor hash para una clave. Este parámetro tiene como valor predeterminado [hash de la clase 1](../standard-library/hash-class.md) para los tipos de clave que admite la clase.

*m*  
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un [std:: unordered_map](../standard-library/unordered-map-class.md) que se usa para inicializar el objeto UnorderedMap actual.

*IL* A [std:: initializer_list](../standard-library/initializer-list-class.md) de [std:: Pair](../standard-library/pair-structure.md) objetos que se usa para inicializar el objeto map.

*first*  
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.

*Último*  
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)  
[Platform::Collections (Espacio de nombres)](../cppcx/platform-collections-namespace.md)  
[clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)  
[Platform::Collections::UnorderedMapView (Clase)](../cppcx/platform-collections-unorderedmapview-class.md)  
[Colecciones](../cppcx/collections-c-cx.md)  
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
