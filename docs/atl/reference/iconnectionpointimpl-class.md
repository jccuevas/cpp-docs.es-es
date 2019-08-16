---
title: Clase IConnectionPointImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: bd88fd5d00df0347c0bd2161129b8cfa3ca35406
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496079"
---
# <a name="iconnectionpointimpl-class"></a>Clase IConnectionPointImpl

Esta clase implementa un punto de conexión.

## <a name="syntax"></a>Sintaxis

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IConnectionPointImpl`.

*piid*<br/>
Puntero al IID de la interfaz representada por el objeto de punto de conexión.

*CDV*<br/>
Una clase que administra las conexiones. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|Establece una conexión entre el punto de conexión y un receptor.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crea un enumerador para recorrer en iteración las conexiones del punto de conexión.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Recupera el IID de la interfaz representada por el punto de conexión.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Recupera un puntero de interfaz al objeto conectable.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Finaliza una conexión establecida previamente a través `Advise`de.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Administra las conexiones para el punto de conexión.|

## <a name="remarks"></a>Comentarios

`IConnectionPointImpl`implementa un punto de conexión, que permite a un objeto exponer una interfaz de salida al cliente. El cliente implementa esta interfaz en un objeto denominado receptor.

ATL usa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) para implementar el objeto conectable. Cada punto de conexión dentro del objeto conectable representa una interfaz de salida, identificada por *piid*. La clase *CDV* administra las conexiones entre el punto de conexión y un receptor. Cada conexión se identifica de forma única mediante una "cookie".

Para obtener más información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="advise"></a>  IConnectionPointImpl::Advise

Establece una conexión entre el punto de conexión y un receptor.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Comentarios

Use [Unadvise](#unadvise) para finalizar la llamada de conexión.

Vea [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) en el Windows SDK.

##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections

Crea un enumerador para recorrer en iteración las conexiones del punto de conexión.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) en el Windows SDK.

##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface

Recupera el IID de la interfaz representada por el punto de conexión.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) en el Windows SDK.

##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer

Recupera un puntero de interfaz al objeto conectable.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) en el Windows SDK.

##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec

Administra las conexiones entre el objeto de punto de conexión y un receptor.

```
CDV m_vec;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada `m_vec` , es de tipo [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise

Finaliza una conexión establecida previamente a través de una [notificación](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPoint:: unvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
