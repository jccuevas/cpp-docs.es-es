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
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862943"
---
# <a name="ioleobjectimpl-class"></a>Clase IOleObjectImpl

Esta clase implementa `IUnknown` y es la interfaz principal a través de la cual un contenedor se comunica con un control.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IOleObjectImpl`.

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleObjectImpl:: Advise](#advise)|Establece una conexión de consulta con el control.|
|[IOleObjectImpl:: Close](#close)|Cambia el estado del control de Running a Loaded.|
|[IOleObjectImpl::D oVerb](#doverb)|Indica al control que realice una de sus acciones enumeradas.|
|[IOleObjectImpl::D oVerbDiscardUndo](#doverbdiscardundo)|Indica al control que descarte cualquier estado de deshacer que está manteniendo.|
|[IOleObjectImpl::D oVerbHide](#doverbhide)|Indica al control que quite su interfaz de usuario de la vista.|
|[IOleObjectImpl::D oVerbInPlaceActivate](#doverbinplaceactivate)|Ejecuta el control e instala su ventana, pero no instala la interfaz de usuario del control.|
|[IOleObjectImpl::D oVerbOpen](#doverbopen)|Hace que el control esté abierto y editado en una ventana independiente.|
|[IOleObjectImpl::D oVerbPrimary](#doverbprimary)|Realiza la acción especificada cuando el usuario hace doble clic en el control. El control define la acción, normalmente para activar el control en contexto.|
|[IOleObjectImpl::D oVerbShow](#doverbshow)|Muestra un control recién insertado al usuario.|
|[IOleObjectImpl::D oVerbUIActivate](#doverbuiactivate)|Activa el control en contexto y muestra la interfaz de usuario del control, como los menús y las barras de herramientas.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera las conexiones de consulta del control.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera las acciones del control.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera el sitio del cliente del control.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera los datos del portapapeles. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetExtent](#getextent)|Recupera la extensión del área de presentación del control.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera el estado del control.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera el moniker del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera el identificador de clase del control.|
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera el nombre del tipo de usuario del control.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa el control a partir de los datos seleccionados. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Comprueba si el control está actualizado. La implementación de ATL Devuelve S_OK.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) después de descartar el estado de la operación de deshacer.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Llamado por [DoVerbHide](#doverbhide) una vez oculto el control.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) una vez que se activa el control en contexto.|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Lo llama [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Lo llama [DoVerbShow](#doverbshow) una vez que se ha hecho visible el control.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Llamado por [DoVerbUIActivate](#doverbuiactivate) una vez activada la interfaz de usuario del control.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de que se descarte el estado de deshacer.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Lo llama [DoVerbHide](#doverbhide) antes de que se oculte el control.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que se active el control en contexto.|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Lo llama [DoVerbOpen](#doverbopen) antes de que el control se haya abierto para editarlo en una ventana independiente.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Lo llama [DoVerbShow](#doverbshow) antes de que se haya hecho visible el control.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Lo llama [DoVerbUIActivate](#doverbuiactivate) antes de que se haya activado la interfaz de usuario del control.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indica al control sobre su sitio de cliente en el contenedor.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recomienda una combinación de colores para la aplicación del control, si la hay. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl:: SetExtent](#setextent)|Establece la extensión del área de presentación del control.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indica al control los nombres de la aplicación contenedora y del documento contenedor.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indica al control cuál es su moniker. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleObjectImpl:: unaconseje](#unadvise)|Elimina una conexión de consulta con el control.|
|[IOleObjectImpl:: Update](#update)|Actualiza el control. La implementación de ATL Devuelve S_OK.|

## <a name="remarks"></a>Observaciones

La interfaz [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject) es la interfaz principal a través de la cual un contenedor se comunica con un control. La clase `IOleObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="advise"></a>IOleObjectImpl:: Advise

Establece una conexión de consulta con el control.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) en el Windows SDK.

##  <a name="close"></a>IOleObjectImpl:: Close

Cambia el estado del control de Running a Loaded.

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Observaciones

