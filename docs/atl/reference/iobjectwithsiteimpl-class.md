---
title: IObjectWithSiteImpl (clase)
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
ms.openlocfilehash: 776f6f67c0490afb9d3ca975fcee7596d415ac12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608928"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl (clase)

Esta clase proporciona métodos que permiten a un objeto para comunicarse con su sitio.

## <a name="syntax"></a>Sintaxis

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IObjectWithSiteImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Consulta el sitio para un puntero de interfaz.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Proporciona el objeto con el sitio `IUnknown` puntero.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Proporciona el objeto con el sitio `IUnknown` puntero.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Administra el sitio `IUnknown` puntero.|

## <a name="remarks"></a>Comentarios

El [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) interfaz permite que un objeto para comunicarse con su sitio. Clase `IObjectWithSiteImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

`IObjectWithSiteImpl` Especifica los dos métodos. El cliente llama primero `SetSite`, pasando el sitio `IUnknown` puntero. Este puntero se almacena dentro del objeto y, más adelante se puede recuperar mediante una llamada a `GetSite`.

Normalmente, deriva la clase de `IObjectWithSiteImpl` cuando se crea un objeto que no es un control. Para los controles, derive la clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio. No se derivan la clase de ambos `IObjectWithSiteImpl` y `IOleObjectImpl`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

Consulta el sitio para un puntero a la interfaz identificada por `riid`.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Comentarios

Si el sitio admite esta interfaz, se devuelve el puntero a través de `ppvSite`. En caso contrario, `ppvSite` se establece en NULL.

Consulte [IObjectWithSite::GetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-getsite) en el SDK de Windows.

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

Administra el sitio `IUnknown` puntero.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Comentarios

`m_spUnkSite` inicialmente recibe este puntero mediante una llamada a [SetSite](#setsite).

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

Proporciona el objeto con el sitio `IUnknown` puntero.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parámetros

*pUnkSite*<br/>
[in] Puntero a la `IUnknown` puntero de interfaz del sitio de administración de este objeto. Si es NULL, el objeto debe llamar a `IUnknown::Release` en cualquier momento en que el objeto ya no conoce su sitio de sitio existente.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

Proporciona el objeto con el sitio `IUnknown` puntero.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Comentarios

Consulte [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
