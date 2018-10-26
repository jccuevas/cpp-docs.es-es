---
title: IOleObjectImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0595b98d26b401a93545b96a719a7c0af3440fea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054196"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl (clase)

Esta clase implementa `IUnknown` y es la interfaz principal a través del cual se comunica un contenedor con un control.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IOleObjectImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|Establece una conexión de consulta con el control.|
|[IOleObjectImpl::Close](#close)|Cambia el estado del control de ejecución para cargar.|
|[IOleObjectImpl::DoVerb](#doverb)|Indica al control que realice una de las acciones enumeradas.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indica al control para descartar cualquier estado de deshacer es de mantenimiento.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indica al control para quitar su interfaz de usuario de vista.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Se ejecuta el control y su ventana se instala, pero no instala la interfaz de usuario del control.|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Hace que el control se puede editar para abrir en una ventana independiente.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Realiza la acción especificada cuando el usuario hace doble clic en el control. El control define la acción, normalmente para activar el control en contexto.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Muestra un control recién insertado al usuario.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Activa el control en el lugar y se muestra la interfaz de usuario del control, como menús y barras de herramientas.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera las conexiones de consulta del control.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera las medidas para el control.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera el sitio de cliente del control.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera los datos desde el Portapapeles. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Recupera la extensión del área de presentación del control.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera el estado del control.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera el moniker del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera el identificador de clase del control.|
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera el nombre de tipo de usuario del control.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa el control de datos seleccionado. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Comprueba si el control está actualizado. La implementación de ATL devuelve S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Lo llama [DoVerbHide](#doverbhide) después de que el control está oculto.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) después de activa el control en su lugar.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Lo llama [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Lo llama [DoVerbShow](#doverbshow) después de que se ha realizado el control visible.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Lo llama [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) antes de la fase de reversión se descarta el estado.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Lo llama [DoVerbHide](#doverbhide) antes de que el control está oculto.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control está activado en su lugar.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Lo llama [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para editarlo en una ventana independiente.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Lo llama [DoVerbShow](#doverbshow) antes de que se ha realizado el control visible.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Lo llama [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indica al control sobre su sitio de cliente en el contenedor.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Se recomienda una combinación de colores para la aplicación del control, si existe. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::SetExtent](#setextent)|Establece la magnitud del área de visualización del control.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indica que el control a los nombres de la aplicación de contenedor y el documento contenedor.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indica al control ¿cuál es su moniker. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::Unadvise](#unadvise)|Elimina una conexión de consulta con el control.|
|[IOleObjectImpl::Update](#update)|Actualiza el control. La implementación de ATL devuelve S_OK.|

## <a name="remarks"></a>Comentarios

El [IOleObject](/windows/desktop/api/oleidl/nn-oleidl-ioleobject) interfaz es la entidad de seguridad a través del cual se comunica un contenedor con un control. Clase `IOleObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="advise"></a>  IOleObjectImpl::Advise

Establece una conexión de consulta con el control.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::Advise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-advise) en el SDK de Windows.

##  <a name="close"></a>  IOleObjectImpl::Close

Cambia el estado del control de ejecución para cargar.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Comentarios

Desactiva el control y destruye la ventana de control, si existe. Si el control de clase de miembro de datos [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) es TRUE y el *dwSaveOption* parámetro es OLECLOSE_SAVEIFDIRTY o OLECLOSE_PROMPTSAVE, son las propiedades del control guardar antes de cerrarse.

Los punteros conservan en los miembros de datos de la clase de control [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) y [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) se publiquen y los miembros de datos [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), y [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) se establecen en FALSE.

Consulte [IOleObject::Close](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-close) en el SDK de Windows.

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

Indica al control que realice una de las acciones enumeradas.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>Comentarios

Dependiendo del valor de `iVerb`, uno de la biblioteca ATL `DoVerb` funciones auxiliares se llama como sigue:

|*iVerb* valor|Función auxiliar de DoVerb llamado|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Consulte [DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) en el SDK de Windows.

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

Indica al control para descartar cualquier estado de deshacer es de mantenimiento.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

Desactiva y quita la interfaz de usuario del control y oculta el control.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

Se ejecuta el control y su ventana se instala, pero no instala la interfaz de usuario del control.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Activa el control en su lugar mediante una llamada a [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que el miembro de datos de la clase control `m_bWindowOnly` es TRUE, `DoVerbInPlaceActivate` primero intenta activar el control como un control sin ventanas (posible únicamente si el contenedor admite [IOleInPlaceSiteWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Si se produce un error, la función intenta activar el control con características extendidas (posible únicamente si el contenedor admite [IOleInPlaceSiteEx](/windows/desktop/api/ocidl/nn-ocidl-ioleinplacesiteex)). Si se produce un error, la función intenta activar el control con ninguna característica extendido (posible únicamente si el contenedor admite [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)). Si la activación se realiza correctamente, la función notifica al contenedor que se ha activado el control.

##  <a name="doverbopen"></a>  IOleObjectImpl::DoVerbOpen

Hace que el control se puede editar para abrir en una ventana independiente.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbprimary"></a>  IOleObjectImpl::DoVerbPrimary

Define la acción realizada cuando el usuario hace doble clic en el control.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

De forma predeterminada, establecido para mostrar las páginas de propiedades. Puede invalidar esto en la clase del control para invocar un comportamiento diferente al hacer doble clic; Por ejemplo, reproducir un vídeo o visite activo en contexto.

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

Indica al contenedor para hacer visible el control.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

Activa la interfaz de usuario del control y notifica al contenedor que los menús están siendo remplazados por menús compuestos.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
[in] Puntero al rectángulo el contenedor desea dibujar en el control.

*hwndParent*<br/>
[in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="enumadvise"></a>  IOleObjectImpl::EnumAdvise

Proporciona una enumeración de las conexiones de consulta registradas para este control.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::EnumAdvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumadvise) en el SDK de Windows.

##  <a name="enumverbs"></a>  IOleObjectImpl::EnumVerbs

Proporciona una enumeración de las acciones registradas (verbos) para este control mediante una llamada a `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Comentarios

Puede agregar verbos al archivo del proyecto. Por ejemplo, vea CIRCCTL. Grupos de recursos en el [CIRC](../../visual-cpp-samples.md) ejemplo.

Consulte [IOleObject:: EnumVerbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs) en el SDK de Windows.

##  <a name="getclientsite"></a>  IOleObjectImpl::GetClientSite

Coloca el puntero en el miembro de datos de la clase de control [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* e incrementa el recuento de referencias del puntero.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::GetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclientsite) en el SDK de Windows.

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

Recupera los datos desde el Portapapeles.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::GetClipboardData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) en el SDK de Windows.

##  <a name="getextent"></a>  IOleObjectImpl::GetExtent

Recupera el tamaño de presentación de un control que se ejecuta en unidades HIMETRIC (0,01 milímetro por unidad).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Comentarios

El tamaño se almacena en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Consulte [IOleObject::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getextent) en el SDK de Windows.

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

Devuelve un puntero a la información de estado registrados para el control mediante una llamada a `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Comentarios

La información de estado incluye comportamientos compatibles con el control y la presentación de datos. Puede agregar información de estado para el archivo del proyecto .rgs.

Consulte [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) en el SDK de Windows.

##  <a name="getmoniker"></a>  IOleObjectImpl::GetMoniker

Recupera el moniker del control.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::GetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmoniker) en el SDK de Windows.

##  <a name="getuserclassid"></a>  IOleObjectImpl::GetUserClassID

Devuelve el identificador de clase del control.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::GetUserClassID](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getuserclassid) en el SDK de Windows.

##  <a name="getusertype"></a>  IOleObjectImpl::GetUserType

Devuelve el nombre de tipo de usuario del control mediante una llamada a `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Comentarios

Se usa el nombre del tipo de usuario para su presentación en elementos de interfaces de usuario como menús y cuadros de diálogo. Puede cambiar el nombre de tipo de usuario en el archivo del proyecto .rgs.

Consulte [IOleObject::GetUserType](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getusertype) en el SDK de Windows.

##  <a name="initfromdata"></a>  IOleObjectImpl::InitFromData

Inicializa el control de datos seleccionado.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject:: InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el SDK de Windows.

##  <a name="isuptodate"></a>  IOleObjectImpl::IsUpToDate

Comprueba si el control está actualizado.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::IsUpToDate](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-isuptodate) en el SDK de Windows.

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que quiere que se ejecuta después de que se descarta el estado de deshacer.

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

Lo llama [DoVerbHide](#doverbhide) después de que el control está oculto.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que quiere que se ejecuta después de que el control está oculto.

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) después de activa el control en su lugar.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que quiere que se ejecuta después de que el control está activado en su lugar.

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

Lo llama [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que desee que se ejecuta después de que el control se ha abierto para editarlo en una ventana independiente.

##  <a name="onpostverbshow"></a>  IOleObjectImpl::OnPostVerbShow

Lo llama [DoVerbShow](#doverbshow) después de que se ha realizado el control visible.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que desee que se ejecuta después de que se ha realizado el control visible.

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

Lo llama [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Invalide este método con el código que desea ejecutar después de activar la interfaz de usuario del control.

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) antes de la fase de reversión se descarta el estado.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para evitar que el estado de deshacer que se descarte, invalide este método para devolver un HRESULT de error.

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

Lo llama [DoVerbHide](#doverbhide) antes de que el control está oculto.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para impedir que se va a ocultar el control, invalide este método para devolver un HRESULT de error.

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control está activado en su lugar.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para evitar que el control está activado en su lugar, invalide este método para devolver un HRESULT de error.

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

Lo llama [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para editarlo en una ventana independiente.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para evitar que el control que se va a abrir para editarlo en una ventana independiente, invalide este método para devolver un HRESULT de error.

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

Lo llama [DoVerbShow](#doverbshow) antes de que se ha realizado el control visible.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para evitar que el control esté visible, invalide este método para devolver un HRESULT de error.

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

Lo llama [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Para evitar que la interfaz de usuario del control que se está activando, invalide este método para devolver un HRESULT de error.

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

Indica al control sobre su sitio de cliente en el contenedor.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Comentarios

El método devuelve S_OK.

Consulte [:: SetClientSite](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setclientsite) en el SDK de Windows.

##  <a name="setcolorscheme"></a>  IOleObjectImpl::SetColorScheme

Se recomienda una combinación de colores para la aplicación del control, si existe.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el SDK de Windows.

##  <a name="setextent"></a>  IOleObjectImpl::SetExtent

Establece la magnitud del área de visualización del control.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Comentarios

En caso contrario, `SetExtent` almacena el valor señalado por `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Este valor está en unidades HIMETRIC (0,01 milímetro por unidad).

Si el control de clase de miembro de datos [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) es TRUE, `SetExtent` también almacena el valor señalado por `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeNatural ](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si el control de clase de miembro de datos [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) es TRUE, `SetExtent` llamadas `SendOnDataChange` y `SendOnViewChange` para notificar a los receptores de todas las consultas registrados con el titular de la consulta que tiene el tamaño de control puede cambiar.

Consulte [IOleObject:: SetExtent](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setextent) en el SDK de Windows.

##  <a name="sethostnames"></a>  IOleObjectImpl::SetHostNames

Indica que el control a los nombres de la aplicación de contenedor y el documento contenedor.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::SetHostNames](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-sethostnames) en el SDK de Windows.

##  <a name="setmoniker"></a>  IOleObjectImpl::SetMoniker

Indica al control ¿cuál es su moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::SetMoniker](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setmoniker) en el SDK de Windows.

##  <a name="unadvise"></a>  IOleObjectImpl::Unadvise

Elimina la conexión de consulta almacenada en la clase control `m_spOleAdviseHolder` miembro de datos.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::Unadvise](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-unadvise) en el SDK de Windows.

##  <a name="update"></a>  IOleObjectImpl::Update

Actualiza el control.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IOleObject::Update](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-update) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
