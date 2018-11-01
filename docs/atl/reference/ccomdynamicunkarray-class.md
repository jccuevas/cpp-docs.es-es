---
title: CComDynamicUnkArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: c18f28cac89288096b812635e77194bfb5dd224b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448690"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray (clase)

Esta clase almacena una matriz de `IUnknown` punteros.

## <a name="syntax"></a>Sintaxis

```
class CComDynamicUnkArray
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructor. Inicializa los valores de la colección es NULL y el tamaño de la colección a cero.|
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Llame a este método para agregar un `IUnknown` puntero a la matriz.|
|[CComDynamicUnkArray::begin](#begin)|Devuelve un puntero al primer `IUnknown` puntero en la colección.|
|[CComDynamicUnkArray::clear](#clear)|Vacía la matriz.|
|[CComDynamicUnkArray::end](#end)|Devuelve un puntero a uno más allá del último `IUnknown` puntero en la colección.|
|[CComDynamicUnkArray::GetAt](#getat)|Recupera el elemento en el índice especificado.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Llame a este método para obtener la cookie asociada con un determinado `IUnknown` puntero.|
|[CComDynamicUnkArray::GetSize](#getsize)|Devuelve la longitud de la matriz.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Llame a este método para obtener el `IUnknown` puntero asociado a una cookie determinada.|
|[CComDynamicUnkArray::Remove](#remove)|Llame a este método para quitar un `IUnknown` puntero de la matriz.|

## <a name="remarks"></a>Comentarios

`CComDynamicUnkArray` contiene una matriz asignada dinámicamente de `IUnknown` punteros, cada uno una interfaz en una conexión de punto. `CComDynamicUnkArray` se puede usar como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.

El `CComDynamicUnkArray` métodos [comenzar](#begin) y [final](#end) puede usarse para recorrer en iteración todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).

Consulte [agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md) para obtener más información acerca de cómo automatizar la creación de conexión de punto de proxy.

> [!NOTE]
> **Tenga en cuenta** la clase `CComDynamicUnkArray` está usando el **Agregar clase** asistente al crear un control que tiene puntos de conexión. Si desea especificar manualmente el número de puntos de conexión, cambie la referencia de `CComDynamicUnkArray` a `CComUnkArray<` *n* `>`, donde *n* es el número de puntos de conexión Obligatorio.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="add"></a>  CComDynamicUnkArray::Add

Llame a este método para agregar un `IUnknown` puntero a la matriz.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
El `IUnknown` puntero para agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el puntero recién agregado.

##  <a name="begin"></a>  CComDynamicUnkArray::begin

Devuelve un puntero al principio de la colección de `IUnknown` punteros de interfaz.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `IUnknown` puntero de interfaz.

### <a name="remarks"></a>Comentarios

La colección contiene punteros a las interfaces que se almacena localmente como `IUnknown`. Convierte cada `IUnknown` interfaz para el tipo de interfaz real y, a continuación, llamar a través de él. No es necesario consultar primero la interfaz.

Antes de usar el `IUnknown` interfaz, debe comprobar que no es NULL.

##  <a name="clear"></a>  CComDynamicUnkArray::clear

Vacía la matriz.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray

El constructor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Comentarios

El tamaño de la colección se establece en cero e inicializa los valores NULL. El destructor libera la colección, si es necesario.

##  <a name="dtor"></a>  CComDynamicUnkArray:: ~ CComDynamicUnkArray

Destructor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Comentarios

Libera recursos asignados por el constructor de clase.

##  <a name="end"></a>  CComDynamicUnkArray::end

Devuelve un puntero a uno más allá del último `IUnknown` puntero en la colección.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `IUnknown` puntero de interfaz.

##  <a name="getat"></a>  CComDynamicUnkArray::GetAt

Recupera el elemento en el índice especificado.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfaz.

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

Llame a este método para obtener la cookie asociada con un determinado `IUnknown` puntero.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parámetros

*ppFind*<br/>
El `IUnknown` puntero para el que se requiere la cookie asociada.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el `IUnknown` puntero, o cero si no hay coincidencia `IUnknown` puntero se encuentra.

### <a name="remarks"></a>Comentarios

Si hay más de una instancia de la misma `IUnknown` puntero, esta función devuelve la cookie para la primera de ellas.

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

Devuelve la longitud de la matriz.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud de la matriz.

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

Llame a este método para obtener el `IUnknown` puntero asociado a una cookie determinada.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
Para que la cookie de asociado `IUnknown` puntero es necesario.

### <a name="return-value"></a>Valor devuelto

Devuelve el `IUnknown` puntero, o NULL si no se encuentra ninguna cookie de búsqueda de coincidencias.

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

Llame a este método para quitar un `IUnknown` puntero de la matriz.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie que hacen referencia a la `IUnknown` puntero va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se quita el puntero; en caso contrario, FALSE.

## <a name="see-also"></a>Vea también

[CComUnkArray (clase)](../../atl/reference/ccomunkarray-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
