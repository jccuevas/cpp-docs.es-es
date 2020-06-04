---
title: Clase CComUnkArray
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
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327302"
---
# <a name="ccomunkarray-class"></a>Clase CComUnkArray

Esta clase `IUnknown` almacena punteros y está diseñada para usarse como parámetro para la clase de plantilla [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Sintaxis

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parámetros

*nMaxSize*<br/>
El número `IUnknown` máximo de punteros que se pueden mantener en la matriz estática.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComUnkArray::Add](#add)|Llame a este `IUnknown` método para agregar un puntero a la matriz.|
|[CComUnkArray::begin](#begin)|Devuelve un puntero `IUnknown` al primer puntero de la colección.|
|[CComUnkArray::end](#end)|Devuelve un puntero a `IUnknown` uno más allá del último puntero de la colección.|
|[CComUnkArray::GetCookie](#getcookie)|Llame a este método para obtener `IUnknown` la cookie asociada a un puntero determinado.|
|[CComUnkArray::GetUnknown](#getunknown)|Llame a este `IUnknown` método para obtener el puntero asociado a una cookie determinada.|
|[CComUnkArray::Remove](#remove)|Llame a este `IUnknown` método para quitar un puntero de la matriz.|

## <a name="remarks"></a>Observaciones

`CComUnkArray`contiene un número `IUnknown` fijo de punteros, cada uno una interfaz en un punto de conexión. `CComUnkArray`se puede utilizar como parámetro para la clase de plantilla [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `CComUnkArray<1>`es una especialización de plantilla de `CComUnkArray` que se ha optimizado para un punto de conexión.

Los `CComUnkArray` métodos [begin](#begin) y [end](#end) se pueden utilizar para recorrer en bucle todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).

Consulte Adición de [puntos](../../atl/adding-connection-points-to-an-object.md) de conexión a un objeto para obtener más información sobre cómo automatizar la creación de servidores proxy de punto de conexión.

> [!NOTE]
> **Nota** La clase [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) es utilizado por el Asistente para **agregar clase** al crear un control que tiene puntos de conexión. Si desea especificar manualmente el número de puntos `CComDynamicUnkArray` de `CComUnkArray<` conexión, cambie la referencia de *n* `>`, donde *n* es el número de puntos de conexión necesarios.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Add

Llame a este `IUnknown` método para agregar un puntero a la matriz.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
Llame a este `IUnknown` método para agregar un puntero a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el puntero recién agregado, o 0 si la matriz no es lo suficientemente grande como para contener el nuevo puntero.

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::begin

Devuelve un puntero al principio `IUnknown` de la colección de punteros de interfaz.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valor devuelto

Un puntero `IUnknown` a un puntero de interfaz.

### <a name="remarks"></a>Observaciones

La colección contiene punteros a `IUnknown`interfaces almacenadas localmente como . Usted convierte `IUnknown` cada interfaz al tipo de interfaz real y después llama a través de ella. No es necesario consultar primero la interfaz.

Antes de `IUnknown` usar la interfaz, debe comprobar que no es NULL.

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray

El constructor.

```
CComUnkArray();
```

### <a name="remarks"></a>Observaciones

Establece la colección para contener `nMaxSize` `IUnknown` punteros e inicializa los punteros a NULL.

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkArray::end

Devuelve un puntero a `IUnknown` uno más allá del último puntero de la colección.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valor devuelto

Un puntero `IUnknown` a un puntero de interfaz.

### <a name="remarks"></a>Observaciones

Los `CComUnkArray` `begin` métodos y `end` se pueden utilizar para recorrer en bucle todos los puntos de conexión, por ejemplo, cuando se desencadena un evento.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie

Llame a este método para obtener `IUnknown` la cookie asociada a un puntero determinado.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parámetros

*ppFind*<br/>
Puntero `IUnknown` para el que se requiere la cookie asociada.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie `IUnknown` asociada con el puntero, o 0 si no se encuentra ningún puntero coincidente. `IUnknown`

### <a name="remarks"></a>Observaciones

Si hay más de una `IUnknown` instancia del mismo puntero, esta función devuelve la cookie para la primera.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown

Llame a este `IUnknown` método para obtener el puntero asociado a una cookie determinada.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie para `IUnknown` la que se requiere el puntero asociado.

### <a name="return-value"></a>Valor devuelto

Devuelve `IUnknown` el puntero o NULL si no se encuentra ninguna cookie coincidente.

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Remove

Llame a este `IUnknown` método para quitar un puntero de la matriz.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie que `IUnknown` hace referencia al puntero que se va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se quita el puntero, FALSE en caso contrario.

## <a name="see-also"></a>Consulte también

[Clase CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
