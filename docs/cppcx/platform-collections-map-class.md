---
title: Clase Platform::Collections::Map | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6580ccb9ca19a575bac6a9fedbb4e8f16c7060ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map (Clase)

Representa una *asignación*, que es una colección de pares clave-valor.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parámetros

*K*  
 Tipo de la clave del par clave-valor.

*V*  
Tipo del valor del par clave-valor.

*C*  
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type()*  
Una función generados por el compilador que valida el tipo de *K* y *V* y proporciona un mensaje de error descriptivo si el tipo no se puede almacenar en el mapa.

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

- enteros

- clase de interfaz ^

- clase ref pública^

- value struct

- clase de enumeración pública

El objeto Map es básicamente un contenedor de [std::map](../standard-library/map-class.md). Es una implementación concreta de C++ de la [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](http://go.microsoft.com/fwlink/p/?LinkId=262408) y [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) tipos que se pasan a través de las interfaces en tiempo de ejecución de Windows. Si intentas usar un tipo `Platform::Collections::Map` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error cambiando el tipo del valor devuelto o parámetro a [Windows::Foundation::Collections::IMap\<K, V >](http://go.microsoft.com/fwlink/p/?LinkId=262408).

Para obtener más información, consulte [colecciones](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Map](#ctor)|Inicializa una nueva instancia de la clase Map.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Map:: Clear](#clear)|Quita todos los pares clave-valor del objeto Map actual.|
|[Map::First](#first)|Devuelve un iterador que especifica el primer elemento del objeto Map.|
|[Map:: GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[Map:: Insert](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[Map:: Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|
|[Map:: Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
|[Map:: Size](#size)|Devuelve el número de elementos del objeto Map actual.|

### <a name="events"></a>Eventos

|||
|-|-|
|nombre|Descripción|
|[Mapchanged](#mapchanged-event.md) `event`|Se produce cuando cambia la asignación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Map`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="clear"></a>  Map:: Clear (método)

Quita todos los pares clave-valor del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="first"></a>  Map:: First (método)

Devuelve un iterador que especifica el primer elemento del mapa o `nullptr` si el mapa está vacío.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del mapa.

### <a name="remarks"></a>Comentarios

Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myMap->First();`.

## <a name="getview"></a>  Map:: GetView (método)

Devuelve una vista de solo lectura del objeto Map actual; es decir, un [mapview (clase)](../cppcx/platform-collections-mapview-class.md), que implementa el [Windows::Foundation::Collections::IMapView\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) interfaz.

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Un objeto `MapView`.

## <a name="haskey"></a>  Map:: haskey (método)

Determina si el objeto Map actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*  
La clave que se usa para ubicar el elemento Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

`true` si se encuentra la clave; de lo contrario, `false`.

## <a name="insert"></a>  Map:: Insert (método)

Agrega el par clave-valor especificado al objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parámetros

*key*  
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

*valor*  
La parte de valor del par clave-valor. El tipo de *valor* es typename *V*.

### <a name="return-value"></a>Valor devuelto

`true` Si la clave de un elemento del mapa actual coincide con *clave* y la parte del valor de ese elemento se establece en *valor*. `false` Si ningún elemento existente del mapa actual coincide con *clave* y *clave* y *valor* parámetros se crean en un par clave-valor y, a continuación, se agrega al mapa actual.

## <a name="lookup"></a>  Map:: Lookup (método)

Recupera el valor de tipo V asociado a la clave especificada de tipo K, si la clave existe.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*  
La clave utilizada para buscar un elemento en el objeto Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con el *clave*. El tipo del valor devuelto es typename *V*.

### <a name="remarks"></a>Comentarios

Si la clave no existe, un [outofboundsexception](../cppcx/platform-outofboundsexception-class.md) se produce.

## <a name="ctor"></a>  Constructor de Map

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

*InIt*  
typename del objeto Map actual.

*comp*  
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map.

*m*  
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un `map Class` que se usa para inicializar el objeto Map actual.

*first*  
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto Map actual.

*último*  
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto Map actual.

## <a name="mapchanged"></a>  Mapchanged (evento)

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

A [MapChangedEventHandler\<K, V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) que contiene información sobre el objeto que provocó el evento y el tipo de cambio producido. Vea también [IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) y [CollectionChange (enumeración)](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Aplicaciones de Windows en tiempo de ejecución que usan C# o Visual Basic proyecto IMap\<K, V > como IDictionary\<K, V >.

## <a name="remove"></a>  Map:: Remove (método)

Elimina el par clave-valor especificado del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parámetros

*key*  
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

## <a name="size"></a>  Map:: Size (método)

Devuelve el número de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementos en el mapa.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del objeto Map.

## <a name="see-also"></a>Vea también

[Namespace de plataforma](platform-namespace-c-cx.md)  
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