Desactiva el control y destruye la ventana de control si existe. Si el miembro de datos de la clase de control [CComControlBase:: m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) es true y el parámetro *dwSaveOption* es OLECLOSE_SAVEIFDIRTY o OLECLOSE_PROMPTSAVE, las propiedades del control se guardan antes de cerrarse.

Los punteros mantenidos en los miembros de datos de la clase de control [CComControlBase:: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) y [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) se liberan, y los miembros de datos [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase:: m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)y [CComControlBase:: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) se establecen en false.

Vea [IOleObject:: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) en el Windows SDK.

##  <a name="doverb"></a>IOleObjectImpl::D oVerb

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

Dependiendo del valor de `iVerb`, una de las funciones auxiliares de `DoVerb` ATL se denomina de la siguiente manera:

|*iVerb* Valor|Función auxiliar Doverb denominada|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::D oVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Vea [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

##  <a name="doverbdiscardundo"></a>IOleObjectImpl::D oVerbDiscardUndo

Indica al control que descarte cualquier estado de deshacer que está manteniendo.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbhide"></a>IOleObjectImpl::D oVerbHide

Desactiva y quita la interfaz de usuario del control y oculta el control.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::D oVerbInPlaceActivate

Ejecuta el control e instala su ventana, pero no instala la interfaz de usuario del control.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Activa el control en contexto mediante una llamada a [CComControlBase:: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que el miembro de datos de la clase de control `m_bWindowOnly` sea TRUE, `DoVerbInPlaceActivate` primero intenta activar el control como un control sin ventana (solo es posible si el contenedor admite [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)). Si se produce un error, la función intenta activar el control con características extendidas (posible únicamente si el contenedor admite [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)). Si se produce un error, la función intenta activar el control sin características extendidas (solo es posible si el contenedor admite [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)). Si la activación se realiza correctamente, la función notifica al contenedor que se ha activado el control.

##  <a name="doverbopen"></a>IOleObjectImpl::D oVerbOpen

Hace que el control esté abierto y editado en una ventana independiente.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

##  <a name="doverbprimary"></a>IOleObjectImpl::D oVerbPrimary

Define la acción que se realiza cuando el usuario hace doble clic en el control.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

De forma predeterminada, se establece para mostrar las páginas de propiedades. Puede invalidar esto en la clase de control para invocar un comportamiento diferente al hacer doble clic; por ejemplo, reproduzca un vídeo o vaya activo.

##  <a name="doverbshow"></a>IOleObjectImpl::D oVerbShow

Indica al contenedor que haga que el control sea visible.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="doverbuiactivate"></a>IOleObjectImpl::D oVerbUIActivate

Activa la interfaz de usuario del control y notifica al contenedor que sus menús se van a reemplazar por menús compuestos.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parámetros

*prcPosRec*<br/>
de Puntero al rectángulo en el que el contenedor desea dibujar el control.

*hwndParent*<br/>
de Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Proporciona una enumeración de conexiones de consulta registradas para este control.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) en el Windows SDK.

##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Proporciona una enumeración de acciones registradas (verbos) para este control llamando a `OleRegEnumVerbs`.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Observaciones

Puede Agregar verbos al archivo. RGS del proyecto. Por ejemplo, vea CIRCCTL. RGS en el ejemplo [Circ](../../overview/visual-cpp-samples.md) .

Vea [IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) en el Windows SDK.

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Coloca el puntero en el miembro de datos de la clase de control [CComControlBase:: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* e incrementa el recuento de referencias en el puntero.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) en el Windows SDK.

##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Recupera los datos del portapapeles.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) en el Windows SDK.

##  <a name="getextent"></a>IOleObjectImpl::GetExtent

Recupera el tamaño de presentación de un control en ejecución en unidades HIMETRIC (0,01 milímetro por unidad).

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Observaciones

El tamaño se almacena en el miembro de datos de la clase de control [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

Vea [IOleObject:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) en el Windows SDK.

##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Devuelve un puntero a la información de estado registrada para el control mediante una llamada a `OleRegGetMiscStatus`.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Observaciones

La información de estado incluye los comportamientos que admiten los datos de presentación y de control. Puede agregar información de estado al archivo. RGS del proyecto.

Vea [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) en el Windows SDK.

##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Recupera el moniker del control.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) en el Windows SDK.

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Devuelve el identificador de clase del control.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) en el Windows SDK.

##  <a name="getusertype"></a>IOleObjectImpl::GetUserType

Devuelve el nombre de tipo de usuario del control mediante una llamada a `OleRegGetUserType`.

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Observaciones

El nombre de tipo de usuario se usa para la presentación en elementos de interfaz de usuario como menús y cuadros de diálogo. Puede cambiar el nombre del tipo de usuario en el archivo. RGS del proyecto.

Vea [IOleObject:: GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) en el Windows SDK.

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

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

Vea [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) en el Windows SDK.

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

Comprueba si el control está actualizado.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) en el Windows SDK.

