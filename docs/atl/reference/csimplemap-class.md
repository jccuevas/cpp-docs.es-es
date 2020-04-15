---
title: Clase CSimpleMap
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: b8650f36ac3d190207870616754dcd596cb7cc45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330806"
---
# <a name="csimplemap-class"></a>Clase CSimpleMap

Esta clase proporciona compatibilidad con una matriz de asignación simple.

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parámetros

*TKey*<br/>
El tipo de elemento clave.

*TVal*<br/>
El tipo de elemento value.

*TEqual*<br/>
Un objeto de rasgo, que define la `T`prueba de igualdad para elementos de tipo .

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Typedef para el tipo de valor.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Typedef para el tipo de clave.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|El constructor.|
|[CSimpleMap::-CSimpleMap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleMap::Add](#add)|Agrega una clave y un valor asociado a la matriz de mapas.|
|[CSimpleMap::FindKey](#findkey)|Busca una clave específica.|
|[CSimpleMap::FindVal](#findval)|Busca un valor específico.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Recupera la clave especificada.|
|[CSimpleMap::GetSize](#getsize)|Devuelve el número de entradas de la matriz de asignación.|
|[CSimpleMap::GetValueAt](#getvalueat)|Recupera el valor especificado.|
|[CSimpleMap::Lookup](#lookup)|Devuelve el valor asociado a la clave dada.|
|[CSimpleMap::Remove](#remove)|Quita una clave y un valor coincidente.|
|[CSimpleMap::RemoveAll](#removeall)|Elimina todas las claves y valores.|
|[CSimpleMap::RemoveAt](#removeat)|Quita una clave específica y un valor coincidente.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Devuelve la clave asociada al valor especificado.|
|[CSimpleMap::SetAt](#setat)|Establece el valor asociado a la clave dada.|
|[CSimpleMap::SetAtIndex](#setatindex)|Establece la clave y el valor específicos.|

## <a name="remarks"></a>Observaciones

`CSimpleMap`proporciona compatibilidad con una matriz de `T`asignación simple de cualquier tipo determinado, administrando una matriz desordenada de elementos clave y sus valores asociados.

El `TEqual` parámetro proporciona un medio para definir una función de igualdad para dos elementos de tipo `T`. Al crear una clase similar a [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), es posible modificar el comportamiento de la prueba de igualdad para cualquier matriz determinada. Por ejemplo, cuando se trata de una matriz de punteros, puede ser útil definir la igualdad como en función de los valores a los que hacen referencia los punteros. La implementación por defecto utiliza **operator (operator)**.

Tanto `CSimpleMap` [CSimpleArray como CSimpleArray](../../atl/reference/csimplearray-class.md) se proporcionan por compatibilidad con versiones ATL anteriores, y [CAtlArray](../../atl/reference/catlarray-class.md) y [CAtlMap](../../atl/reference/catlmap-class.md)proporcionan implementaciones de colección más completas y eficientes.

A diferencia de otras colecciones de mapas en ATL y MFC, esta clase se implementa con una matriz simple y las búsquedas de búsqueda requieren una búsqueda lineal. `CAtlMap`debe utilizarse cuando la matriz contiene un gran número de elementos.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>CSimpleMap::Add

Agrega una clave y un valor asociado a la matriz de mapas.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave.

*Val*<br/>
El valor asociado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la clave y el valor se agregaron correctamente, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Cada clave y par de valores agregadohace que la memoria de la matriz de asignación se libere y reasigna, con el fin de asegurarse de que los datos de cada uno siempre se almacenan de forma contigua. Es decir, el segundo elemento clave siempre sigue directamente el primer elemento clave en la memoria y así sucesivamente.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType

Una typedef para el tipo de clave.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType

Una typedef para el tipo de valor.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap

El constructor.

```
CSimpleMap();
```

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap::-CSimpleMap

Destructor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey

Busca una clave específica.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice de la clave si se encuentra, de lo contrario devuelve -1.

## <a name="csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal

Busca un valor específico.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
Valor que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del valor si se encuentra, de lo contrario devuelve -1.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt

Recupera la clave en el índice especificado.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de la clave que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve la clave a la que hace referencia *nIndex*.

### <a name="remarks"></a>Observaciones

El índice pasado por *nIndex* debe ser válido para que el valor devuelto sea significativo.

## <a name="csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize

Devuelve el número de entradas de la matriz de asignación.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de entradas (una clave y un valor es una entrada) en la matriz de asignación.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt

Recupera el valor en el índice específico.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del valor que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor al que hace referencia *nIndex*.

### <a name="remarks"></a>Observaciones

El índice pasado por *nIndex* debe ser válido para que el valor devuelto sea significativo.

## <a name="csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup

Devuelve el valor asociado a la clave dada.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor asociado. Si no se encuentra ninguna clave coincidente, se devuelve NULL.

## <a name="csimplemapremove"></a><a name="remove"></a>CSimpleMap::Remove

Quita una clave y un valor coincidente.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la clave y el valor coincidente se quitaron correctamente, FALSE en caso contrario.

## <a name="csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll

Elimina todas las claves y valores.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Quita todas las claves y valores del objeto de matriz de asignación.

## <a name="csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt

Quita una clave y un valor asociado en el índice especificado.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de la clave y el valor asociado que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE si el índice especificado es un índice no válido.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup

Devuelve la clave asociada al valor especificado.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
Valor.

### <a name="return-value"></a>Valor devuelto

Devuelve la clave asociada. Si no se encuentra ninguna clave coincidente, se devuelve NULL.

## <a name="csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt

Establece el valor asociado a la clave dada.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave.

*Val*<br/>
El nuevo valor que se va a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se encontró la clave y el valor se cambió correctamente, FALSE en caso contrario.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex

Establece la clave y el valor en un índice especificado.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice, haciendo referencia al emparejamiento de clave y valor que se va a cambiar.

*key*<br/>
Nueva clave.

*Val*<br/>
Nuevo valor.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente, FALSE si el índice no era válido.

### <a name="remarks"></a>Observaciones

Actualiza tanto la clave como el valor a los que apunta *nIndex*.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
