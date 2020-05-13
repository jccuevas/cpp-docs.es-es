---
title: Platform::Collections::Map (Clase)
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
ms.openlocfilehash: ff27f6c543a2326dd4318f66aae51b89092b28e2
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032452"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map (Clase)

Representa una *asignación*, que es una colección de pares clave-valor. Implementa [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) para ayudar con el enlace de [datos](/windows/uwp/data-binding/data-binding-in-depth)XAML.

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

*Ⅴ*<br/>
Tipo del valor del par clave-valor.

*C*<br/>
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map. De forma predeterminada, [std::less\<K>](../standard-library/less-struct.md).

*__is_valid_winrt_type()* Función generada por el compilador que valida el tipo de *K* y *V* y proporciona un mensaje de error descriptivo si el tipo no se puede almacenar en el mapa.

### <a name="remarks"></a>Observaciones

Los tipos permitidos son:

- enteros

- clase de interfaz ?

- clase ref pública^

- value struct

- clase de enumeración pública

El objeto Map es básicamente un contenedor de [std::map](../standard-library/map-class.md). Es una implementación concreta de C++ de los tipos [Windows::Foundation::Collections::IMap<\<Windows::Foundation::Collections::IKeyValuePair K,V>>](/uwp/api/windows.foundation.collections.imap-2) e [IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) que se pasan a través de interfaces públicas de Windows Runtime. Si intentas usar un tipo `Platform::Collections::Map` en un valor devuelto o un parámetro público, se produce el error del compilador C3986. Puede corregir el error cambiando el tipo del parámetro o valor devuelto a [Windows::Foundation::Collections::IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).

Para obtener más información, consulte [Colecciones](../cppcx/collections-c-cx.md).

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Mapa::Mapa](#ctor)|Inicializa una nueva instancia de la clase Map.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Mapa::Borrar](#clear)|Quita todos los pares clave-valor del objeto Map actual.|
|[Mapa::Primero](#first)|Devuelve un iterador que especifica el primer elemento del objeto Map.|
|[Mapa::GetView](#getview)|Devuelve una vista de solo lectura del objeto Map actual; es decir, [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Mapa::HasKey](#haskey)|Determina si el objeto Map actual contiene la clave especificada.|
|[Mapa::Insertar](#insert)|Agrega el par clave-valor especificado al objeto Map actual.|
|[Mapa::Búsqueda](#lookup)|Recupera el elemento en la clave especificada del objeto Map actual.|
|[Map::Remove](#remove)|Elimina el par clave-valor especificado del objeto Map actual.|
|[Mapa::Tamaño](#size)|Devuelve el número de elementos del objeto Map actual.|

### <a name="events"></a>Events

|||
|-|-|
|Nombre|Descripción|
|[Evento Map::MapChanged](#mapchanged)|Se produce cuando cambia la asignación.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Map`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>Mapa::Método Clear

Quita todos los pares clave-valor del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Mapa::Primer método

Devuelve un iterador que especifica el primer elemento del mapa o `nullptr` si el mapa está vacío.

### <a name="syntax"></a>Sintaxis

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Valor devuelto

Un iterador que especifica el primer elemento del mapa.

### <a name="remarks"></a>Observaciones

Una forma cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con la palabra clave de deducción de tipo **automático.** Por ejemplo: `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Map::GetView Método

Devuelve una vista de solo lectura del mapa actual; es decir, un [Platform::Collections::MapView (clase)](../cppcx/platform-collections-mapview-class.md), que implementa la interfaz [de>Windows::Foundation::Collections::IMapView\<K,V.](/uwp/api/windows.foundation.collections.imapview-2)

### <a name="syntax"></a>Sintaxis

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Valor devuelto

Objeto `MapView` .

## <a name="maphaskey-method"></a><a name="haskey"></a>Map::HasKey Método

Determina si el objeto Map actual contiene la clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave que se usa para ubicar el elemento Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

**true** si se encuentra la clave; de lo contrario, **false**.

## <a name="mapinsert-method"></a><a name="insert"></a>Map::Insert Método

Agrega el par clave-valor especificado al objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

*value*<br/>
La parte de valor del par clave-valor. El tipo de *valor* es typename *V*.

### <a name="return-value"></a>Valor devuelto

**true** si la clave de un elemento existente en la clave Map actual coincide con la *clave* y la parte del valor de ese elemento se establece en *value*. **false** si ningún elemento existente en el mapa actual coincide con la *clave* y los parámetros de *clave* y *valor* se convierten en un par clave-valor y, a continuación, se agregan al mapa actual.

## <a name="maplookup-method"></a><a name="lookup"></a>Map::Método de búsqueda

Recupera el valor de tipo V asociado a la clave especificada de tipo K, si la clave existe.

### <a name="syntax"></a>Sintaxis

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave utilizada para buscar un elemento en el objeto Map. El tipo de *clave* es typename *K*.

### <a name="return-value"></a>Valor devuelto

El valor que se empareja con la *clave*. El tipo del valor devuelto es typename *V*.

### <a name="remarks"></a>Observaciones

Si la clave no existe, se produce una [excepción Platform::OutOfBoundsException.](../cppcx/platform-outofboundsexception-class.md)

## <a name="mapmap-constructor"></a><a name="ctor"></a>Mapa::Constructor de mapas

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

*Init*<br/>
typename del objeto Map actual.

*Comp*<br/>
Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map.

*M*<br/>
Una referencia o valor `map Class` [r](../cpp/lvalues-and-rvalues-visual-cpp.md) a que se utiliza para inicializar el mapa actual.

*first*<br/>
El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto Map actual.

*last*<br/>
El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto Map actual.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Evento Map::MapChanged

Se produce cuando un elemento se inserta en el mapa o se quita del mapa.

### <a name="syntax"></a>Sintaxis

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un [MapChangedEventHandler\<K,V>](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) que contiene información sobre el objeto que generó el evento y el tipo de cambio que se produjo. Vea también [IMapChangedEventArgs\<K>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) y [CollectionChange (enumeración).](/uwp/api/windows.foundation.collections.collectionchange)

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Las aplicaciones de Windows en tiempo de\<ejecución que usan\<el proyecto iMap K,V de Visual Basic de C o Visual Basic> como IDictionary K,V>.

## <a name="mapremove-method"></a><a name="remove"></a>Mapa::Eliminar método

Elimina el par clave-valor especificado del objeto Map actual.

### <a name="syntax"></a>Sintaxis

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La parte de clave del par clave-valor. El tipo de *clave* es typename *K*.

## <a name="mapsize-method"></a><a name="size"></a>Mapa::Método de tamaño

Devuelve el número de [elementos windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) en el mapa.

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
