---
title: CComControl (clase)
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: ffbec7c1a83c0dd829878f4c73340528d32fb852
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246504"
---
# <a name="ccomcontrol-class"></a>CComControl (clase)

Esta clase proporciona métodos para crear y administrar los controles ATL.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase de implementación del control.

*WinBase*<br/>
La clase base que implementa las funciones de ventana. El valor predeterminado es [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crea una ventana para el control.|
|[CComControl::FireOnChanged](#fireonchanged)|Notifica a los receptores del contenedor que ha cambiado una propiedad de control.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifica a los receptores del contenedor que una propiedad de control se va a cambiar y que el objeto está solicitando el receptor cómo proceder.|
|[CComControl::MessageBox](#messagebox)|Llame a este método para crear, mostrar y trabajar con un cuadro de mensaje.|

## <a name="remarks"></a>Comentarios

`CComControl` es un conjunto de funciones auxiliares de control útil y miembros de datos esenciales para controles ATL. Cuando se crea un control estándar o un control DHTML mediante el Asistente para controles ATL, el asistente automáticamente derivará la clase de `CComControl`. `CComControl` se deriva la mayoría de los métodos de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Para obtener más información acerca de cómo crear un control, vea el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

Para ver una demostración de `CComControl` métodos y miembros de datos, vea el [CIRC](../../overview/visual-cpp-samples.md) ejemplo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

El constructor.

```
CComControl();
```

### <a name="remarks"></a>Comentarios

Las llamadas del [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) constructor, pasando el `m_hWnd` hereda el miembro de datos a través de [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Recupera un puntero a la interfaz solicitada.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
[in] El GUID de la interfaz que se solicita.

*ppv*<br/>
[out] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="remarks"></a>Comentarios

solo administra interfaces de la tabla de asignación COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

De forma predeterminada, crea una ventana para el control mediante una llamada a `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[in] Identificador de la ventana principal o propietaria. Debe proporcionar un identificador de ventana válido. La ventana de control se limita al área de su ventana primaria.

*rcPos*<br/>
[in] El tamaño inicial y la posición de la ventana para crearse.

### <a name="remarks"></a>Comentarios

Invalide este método si desea hacer algo distinto de crear una sola ventana, por ejemplo, para crear dos ventanas, uno de los cuales se convierte en una barra de herramientas para el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Notifica a los receptores del contenedor que ha cambiado una propiedad de control.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
[in] Identificador de la propiedad que ha cambiado.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la clase del control se deriva de [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), este método llama a [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) notificar a todos conectados `IPropertyNotifySink` interfaces que el control especificado propiedad ha cambiado. Si la clase del control no se deriva de `IPropertyNotifySink`, este método devuelve S_OK.

Este método es seguro llamar a incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Notifica a los receptores del contenedor que una propiedad de control se va a cambiar y que el objeto está solicitando el receptor cómo proceder.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
[in] Identificador de la propiedad que se va a cambiar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la clase del control se deriva de [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), llama este método [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) notificar a todos conectados `IPropertyNotifySink` interfaces que el especificado propiedad de control que se va a cambiar. Si la clase del control no se deriva de `IPropertyNotifySink`, este método devuelve S_OK.

Este método es seguro llamar a incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Llame a este método para crear, mostrar y trabajar con un cuadro de mensaje.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
El texto que se mostrará en el cuadro de mensaje.

*lpszCaption*<br/>
El título del cuadro de diálogo. Si es NULL (valor predeterminado), el título que se usa "Error".

*nType*<br/>
Especifica el contenido y el comportamiento del cuadro de diálogo. Consulte la [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) entrada en la documentación del SDK de Windows para obtener una lista de los cuadros de mensajes distintos disponibles. El valor predeterminado proporciona un sencillo **Aceptar** botón.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor entero que especifica uno de los valores de elemento de menú que aparece bajo [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) en la documentación del SDK de Windows.

### <a name="remarks"></a>Comentarios

`MessageBox` es útil durante el desarrollo y una manera sencilla de mostrar un mensaje de advertencia o error al usuario.

## <a name="see-also"></a>Vea también

[CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComControlBase (clase)](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl (clase)](../../atl/reference/ccomcompositecontrol-class.md)
