---
title: Clase IOleInPlaceActiveObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326583"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Clase IOleInPlaceActiveObjectImpl

Esta clase proporciona métodos para ayudar a la comunicación entre un control en el lugar y su contenedor.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IOleInPlaceActiveObjectImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la ayuda contextual. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Habilita los cuadros de diálogo no quedes. La implementación de ATL devuelve S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Notifica al control cuando se activa o desactiva la ventana de documento del contenedor. La implementación de ATL devuelve S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Notifica al control cuando se activa o desactiva la ventana de marco de nivel superior del contenedor. La implementación de ATL devuelve|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informa al control que necesita para cambiar el tamaño de sus bordes. La implementación de ATL devuelve S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Procesa los mensajes de clave del acelerador de menús desde el contenedor. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

La interfaz [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) ayuda a la comunicación entre un control en el lugar y su contenedor; por ejemplo, comunicar el estado activo del control y el contenedor, e informar al control que necesita para cambiar su tamaño. Clase `IOleInPlaceActiveObjectImpl` proporciona una `IOleInPlaceActiveObject` implementación `IUnknown` predeterminada y admite el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Habilita la ayuda contextual.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless

Habilita los cuadros de diálogo no quedes.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow

El contenedor llama a esta función para obtener el identificador de ventana del control.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Observaciones

Algunos contenedores no funcionarán con un control que no ha sido windows, incluso si está actualmente en la ventana. En la implementación de `CComControl::m_bWasOnceWindowless` ATL, si el miembro de datos es TRUE, la función devuelve E_FAIL. De lo \* contrario, si *phwnd* no es NULL, `GetWindow` asigna *phwnd* al miembro `m_hWnd` de datos de la clase de control y devuelve S_OK.

Consulte [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Notifica al control cuando se activa o desactiva la ventana de documento del contenedor.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Notifica al control cuando se activa o desactiva la ventana de marco de nivel superior del contenedor.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder

Informa al control que necesita para cambiar el tamaño de sus bordes.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) en el Windows SDK.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator

Procesa los mensajes de clave del acelerador de menús desde el contenedor.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Valor devuelto

Este método admite los valores devueltos siguientes:

S_OK si el mensaje se ha traducido correctamente.

S_FALSE si el mensaje no se ha traducido.

### <a name="remarks"></a>Observaciones

Consulte [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
