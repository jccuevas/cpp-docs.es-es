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
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495834"
---
# <a name="iobjectwithsiteimpl-class"></a>Clase IObjectWithSiteImpl

Esta clase proporciona métodos que permiten a un objeto comunicarse con su sitio.

## <a name="syntax"></a>Sintaxis

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IObjectWithSiteImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Consulta el sitio para obtener un puntero de interfaz.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Proporciona el objeto con el puntero del `IUnknown` sitio.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Proporciona el objeto con el puntero del `IUnknown` sitio.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Administra el puntero del `IUnknown` sitio.|

## <a name="remarks"></a>Comentarios

La interfaz [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) permite que un objeto se comunique con su sitio. La `IObjectWithSiteImpl` clase proporciona una implementación predeterminada de esta interfaz e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

`IObjectWithSiteImpl`especifica dos métodos. El cliente llama primero `SetSite`a, pasando el puntero `IUnknown` del sitio. Este puntero se almacena en el objeto y se puede recuperar más adelante mediante una llamada a `GetSite`.

Normalmente, la clase se deriva de `IObjectWithSiteImpl` cuando se crea un objeto que no es un control. En el caso de los controles, derive la clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio. No derive su clase de `IObjectWithSiteImpl` y. `IOleObjectImpl`

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

Consulta el sitio para obtener un puntero a la interfaz identificada por `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Comentarios

Si el sitio admite esta interfaz, el puntero se devuelve a `ppvSite`través de. De lo `ppvSite` contrario, se establece en NULL.

Vea [IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) en el Windows SDK.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Administra el puntero del `IUnknown` sitio.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Comentarios

`m_spUnkSite`recibe inicialmente este puntero a través de una llamada a [SetSite](#setsite).

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

Proporciona el objeto con el puntero del `IUnknown` sitio.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parámetros

*pUnkSite*<br/>
de Puntero al `IUnknown` puntero de interfaz del sitio que administra este objeto. Si es null, el objeto debe `IUnknown::Release` llamar a en cualquier sitio existente, en el que el objeto ya no conoce su sitio.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

Proporciona el objeto con el puntero del `IUnknown` sitio.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Comentarios

Vea [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
