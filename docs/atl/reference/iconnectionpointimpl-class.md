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
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329853"
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
Su clase, derivada `IConnectionPointImpl`de .

*piid*<br/>
Puntero al IID de la interfaz representada por el objeto de punto de conexión.

*Cdv*<br/>
Una clase que administra las conexiones. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas. También puede utilizar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|Establece una conexión entre el punto de conexión y un receptor.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crea un enumerador para recorrer en iteración las conexiones del punto de conexión.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Recupera el IID de la interfaz representada por el punto de conexión.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Recupera un puntero de interfaz al objeto conectable.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Termina una conexión previamente establecida a través `Advise`de .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Administra las conexiones para el punto de conexión.|

## <a name="remarks"></a>Observaciones

`IConnectionPointImpl`implementa un punto de conexión, que permite a un objeto exponer una interfaz saliente al cliente. El cliente implementa esta interfaz en un objeto denominado receptor.

ATL usa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) para implementar el objeto conectable. Cada punto de conexión dentro del objeto conectable representa una interfaz saliente, identificada por *piid*. La clase *CDV* administra las conexiones entre el punto de conexión y un receptor. Cada conexión se identifica de forma única mediante una "cookie".

Para obtener más información sobre el uso de puntos de conexión en ATL, consulte el artículo [Puntos](../../atl/atl-connection-points.md)de conexión .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointImpl::Advise

Establece una conexión entre el punto de conexión y un receptor.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Observaciones

Utilice [Unadvise](#unadvise) para finalizar la llamada de conexión.

Consulte [IConnectionPoint::Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) en el Windows SDK.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Crea un enumerador para recorrer en iteración las conexiones del punto de conexión.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Observaciones

Consulte [IConnectionPoint::EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) en el Windows SDK.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface

Recupera el IID de la interfaz representada por el punto de conexión.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Observaciones

Consulte [IConnectionPoint::GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) en el Windows SDK.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer

Recupera un puntero de interfaz al objeto conectable.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Observaciones

Consulte [IConnectionPoint::GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) en el Windows SDK.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointImpl::m_vec

Administra las conexiones entre el objeto de punto de conexión y un receptor.

```
CDV m_vec;
```

### <a name="remarks"></a>Observaciones

De forma `m_vec` predeterminada, es de tipo [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointImpl::Unadvise

Termina una conexión previamente establecida a través de [Advise](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Observaciones

Consulte [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
