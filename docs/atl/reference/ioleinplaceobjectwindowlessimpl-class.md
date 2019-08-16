---
title: Clase IOleInPlaceObjectWindowlessImpl
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495743"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Clase IOleInPlaceObjectWindowlessImpl

Esta clase implementa `IUnknown` y proporciona métodos que permiten a un control sin ventana recibir los mensajes de ventana y participar en las operaciones de arrastrar y colocar.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la ayuda contextual. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Proporciona la `IDropTarget` interfaz para un objeto in situ activo sin ventanas que admite arrastrar y colocar. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Desactiva un control en contexto activo.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Envía un mensaje desde el contenedor a un control sin ventana activo en contexto.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Reactiva un control previamente desactivado. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indica qué parte del control en contexto está visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Desactiva y quita la interfaz de usuario que admite la activación en contexto.|

## <a name="remarks"></a>Comentarios

La interfaz [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) administra la reactivación y desactivación de los controles en contexto y determina qué parte del control debe estar visible. La interfaz [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) permite a un control sin ventana recibir los mensajes de ventana y participar en las operaciones de arrastrar y colocar. La `IOleInPlaceObjectWindowlessImpl` clase proporciona una implementación predeterminada `IOleInPlaceObject` de `IOleInPlaceObjectWindowless` e e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Devuelve E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Comentarios

Vea [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) en el Windows SDK.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Devuelve E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Comentarios

Vea [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) en el Windows SDK.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

El contenedor llama a esta función para obtener el identificador de ventana del control.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Comentarios

Algunos contenedores no funcionarán con un control que no tenga ventana, aunque esté actualmente en la ventana. En la implementación de ATL, si el miembro `m_bWasOnceWindowless` de datos de la clase de control es true, la función devuelve E_FAIL. De lo contrario, si *phwnd* no es `GetWindow` null \* , establece *phwnd* en el miembro `m_hWnd` de datos de la clase de control y Devuelve S_OK.

Vea [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) en el Windows SDK.

##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Lo llama el contenedor para desactivar un control activo en contexto.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Comentarios

Este método realiza una desactivación completa o parcial en función del estado del control. Si es necesario, se desactiva la interfaz de usuario del control y se destruye la ventana del control, si existe. Se notifica al contenedor que el control ya no está activo en contexto. Se `IOleInPlaceUIWindow` libera la interfaz utilizada por el contenedor para negociar los menús y el espacio del borde.

Vea [IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) en el Windows SDK.

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Envía un mensaje de un contenedor a un control sin ventana activo en contexto.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Comentarios

Vea [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) en el Windows SDK.

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Devuelve E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Comentarios

Vea [IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) en el Windows SDK.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Lo llama el contenedor para informar al control de que el tamaño y/o la posición han cambiado.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Comentarios

Actualiza el miembro de `m_rcPos` datos del control y la presentación del control. Solo se muestra la parte del control que forma una intersección con la región de recorte. Si la presentación de un control se recortó anteriormente pero se ha quitado el recorte, se puede llamar a esta función para volver a dibujar una vista completa del control.

Vea [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) en el Windows SDK.

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

Desactiva y quita la interfaz de usuario del control que admite la activación en contexto.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Comentarios

Establece el miembro `m_bUIActive` de datos de la clase de control en false. La implementación de ATL de esta función siempre Devuelve S_OK.

Vea [IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) en el Windows SDK.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
