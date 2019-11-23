---
title: Platform::Collections::Map Class
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 81721d719a424250beed89f4a5656b3f2fc27922
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816307"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map Class

Representa una *asignación*, que es una colección de pares clave-valor. Implementa [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap_k_v_) para ayudar con el [enlace de datos](/windows/uwp/data-binding/data-binding-in-depth)XAML.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parámetros

*K*<br/>
El tipo de la clave del par de clave-valor.

*V*<br/>
El tipo del valor del par de clave-valor.

*C*<br/>
Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar el orden relativo en el mapa. De forma predeterminada, [STD:: less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Función generada por el compilador que valida el tipo de *K* y *V* y proporciona un mensaje de error descriptivo si el tipo no se puede almacenar en la asignación.

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

- números enteros

- clase de interfaz ^

- clase ref pública ^

- struct de valor

- clase Enum pública

El objeto Map es básicamente un contenedor de [std::map](../standard-library/map-class.md). Se trata de C++ una implementación concreta de los tipos [Windows:: Foundation:: Collections:: IMap < Windows:: Foundation:: Collections:: IKeyValuePair\<K, V > >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) y [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) que se pasan a través de interfaces Windows Runtime públicas. Si intentas usar un tipo `Platform::Collections::Map` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error cambiando el tipo del parámetro o el valor devuelto a [Windows:: Foundation:: Collections:: IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Para obtener más información, vea [colecciones](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Map::Map](#ctor)|Inicializa una nueva instancia de la clase Map.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Map::Clear](#clear)|Quita todos los pares clave-valor del objeto Map actual.|
|[Map::First](#first)|Devuelve un iterador que especifica el primer elemento del mapa.|
|[Map::GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[Map:: Insert](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[Map:: Lookup](#lookup)|Recupera el elemento en la clave especificada en el objeto Map actual.|
|[Map::Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
|[Map::Size](#size)|Devuelve el número de elementos del objeto Map actual.|

### <a name="events"></a>Eventos

|||
|-|-|
|Name|Descripción|
|[Map:: MapChanged](#mapchanged) (evento)|Ocurre cuando el objeto Map cambia.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Map`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="clear"></a>Map:: CLEAR (método)

Quita todos los pares clave-valor del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="first"></a>Map:: First (método)

Devuelve un iterador que especifica el primer elemento del mapa o `nullptr` si el mapa está vacío.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del mapa.

### <a name="remarks"></a>Comentarios

Una manera cómoda de contener el iterador devuelto por First () es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **auto** . Por ejemplo: `auto x = myMap->First();`.

## <a name="getview"></a>Map:: GetView ((método)

Devuelve una vista de solo lectura del mapa actual; es decir, una [clase Platform:: Collections:: MapView](../cppcx/platform-collections-mapview-class.md), que implementa la interfaz [Windows:: Foundation:: Collections:: IMapView\<K, V >]/UWP/API/Windows.Foundation.Collections. IMapView_K_V_).

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Objeto `MapView`.

## <a name="haskey"></a>Map:: Haskey ((método)

Determina si el objeto Map actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave que se usa para ubicar el elemento Map. El tipo de *clave* es TypeName *K*.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra la clave; en caso contrario, **false**.

## <a name="insert"></a>Map:: Insert (método)

Agrega el par clave-valor especificado al objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es TypeName *K*.

*valor*<br/>
La parte de valor del par clave-valor. El tipo de *valor* es TypeName *V*.

### <a name="return-value"></a>Valor devuelto

**true** si la clave de un elemento existente en la asignación actual coincide con la *clave* y la parte del valor de ese elemento se establece en *Value*. **false** si ningún elemento existente en la asignación actual coincide con la *clave* y los parámetros de *clave* y *valor* se convierten en un par clave-valor y se agregan a la asignación actual.

## <a name="lookup"></a>Map:: Lookup (método)

Recupera el valor de tipo V asociado a la clave especificada de tipo K, si la clave existe.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave utilizada para buscar un elemento en el objeto Map. El tipo de *clave* es TypeName *K*.

### <a name="return-value"></a>Valor devuelto

Valor que se empareja con la *clave*. El tipo del valor devuelto es TypeName *V*.

### <a name="remarks"></a>Comentarios

Si la clave no existe, se produce una excepción [Platform:: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) .

## <a name="ctor"></a>Map:: Map (constructor)

Inicializa una nueva instancia de la clase Map.

### <a name="syntax"></a>Sintaxis

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Parámetros

*InIt*<br/>
typename del objeto Map actual.

*comp*<br/>
Un tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar el orden relativo en el mapa.

*m*<br/>
Referencia o valor [r](../cpp/lvalues-and-rvalues-visual-cpp.md) a un `map Class` que se usa para inicializar la asignación actual.

*first*<br/>
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto Map actual.

*last*<br/>
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto Map actual.

## <a name="mapchanged"></a>Map:: MapChanged (evento)

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

[MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) que contiene información sobre el objeto que ha generado el evento y el tipo de cambio que se ha producido. Vea también [IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) y la [enumeración CollectionChange](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Windows Runtime las aplicaciones que C# usan o Visual Basic el proyecto IMap\<k, v > como IDictionary\<k, v >.

## <a name="remove"></a>Map:: Remove (método)

Elimina el par clave-valor especificado del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es TypeName *K*.

## <a name="size"></a>Map:: Size (método)

Devuelve el número de elementos [Windows:: Foundation:: Collections:: IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) en el mapa.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del objeto Map.

## <a name="see-also"></a>Vea también

[Colecciones (C++/CX)](collections-c-cx.md)<br/>
[Espacio de nombres de plataforma](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