##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Lo llama [DoVerbDiscardUndo](#doverbdiscardundo) después de descartar el estado de la operación de deshacer.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de descartar el estado de deshacer.

##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Llamado por [DoVerbHide](#doverbhide) una vez oculto el control.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que se oculte el control.

##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) una vez que se activa el control en contexto.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de activar el control en contexto.

##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen

Lo llama [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que el control se haya abierto para editarlo en una ventana independiente.

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Lo llama [DoVerbShow](#doverbshow) una vez que se ha hecho visible el control.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que se haya hecho visible el control.

##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Llamado por [DoVerbUIActivate](#doverbuiactivate) una vez activada la interfaz de usuario del control.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Invalide este método con el código que desea ejecutar después de que se haya activado la interfaz de usuario del control.

##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Llamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de que se descarte el estado de deshacer.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que se descarte el estado de deshacer, Invalide este método para devolver un error HRESULT.

##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Lo llama [DoVerbHide](#doverbhide) antes de que se oculte el control.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que se oculte el control, Invalide este método para devolver un error HRESULT.

##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Lo llama [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que se active el control en contexto.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se active en su lugar, Invalide este método para devolver un error HRESULT.

##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen

Lo llama [DoVerbOpen](#doverbopen) antes de que el control se haya abierto para editarlo en una ventana independiente.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se abra para su edición en una ventana independiente, Invalide este método para devolver un error HRESULT.

##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Lo llama [DoVerbShow](#doverbshow) antes de que se haya hecho visible el control.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que el control se haga visible, Invalide este método para devolver un error HRESULT.

##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Lo llama [DoVerbUIActivate](#doverbuiactivate) antes de que se haya activado la interfaz de usuario del control.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Para evitar que la interfaz de usuario del control se active, Invalide este método para devolver un error HRESULT.

##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Indica al control sobre su sitio de cliente en el contenedor.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Observaciones

Después, el método devuelve S_OK.

Vea [IOleObject:: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) en el Windows SDK.

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Recomienda una combinación de colores para la aplicación del control, si la hay.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) en el Windows SDK.

##  <a name="setextent"></a>IOleObjectImpl:: SetExtent

Establece la extensión del área de presentación del control.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Observaciones

De lo contrario, `SetExtent` almacena el valor al que apunta `psizel` en el miembro de datos de la clase de control [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Este valor se encuentra en unidades HIMETRIC (0,01 milímetro por unidad).

Si el miembro de datos de la clase de control [CComControlBase:: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) es TRUE, `SetExtent` también almacena el valor al que apunta `psizel` en el miembro de datos de la clase de control [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).

Si el miembro de datos de la clase de control [CComControlBase:: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) es TRUE, `SetExtent` llama a `SendOnDataChange` y `SendOnViewChange` para notificar a todos los receptores de consulta registrados con el titular de la notificación de que el tamaño del control ha cambiado.

Consulte [IOleObject:: SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) en el Windows SDK.

##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Indica al control los nombres de la aplicación contenedora y del documento contenedor.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) en el Windows SDK.

##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Indica al control cuál es su moniker.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) en el Windows SDK.

##  <a name="unadvise"></a>IOleObjectImpl:: unaconseje

Elimina la conexión de consulta almacenada en el miembro de datos `m_spOleAdviseHolder` de la clase de control.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: unvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) en el Windows SDK.

##  <a name="update"></a>IOleObjectImpl:: Update

Actualiza el control.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleObject:: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
