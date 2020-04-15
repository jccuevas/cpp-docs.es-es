---
title: Clase IOleObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326525"
---
# <a name="ioleobjectimpl-class"></a>Clase IOleObjectImpl

Esta clase `IUnknown` implementa y es la interfaz principal a través de la cual un contenedor se comunica con un control.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IOleObjectImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|Establece una conexión de asesoramiento con el control.|
|[IOleObjectImpl::Cerrar](#close)|Cambia el estado del control de la ejecución a la carga.|
|[IOleObjectImpl::DoVerb](#doverb)|Indica al control que realice una de sus acciones enumeradas.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indica al control que descarte cualquier estado de deshacer que esté manteniendo.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indica al control que quite su interfaz de usuario de la vista.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Ejecuta el control e instala su ventana, pero no instala la interfaz de usuario del control.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Hace que el control se edite abiertamente en una ventana independiente.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Realiza la acción especificada cuando el usuario hace doble clic en el control. El control define la acción, normalmente para activar el control in situ.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Muestra un control recién insertado al usuario.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Activa el control in situ y muestra la interfaz de usuario del control, como menús y barras de herramientas.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera las conexiones de asesoramiento del control.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera las acciones para el control.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera el sitio de cliente del control.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera datos del Portapapeles. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Recupera la extensión del área de visualización del control.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera el estado del control.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera el apodo del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera el identificador de clase del control.|
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera el nombre de tipo de usuario del control.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa el control a partir de los datos seleccionados. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Comprueba si el control está actualizado. La implementación de ATL devuelve S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Llamado por [DoVerbHide](#doverbhide) después de que el control está oculto.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Llamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) después de que el control se activa en su lugar.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Llamado por [DoVerbOpen](#doverbopen) después de que el control se ha abierto para su edición en una ventana independiente.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Llamado por [DoVerbShow](#doverbshow) después de que el control se ha hecho visible.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Llamado por [DoVerbUIActivate](#doverbuiactivate) después de que se ha activado la interfaz de usuario del control.|
|[IOleObjectImpl::OnPreverbDiscardUndo](#onpreverbdiscardundo)|Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de que se descarte el estado de deshacer.|
|[IOleObjectImpl::OnPreverbHide](#onpreverbhide)|Llamado por [DoVerbHide](#doverbhide) antes de que el control esté oculto.|
|[IOleObjectImpl::OnPreverbInPlaceActivate](#onpreverbinplaceactivate)|Llamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control se active en su lugar.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Llamado por [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para su edición en una ventana independiente.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Llamado por [DoVerbShow](#doverbshow) antes de que el control se haya hecho visible.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Llamado por [DoVerbUIActivate](#doverbuiactivate) antes de que se haya activado la interfaz de usuario del control.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indica el control sobre su sitio de cliente en el contenedor.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recomienda un esquema de color a la aplicación del control, si existe. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Establece la extensión del área de visualización del control.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indica al control los nombres de la aplicación contenedora y el documento contenedor.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Le dice al control cuál es su apodo. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Elimina una conexión de aviso con el control.|
|[IOleObjectImpl::Update](#update)|Actualiza el control. La implementación de ATL devuelve S_OK.|

## <a name="remarks"></a>Observaciones

La interfaz [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) es la interfaz principal a través de la cual un contenedor se comunica con un control. Clase `IOleObjectImpl` proporciona una implementación predeterminada `IUnknown` de esta interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectImpl::Advise

Establece una conexión de asesoramiento con el control.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) en el Windows SDK.

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectImpl::Cerrar

Cambia el estado del control de la ejecución a la carga.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Observaciones

Desactiva el control y destruye la ventana de control si existe. Si el miembro de datos de clase de control [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) es TRUE y el *dwSaveOption* parámetro es OLECLOSE_SAVEIFDIRTY o OLECLOSE_PROMPTSAVE, las propiedades del control se guardan antes de cerrar.

Los punteros mantenidos en los miembros de datos de la clase de control [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) y [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) se liberan y los miembros de datos [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)) y [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) se establecen en FALSE.

Consulte [IOleObject::Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) en el Windows SDK.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb

Indica al control que realice una de sus acciones enumeradas.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>Observaciones

Dependiendo del valor `iVerb`de , se `DoVerb` llama a una de las funciones auxiliares de ATL de la siguiente manera:

|*iVerb* Valor|Función auxiliar DoVerb llamada|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Consulte [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo

Indica al control que descarte cualquier estado de deshacer que esté manteniendo.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide

Desactiva y quita la interfaz de usuario del control y oculta el control.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate

Ejecuta el control e instala su ventana, pero no instala la interfaz de usuario del control.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Activa el control en su lugar mediante una llamada a [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que el `m_bWindowOnly` miembro de `DoVerbInPlaceActivate` datos de la clase de control sea TRUE, primero intenta activar el control como un control sin ventanas (posible solo si el contenedor admite [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Si se produce un error, la función intenta activar el control con características extendidas (solo es posible si el contenedor admite [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Si se produce un error, la función intenta activar el control sin características extendidas (solo es posible si el contenedor admite [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Si la activación se realiza correctamente, la función notifica al contenedor que se ha activado el control.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen

Hace que el control se edite abiertamente en una ventana independiente.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary

Define la acción realizada cuando el usuario hace doble clic en el control.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

De forma predeterminada, se establece para mostrar las páginas de propiedades. Puede invalidar esto en la clase de control para invocar un comportamiento diferente al hacer doble clic; por ejemplo, reproducir un vídeo o ir activo en el lugar.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow

Indica al contenedor que haga visible el control.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate

Activa la interfaz de usuario del control y notifica al contenedor que sus menús se reemplazan por menús compuestos.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[en] Puntero al rectángulo que el contenedor desea que el control se dibuje en.

*hwndParent*<br/>
[en] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Proporciona una enumeración de conexiones de aviso registradas para este control.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) en el Windows SDK.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Proporciona una enumeración de acciones registradas (verbos) para este control mediante una llamada a `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Observaciones

Puede agregar verbos al archivo .rgs del proyecto. Por ejemplo, consulte CIRCCTL. RGS en la muestra [CIRC.](../../overview/visual-cpp-samples.md)

Consulte [IOleObject::EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) en el Windows SDK.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Coloca el puntero en el miembro de datos de clase de control [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* e incrementa el recuento de referencias en el puntero.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) en el Windows SDK.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Recupera datos del Portapapeles.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) en el Windows SDK.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectImpl::GetExtent

Recupera el tamaño de visualización de un control en ejecución en unidades HIMETRIC (0,01 milímetros por unidad).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Observaciones

El tamaño se almacena en el miembro de datos de clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Consulte [IOleObject::GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) en el Windows SDK.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Devuelve un puntero a la información `OleRegGetMiscStatus`de estado registrada para el control mediante una llamada a .

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Observaciones

La información de estado incluye comportamientos admitidos por los datos de control y presentación. Puede agregar información de estado al archivo .rgs del proyecto.

Consulte [IOleObject::GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) en el Windows SDK.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Recupera el apodo del control.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) en el Windows SDK.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Devuelve el identificador de clase del control.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject::GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) en el Windows SDK.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectImpl::GetUserType

Devuelve el nombre de tipo de `OleRegGetUserType`usuario del control llamando a .

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Observaciones

El nombre de tipo de usuario se utiliza para mostrar en elementos de interfaces de usuario como menús y cuadros de diálogo. Puede cambiar el nombre de tipo de usuario en el archivo .rgs del proyecto.

Consulte [IOleObject::GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) en el Windows SDK.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData

Inicializa el control a partir de los datos seleccionados.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el Windows SDK.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Comprueba si el control está actualizado.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) en el Windows SDK.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que se descarte el estado de deshacer.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Llamado por [DoVerbHide](#doverbhide) después de que el control está oculto.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que el control está oculto.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Llamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) después de que el control se activa en su lugar.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de activar el control en su lugar.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Llamado por [DoVerbOpen](#doverbopen) después de que el control se ha abierto para su edición en una ventana independiente.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que el control se ha abierto para su edición en una ventana independiente.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Llamado por [DoVerbShow](#doverbshow) después de que el control se ha hecho visible.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que el control se ha hecho visible.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Llamado por [DoVerbUIActivate](#doverbuiactivate) después de que se ha activado la interfaz de usuario del control.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de activar la interfaz de usuario del control.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreverbDiscardUndo

Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de que se descarte el estado de deshacer.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que se descarte el estado de deshacer, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleObjectImpl::OnPreverbHide

Llamado por [DoVerbHide](#doverbhide) antes de que el control esté oculto.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se osintie, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreverbInPlaceActivate

Llamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control se active en su lugar.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se active en su lugar, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Llamado por [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para su edición en una ventana independiente.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se abra para su edición en una ventana independiente, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Llamado por [DoVerbShow](#doverbshow) antes de que el control se haya hecho visible.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se haga visible, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Llamado por [DoVerbUIActivate](#doverbuiactivate) antes de que se haya activado la interfaz de usuario del control.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que se active la interfaz de usuario del control, invalide este método para devolver un error HRESULT.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Indica el control sobre su sitio de cliente en el contenedor.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Observaciones

A continuación, el método devuelve S_OK.

Consulte [IOleObject::SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) en el Windows SDK.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Recomienda un esquema de color a la aplicación del control, si existe.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el Windows SDK.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectImpl::SetExtent

Establece la extensión del área de visualización del control.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Observaciones

De `SetExtent` lo contrario, almacena `psizel` el valor al que apunta el miembro de datos de clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Este valor está en unidades HIMETRIC (0,01 milímetros por unidad).

Si el miembro de datos de clase de `SetExtent` control [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) es TRUE, también almacena el valor al que apunta `psizel` el miembro de datos de clase de control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si el miembro de datos de clase de `SetExtent` control `SendOnDataChange` `SendOnViewChange` [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) es TRUE, llama y para notificar a todos los receptores de aviso registrados con el titular de advertencia que el tamaño del control ha cambiado.

Consulte [IOleObject::SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) en el Windows SDK.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Indica al control los nombres de la aplicación contenedora y el documento contenedor.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) en el Windows SDK.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Le dice al control cuál es su apodo.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) en el Windows SDK.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Unadvise

Elimina la conexión de aviso almacenada `m_spOleAdviseHolder` en el miembro de datos de la clase de control.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) en el Windows SDK.

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectImpl::Update

Actualiza el control.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IOleObject::Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
