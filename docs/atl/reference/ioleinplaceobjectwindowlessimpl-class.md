---
title: IOleInPlaceObjectWindowlessImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd6c2ddfaef8c298696ea33537ea7bfd754330f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762614"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl (clase)

Esta clase implementa `IUnknown` y proporciona métodos que permiten un control sin ventanas para recibir los mensajes de ventana y participar en operaciones de arrastrar y colocar.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parámetros

*T*  
La clase derivada de `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la Ayuda contextual. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Proporciona el `IDropTarget` interfaz para un objeto activo en contexto que admite arrastrar y colocar. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Desactiva un control en contexto activo.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Envía un mensaje desde el contenedor a un control sin ventana que está activo en contexto.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Vuelve a activar un control desactivado anteriormente. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indica qué parte del control en el contexto está visible.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Desactiva y quita la interfaz de usuario que admite la activación en contexto.|

## <a name="remarks"></a>Comentarios

El [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject) interfaz administra la reactivación y desactivación de local controles y determina cuánto control debe estar visible. El [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) interfaz permite que un control sin ventanas para recibir los mensajes de ventana y participar en operaciones de arrastrar y colocar. Clase `IOleInPlaceObjectWindowlessImpl` proporciona una implementación predeterminada de `IOleInPlaceObject` y `IOleInPlaceObjectWindowless` e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Devuelve E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) en el SDK de Windows.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Devuelve E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleInPlaceObjectWindowless::GetDropTarget](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) en el SDK de Windows.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

El contenedor llama a esta función para obtener el identificador de ventana del control.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Comentarios

Algunos contenedores no funcionará con un control que ha sido sin ventanas, incluso si es actualmente con ventanas. En la implementación de ATL, si el miembro de datos de la clase control `m_bWasOnceWindowless` es TRUE, la función devuelve E_FAIL. De lo contrario, si *phwnd* no es NULL, `GetWindow` establece \* *phwnd* al miembro de datos de la clase control `m_hWnd` y devuelve S_OK.

Consulte [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) en el SDK de Windows.

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Lo llama el contenedor para desactivar un control activo en contexto.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Comentarios

Este método lleva a cabo una desactivación completa o parcial, según el estado del control. Si es necesario, se desactiva la interfaz de usuario del control y la ventana del control, si existe, se destruye. El contenedor se notifica que el control ya no está activo en su lugar. El `IOleInPlaceUIWindow` se libera la interfaz utilizada por el contenedor para negociar los menús y el espacio del borde.

Consulte [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) en el SDK de Windows.

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Envía un mensaje desde un contenedor a un control sin ventana que está activo en contexto.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) en el SDK de Windows.

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Devuelve E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Comentarios

Consulte [IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) en el SDK de Windows.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Lo llama el contenedor para informar al control que ha cambiado su tamaño o posición.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Comentarios

Actualiza el control `m_rcPos` miembro de datos y la presentación del control. Se muestra solo la parte del control que forma una intersección con la región de recorte. Si anteriormente se recorta la vista del control, pero se quitó el recorte, se puede llamar a esta función para volver a dibujar una vista completa del control.

Consulte [IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) en el SDK de Windows.

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

Desactiva y se quita de la interfaz de usuario del control que admite la activación en contexto.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Comentarios

Establece el miembro de datos de la clase control `m_bUIActive` en FALSE. La implementación de ATL de esta función siempre devuelve S_OK.

Consulte [IOleInPlaceObject::UIDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
