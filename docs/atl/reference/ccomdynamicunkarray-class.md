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
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497246"
---
# <a name="ccomdynamicunkarray-class"></a>Clase CComDynamicUnkArray

Esta clase almacena una matriz de `IUnknown` punteros.

## <a name="syntax"></a>Sintaxis

```
class CComDynamicUnkArray
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Constructor. Inicializa los valores de la colección en NULL y el tamaño de la colección en cero.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Llame a este método para agregar `IUnknown` un puntero a la matriz.|
|[CComDynamicUnkArray::begin](#begin)|Devuelve un puntero al primer `IUnknown` puntero de la colección.|
|[CComDynamicUnkArray::clear](#clear)|Vacía la matriz.|
|[CComDynamicUnkArray::end](#end)|Devuelve un puntero a uno más allá del `IUnknown` último puntero de la colección.|
|[CComDynamicUnkArray::GetAt](#getat)|Recupera el elemento en el índice especificado.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Llame a este método para obtener la cookie asociada a un `IUnknown` puntero determinado.|
|[CComDynamicUnkArray::GetSize](#getsize)|Devuelve la longitud de una matriz.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Llame a este método para obtener `IUnknown` el puntero asociado a una cookie determinada.|
|[CComDynamicUnkArray::Remove](#remove)|Llame a este método para quitar `IUnknown` un puntero de la matriz.|

## <a name="remarks"></a>Comentarios

`CComDynamicUnkArray`contiene una matriz de `IUnknown` punteros asignada dinámicamente, cada una de las interfaces de un punto de conexión. `CComDynamicUnkArray`se puede usar como un parámetro para la clase de plantilla [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

Los `CComDynamicUnkArray` métodos [Begin](#begin) y [End](#end) se pueden usar para recorrer en bucle todos los puntos de conexión (por ejemplo, cuando se desencadena un evento).

Consulte [Agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md) para obtener más información sobre la automatización de la creación de servidores proxy de punto de conexión.

> [!NOTE]
> **Nota:** El asistente `CComDynamicUnkArray` para **Agregar clases** usa la clase al crear un control que tiene puntos de conexión. Si desea especificar el número de puntos de conexión manualmente, `CComDynamicUnkArray` cambie la referencia de a `>` `CComUnkArray<` n, donde *n* es el número de puntos de conexión necesarios.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="add"></a>  CComDynamicUnkArray::Add

Llame a este método para agregar `IUnknown` un puntero a la matriz.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
`IUnknown` Puntero que se va a agregar a la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada al puntero recién agregado.

##  <a name="begin"></a>  CComDynamicUnkArray::begin

Devuelve un puntero al principio de la colección de punteros de `IUnknown` interfaz.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `IUnknown` puntero de interfaz.

### <a name="remarks"></a>Comentarios

La colección contiene punteros a interfaces almacenadas localmente `IUnknown`como. Convierta cada `IUnknown` interfaz en el tipo de interfaz real y, a continuación, llame a través de ella. No es necesario consultar primero la interfaz.

Antes de utilizar `IUnknown` la interfaz, debe comprobar que no es NULL.

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

Establece el tamaño de la colección en cero e inicializa los valores en NULL. El destructor libera la colección, si es necesario.

##  <a name="dtor"></a>  CComDynamicUnkArray::~CComDynamicUnkArray

Destructor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Comentarios

Libera los recursos asignados por el constructor de clase.

##  <a name="end"></a>  CComDynamicUnkArray::end

Devuelve un puntero a uno más allá del `IUnknown` último puntero de la colección.

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

Puntero a una interfaz [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) .

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

Llame a este método para obtener la cookie asociada a un `IUnknown` puntero determinado.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parámetros

*ppFind*<br/>
`IUnknown` Puntero para el que se requiere la cookie asociada.

### <a name="return-value"></a>Valor devuelto

Devuelve la cookie asociada `IUnknown` al puntero o cero si no se encuentra ningún puntero coincidente. `IUnknown`

### <a name="remarks"></a>Comentarios

Si hay más de una instancia del mismo `IUnknown` puntero, esta función devuelve la cookie para la primera.

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

Devuelve la longitud de una matriz.

```
int GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud de la matriz.

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

Llame a este método para obtener `IUnknown` el puntero asociado a una cookie determinada.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
Cookie para la que se requiere `IUnknown` el puntero asociado.

### <a name="return-value"></a>Valor devuelto

Devuelve el `IUnknown` puntero o null si no se encuentra ninguna cookie coincidente.

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

Llame a este método para quitar `IUnknown` un puntero de la matriz.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parámetros

*dwCookie*<br/>
Cookie que hace referencia `IUnknown` al puntero que se va a quitar de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se quita el puntero; en caso contrario, FALSE.

## <a name="see-also"></a>Vea también

[CComUnkArray (clase)](../../atl/reference/ccomunkarray-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
