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
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326575"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Clase IOleInPlaceObjectWindowlessImpl

Esta clase `IUnknown` implementa y proporciona métodos que permiten a un control sin ventanas recibir mensajes de ventana y participar en operaciones de arrastrar y colocar.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IOleInPlaceObjectWindowlessImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la ayuda contextual. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Proporciona la `IDropTarget` interfaz para un objeto activo y sin ventanas en el lugar que admite arrastrar y colocar. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Desactiva un control in situ activo.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Distribuye un mensaje desde el contenedor a un control sin ventanas que está activo en el lugar.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Reactiva un control previamente desactivado. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indica qué parte del control in situ está visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Desactiva y quita la interfaz de usuario que admite la activación en contexto.|

## <a name="remarks"></a>Observaciones

El [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) interfaz administra la reactivación y desactivación de controles en contexto y determina cuánto del control debe ser visible. El [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) interfaz permite un control sin ventanas para recibir mensajes de ventana y participar en operaciones de arrastrar y colocar. Clase `IOleInPlaceObjectWindowlessImpl` proporciona una `IOleInPlaceObject` implementación predeterminada de e `IOleInPlaceObjectWindowless` implementa `IUnknown` mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Devuelve E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget

Devuelve E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleInPlaceObjectWindowless::GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow

El contenedor llama a esta función para obtener el identificador de ventana del control.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Observaciones

Algunos contenedores no funcionarán con un control que no ha sido windows, incluso si está actualmente en la ventana. En la implementación de ATL, si `m_bWasOnceWindowless` el miembro de datos de la clase de control es TRUE, la función devuelve E_FAIL. De lo contrario, si *phwnd* no `GetWindow` es NULL, establece \* `m_hWnd` *phwnd* en el miembro de datos de la clase de control y devuelve S_OK.

Consulte [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Llamado por el contenedor para desactivar un control activo en el lugar.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Observaciones

Este método realiza una desactivación total o parcial en función del estado del control. Si es necesario, se desactiva la interfaz de usuario del control y se destruye la ventana del control, si la hay. Se notifica al contenedor que el control ya no está activo en su lugar. Se `IOleInPlaceUIWindow` libera la interfaz utilizada por el contenedor para negociar los menús y el espacio de borde.

Consulte [IOleInPlaceObject::InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Distribuye un mensaje de un contenedor a un control sin ventanas que está activo en el lugar.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Observaciones

Vea [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Devuelve E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Observaciones

Consulte [IOleInPlaceObject::ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects

Llamado por el contenedor para informar al control de que su tamaño y/ o posición ha cambiado.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Observaciones

Actualiza el miembro `m_rcPos` de datos del control y la visualización del control. Solo se muestra la parte del control que interseca la región del clip. Si la pantalla de un control se recorta balaste anteriormente pero se ha eliminado el recorte, se puede llamar a esta función para volver a dibujar una vista completa del control.

Consulte [IOleInPlaceObject::SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) en el Windows SDK.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate

Desactiva y quita la interfaz de usuario del control que admite la activación en contexto.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Observaciones

Establece el miembro `m_bUIActive` de datos de la clase de control en FALSE. La implementación ATL de esta función siempre devuelve S_OK.

Consulte [IOleInPlaceObject::UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
