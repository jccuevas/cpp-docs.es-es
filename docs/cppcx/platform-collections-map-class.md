---
title: Platform::Collections::Map (Clase)
ms.date: 01/18/2018
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
ms.openlocfilehash: c6edd8cdd089e24011df41db09f3c1bb5d6465f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481463"
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

*K*<br/>
Tipo de la clave del par clave-valor.

*V*<br/>
Tipo del valor del par clave-valor.

*C*<br/>
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std:: less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type()* una función generado por el compilador que valida el tipo de *K* y *V* y proporciona un mensaje de error descriptivo si el tipo no puede almacenarse en el mapa.

### <a name="remarks"></a>Comentarios

Los tipos permitidos son:

- enteros

- clase de interfaz ^

- clase ref pública^

- value struct

- clase de enumeración pública

El objeto Map es básicamente un contenedor de [std::map](../standard-library/map-class.md). Es una implementación concreta de C++ de la [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) y [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) tipos que se pasan a través de las interfaces de Windows en tiempo de ejecución. Si intentas usar un tipo `Platform::Collections::Map` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error cambiando el tipo del valor devuelto o parámetro a [Windows::Foundation::Collections::IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

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
|[GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[Map:: Insert](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[Map:: Lookup](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|
|[Map](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
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

## <a name="first"></a>  Map (método)

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

## <a name="getview"></a>  GetView (método)

Devuelve una vista de solo lectura del objeto Map actual; es decir, un [mapview (clase)](../cppcx/platform-collections-mapview-class.md), que implementa la [Windows::Foundation::Collections::IMapView\<K, V >] / uwp/api/Windows.Foundation.Collections.IMapView_K_V_) interfaz.

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Un objeto `MapView`.

## <a name="haskey"></a>  Haskey (método)

Determina si el objeto Map actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave que se usa para ubicar el elemento Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

**True** si la clave se encuentra; en caso contrario, **false**.

## <a name="insert"></a>  Map:: Insert (método)

Agrega el par clave-valor especificado al objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

*valor*<br/>
La parte de valor del par clave-valor. El tipo de *valor* es typename *V*.

### <a name="return-value"></a>Valor devuelto

**True** si la clave de un elemento existente en el mapa actual coincide con *clave* y la parte del valor de ese elemento se establece en *valor*. **false** si ningún elemento existente en el mapa actual coincide con *clave* y *clave* y *valor* parámetros se crean en un par de clave-valor y, a continuación, se agregan a la objeto Map actual.

## <a name="lookup"></a>  Map:: Lookup (método)

Recupera el valor de tipo V asociado a la clave especificada de tipo K, si la clave existe.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave utilizada para buscar un elemento en el objeto Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con el *clave*. El tipo del valor devuelto es typename *V*.

### <a name="remarks"></a>Comentarios

Si la clave no existe, entonces un [outofboundsexception](../cppcx/platform-outofboundsexception-class.md) se produce.

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

*InIt*<br/>
typename del objeto Map actual.

*Comp.*<br/>
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map.

*m*<br/>
Una referencia o [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a un `map Class` que se utiliza para inicializar el objeto Map actual.

*first*<br/>
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto Map actual.

*Último*<br/>
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto Map actual.

## <a name="mapchanged"></a>  Mapchanged (evento)

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) que contiene información sobre el objeto que provocó el evento y el tipo de cambio producido. Vea también [IMapChangedEventArgs\<K >](https://msdn.microsoft.com/library/windows/apps/br226034.aspx) y [CollectionChange (enumeración)](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Las aplicaciones de Windows en tiempo de ejecución que usan C# o Visual Basic del proyecto IMap\<K, V > como IDictionary\<K, V >.

## <a name="remove"></a>  Map (método)

Elimina el par clave-valor especificado del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

## <a name="size"></a>  Map:: Size (método)

Devuelve el número de [Windows::Foundation::Collections::IKeyValuePair\<K, V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementos del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del objeto Map.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
