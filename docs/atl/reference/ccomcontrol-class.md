---
title: Clase CComControl
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
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320765"
---
# <a name="ccomcontrol-class"></a>Clase CComControl

Esta clase proporciona métodos para crear y administrar controles ATL.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que implementa el control.

*WinBase*<br/>
La clase base que implementa funciones de ventanas. El valor predeterminado es [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crea una ventana para el control.|
|[CComControl::FireOnChanged](#fireonchanged)|Notifica al receptor del contenedor que ha cambiado una propiedad de control.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar y que el objeto está preguntando al receptor cómo proceder.|
|[CComControl::MessageBox](#messagebox)|Llame a este método para crear, mostrar y operar un cuadro de mensaje.|

## <a name="remarks"></a>Observaciones

`CComControl`es un conjunto de funciones auxiliares de control útiles y miembros de datos esenciales para los controles ATL. Al crear un control estándar o un control DHTML mediante el Asistente para `CComControl`controles ATL, el asistente derivará automáticamente la clase de . `CComControl`deriva la mayoría de sus métodos de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Para obtener más información sobre la creación de un control, vea el Tutorial de [ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

Para obtener `CComControl` una demostración de métodos y miembros de datos, vea el [ejemplo CIRC.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CComControl::CComControl

El constructor.

```
CComControl();
```

### <a name="remarks"></a>Observaciones

Llama al constructor [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) y pasa el `m_hWnd` miembro de datos heredado a través de [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Recupera un puntero a la interfaz solicitada.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*Ppv*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="remarks"></a>Observaciones

Solo controla las interfaces de la tabla de mapas COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComControl::CreateControlWindow

De forma predeterminada, crea una `CWindowImpl::Create`ventana para el control llamando a .

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[en] Controle la ventana principal o propietaria. Se debe proporcionar un identificador de ventana válido. La ventana de control se limita al área de su ventana primaria.

*rcPos*<br/>
[en] El tamaño inicial y la posición de la ventana que se va a crear.

### <a name="remarks"></a>Observaciones

Invalide este método si desea hacer algo distinto de crear una sola ventana, por ejemplo, para crear dos ventanas, una de las cuales se convierte en una barra de herramientas para el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl::FireOnChanged

Notifica al receptor del contenedor que ha cambiado una propiedad de control.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
[en] Identificador de la propiedad que ha cambiado.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si la clase de control deriva de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), este método llama a `IPropertyNotifySink` [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) para notificar a todas las interfaces conectadas que la propiedad de control especificada ha cambiado. Si la clase de `IPropertyNotifySink`control no deriva de , este método devuelve S_OK.

Este método es seguro llamar incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar y que el objeto está preguntando al receptor cómo proceder.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
[en] Identificador de la propiedad a punto de cambiar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si la clase de control deriva de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), este método llama a [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) para notificar a todas las interfaces conectadas `IPropertyNotifySink` que la propiedad de control especificada está a punto de cambiar. Si la clase de `IPropertyNotifySink`control no deriva de , este método devuelve S_OK.

Este método es seguro llamar incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl::MessageBox

Llame a este método para crear, mostrar y operar un cuadro de mensaje.

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
El título del cuadro de diálogo. Si NULL (valor predeterminado), se utiliza el título "Error".

*nType*<br/>
Especifica el contenido y el comportamiento del cuadro de diálogo. Consulte la entrada [de cuadro](/windows/win32/api/winuser/nf-winuser-messagebox) de mensajes en la documentación de Windows SDK para obtener una lista de los diferentes cuadros de mensaje disponibles. El valor predeterminado proporciona un botón **Aceptar** simple.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor entero que especifica uno de los valores de elemento de menú enumerados en [cuadro](/windows/win32/api/winuser/nf-winuser-messagebox) de mensajes en la documentación de Windows SDK.

### <a name="remarks"></a>Observaciones

`MessageBox`es útil tanto durante el desarrollo como como una manera fácil de mostrar un mensaje de error o advertencia al usuario.

## <a name="see-also"></a>Consulte también

[Clase CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Clase CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
