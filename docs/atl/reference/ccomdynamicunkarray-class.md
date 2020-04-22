---
title: Clase CComDynamicUnkArray
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
ms.openlocfilehash: 51b1d7e81c98bd5dbcf957b1705e7a717bfb9ab0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747977"
---
# <a name="ccomdynamicunkarray-class"></a>Clase CComDynamicUnkArray

Esta clase almacena `IUnknown` una matriz de punteros.

## <a name="syntax"></a>Sintaxis

```
class CComDynamicUnkArray
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructor. Inicializa los valores de colección en NULL y el tamaño de la colección en cero.|
|[CComDynamicUnkArray::-CComDynamicUnkArray](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Llame a este `IUnknown` método para agregar un puntero a la matriz.|
|[CComDynamicUnkArray::begin](#begin)|Devuelve un puntero `IUnknown` al primer puntero de la colección.|
|[CComDynamicUnkArray::clear](#clear)|Vacía la matriz.|
|[CComDynamicUnkArray::end](#end)|Devuelve un puntero a `IUnknown` uno más allá del último puntero de la colección.|
|[CComDynamicUnkArray::GetAt](#getat)|Recupera el elemento en el índice especificado.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Llame a este método para obtener `IUnknown` la cookie asociada a un puntero determinado.|
|[CComDynamicUnkArray::GetSize](#getsize)|Devuelve la longitud de una matriz.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Llame a este `IUnknown` método para obtener el puntero asociado a una cookie determinada.|
|[CComDynamicUnkArray::Remove](#remove)|Llame a este `IUnknown` método para quitar un puntero de la matriz.|

## <a name="remarks"></a>Observaciones

`CComDynamicUnkArray`contiene una matriz de `IUnknown` punteros asignada dinámicamente, cada uno de los dos una interfaz en un punto de conexión. `CComDynamicUnkArray`se puede utilizar como parámetro para la clase de plantilla [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

Los `CComDynamicUnkArray` métodos [begin](#begin) y [end](#end) se pueden utilizar para recorrer en bucle todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).

Consulte Adición de [puntos](../../atl/adding-connection-points-to-an-object.md) de conexión a un objeto para obtener más información sobre cómo automatizar la creación de servidores proxy de punto de conexión.

> [!NOTE]
> **Nota** La `CComDynamicUnkArray` clase la utiliza el asistente **Agregar clase** al crear un control que tiene puntos de conexión. Si desea especificar manualmente el número de puntos `CComDynamicUnkArray` de `CComUnkArray<` conexión, cambie la referencia de *n* `>`, donde *n* es el número de puntos de conexión necesarios.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkArray::Add

Llame a este `IUnknown` método para agregar un puntero a la matriz.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
El `IUnknown` puntero que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada con el puntero recién agregado.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkArray::begin

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

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkArray::clear

Vacía la matriz.

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

El constructor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Observaciones

Establece el tamaño de la colección en cero e inicializa los valores en NULL. El destructor libera la colección, si es necesario.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkArray::-CComDynamicUnkArray

Destructor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Observaciones

Libera los recursos asignados por el constructor de clase.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkArray::end

Devuelve un puntero a `IUnknown` uno más allá del último puntero de la colección.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Valor devuelto

Un puntero `IUnknown` a un puntero de interfaz.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkArray::GetAt

Recupera el elemento en el índice especificado.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del elemento que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Un puntero a una interfaz [IUnknown.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkArray::GetCookie

Llame a este método para obtener `IUnknown` la cookie asociada a un puntero determinado.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parámetros

*ppFind*<br/>
Puntero `IUnknown` para el que se requiere la cookie asociada.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie `IUnknown` asociada con el puntero, o cero si no se encuentra ningún puntero coincidente. `IUnknown`

### <a name="remarks"></a>Observaciones

Si hay más de una `IUnknown` instancia del mismo puntero, esta función devuelve la cookie para la primera.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkArray::GetSize

Devuelve la longitud de una matriz.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud de la matriz.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

Llame a este `IUnknown` método para obtener el puntero asociado a una cookie determinada.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie para `IUnknown` la que se requiere el puntero asociado.

### <a name="return-value"></a>Valor devuelto

Devuelve `IUnknown` el puntero o NULL si no se encuentra ninguna cookie coincidente.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkArray::Remove

Llame a este `IUnknown` método para quitar un puntero de la matriz.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
La cookie que `IUnknown` hace referencia al puntero que se va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se quita el puntero; de lo contrario FALSO.

## <a name="see-also"></a>Vea también

[Clase CComUnkArray](../../atl/reference/ccomunkarray-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
