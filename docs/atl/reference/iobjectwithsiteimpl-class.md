---
title: Clase IObjectWithSiteImpl
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329643"
---
# <a name="iobjectwithsiteimpl-class"></a>Clase IObjectWithSiteImpl

Esta clase proporciona métodos que permiten que un objeto se comunique con su sitio.

## <a name="syntax"></a>Sintaxis

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IObjectWithSiteImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Consulta el sitio para un puntero de interfaz.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Proporciona el objeto con `IUnknown` el puntero del sitio.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Proporciona el objeto con `IUnknown` el puntero del sitio.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Administra el puntero `IUnknown` del sitio.|

## <a name="remarks"></a>Observaciones

La interfaz [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) permite que un objeto se comunique con su sitio. Clase `IObjectWithSiteImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

`IObjectWithSiteImpl`especifica dos métodos. El cliente `SetSite`llama primero, pasando `IUnknown` el puntero del sitio. Este puntero se almacena dentro del objeto y más `GetSite`adelante se puede recuperar a través de una llamada a .

Normalmente, se deriva `IObjectWithSiteImpl` la clase cuando se crea un objeto que no es un control. Para los controles, derive la clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio. No derive su clase `IObjectWithSiteImpl` `IOleObjectImpl`de ambos y .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite

Consulta el sitio para obtener un `riid`puntero a la interfaz identificada por .

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Observaciones

Si el sitio admite esta interfaz, el puntero se devuelve a través `ppvSite`de . De `ppvSite` lo contrario, se establece en NULL.

Consulte [IObjectWithSite::GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) en el Windows SDK.

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

Administra el puntero `IUnknown` del sitio.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Observaciones

`m_spUnkSite`inicialmente recibe este puntero a través de una llamada a [SetSite](#setsite).

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

Proporciona el objeto con `IUnknown` el puntero del sitio.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parámetros

*pUnkSite*<br/>
[en] Puntero al `IUnknown` puntero de interfaz del sitio que administra este objeto. Si NULL, el `IUnknown::Release` objeto debe llamar a cualquier sitio existente en cuyo momento el objeto ya no conoce su sitio.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite

Proporciona el objeto con `IUnknown` el puntero del sitio.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Observaciones

Consulte [IObjectWithSite::SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
