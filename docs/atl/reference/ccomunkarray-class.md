---
title: CComUnkArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: 7a73158e407279b529f76484e4c32f0a8a7a63c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259461"
---
# <a name="ccomunkarray-class"></a>CComUnkArray (clase)

Esta clase almacena `IUnknown` punteros y está diseñado para usarse como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla.

## <a name="syntax"></a>Sintaxis

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parámetros

*nMaxSize*<br/>
El número máximo de `IUnknown` punteros que se pueden almacenar en la matriz estática.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComUnkArray::Add](#add)|Llame a este método para agregar un `IUnknown` puntero a la matriz.|
|[CComUnkArray::begin](#begin)|Devuelve un puntero al primer `IUnknown` puntero en la colección.|
|[CComUnkArray::end](#end)|Devuelve un puntero a uno más allá del último `IUnknown` puntero en la colección.|
|[CComUnkArray::GetCookie](#getcookie)|Llame a este método para obtener la cookie asociada con un determinado `IUnknown` puntero.|
|[CComUnkArray::GetUnknown](#getunknown)|Llame a este método para obtener el `IUnknown` puntero asociado a una cookie determinada.|
|[CComUnkArray::Remove](#remove)|Llame a este método para quitar un `IUnknown` puntero de la matriz.|

## <a name="remarks"></a>Comentarios

`CComUnkArray` contiene un número fijo de `IUnknown` punteros, cada uno una interfaz en una conexión de punto. `CComUnkArray` se puede usar como un parámetro a la [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) clase de plantilla. `CComUnkArray<1>` es una especialización de plantilla de `CComUnkArray` que se ha optimizado para un punto de conexión.

El `CComUnkArray` métodos [comenzar](#begin) y [final](#end) puede usarse para recorrer en iteración todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).

Consulte [agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md) para obtener más información acerca de cómo automatizar la creación de conexión de punto de proxy.

> [!NOTE]
> **Tenga en cuenta** la clase [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) está usando el **Agregar clase** asistente al crear un control que tiene puntos de conexión. Si desea especificar manualmente el número de puntos de conexión, cambie la referencia de `CComDynamicUnkArray` a `CComUnkArray<` *n* `>`, donde *n* es el número de puntos de conexión Obligatorio.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

Llame a este método para agregar un `IUnknown` puntero a la matriz.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
Llame a este método para agregar un `IUnknown` puntero a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el puntero recién agregado, o 0 si la matriz no es suficientemente grande como para contener el nuevo puntero.

##  <a name="begin"></a>  CComUnkArray::begin

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

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

El constructor.

```
CComUnkArray();
```

### <a name="remarks"></a>Comentarios

Establece la colección para contener `nMaxSize` `IUnknown` punteros e inicializa los punteros a NULL.

##  <a name="end"></a>  CComUnkArray::end

Devuelve un puntero a uno más allá del último `IUnknown` puntero en la colección.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `IUnknown` puntero de interfaz.

### <a name="remarks"></a>Comentarios

El `CComUnkArray` métodos `begin` y `end` puede usarse para recorrer en bucle todos los puntos de conexión, por ejemplo, cuando se desencadena un evento.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

Llame a este método para obtener la cookie asociada con un determinado `IUnknown` puntero.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parámetros

*ppFind*<br/>
El `IUnknown` puntero para el que se requiere la cookie asociada.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el `IUnknown` puntero, o 0 si no hay coincidencia `IUnknown` puntero se encuentra.

### <a name="remarks"></a>Comentarios

Si hay más de una instancia de la misma `IUnknown` puntero, esta función devuelve la cookie para la primera de ellas.

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

Llame a este método para obtener el `IUnknown` puntero asociado a una cookie determinada.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
Para que la cookie de asociado `IUnknown` puntero es necesario.

### <a name="return-value"></a>Valor devuelto

Devuelve el `IUnknown` puntero, o NULL si no se encuentra ninguna cookie de búsqueda de coincidencias.

##  <a name="remove"></a>  CComUnkArray::Remove

Llame a este método para quitar un `IUnknown` puntero de la matriz.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie que hacen referencia a la `IUnknown` puntero va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el puntero se ha quitado, FALSE en caso contrario.

## <a name="see-also"></a>Vea también

[CComDynamicUnkArray (clase)](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
