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
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497530"
---
# <a name="ccomcontrol-class"></a>Clase CComControl

Esta clase proporciona métodos para crear y administrar controles ATL.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

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
La clase base que implementa las funciones de ventanas. El valor predeterminado es [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crea una ventana para el control.|
|[CComControl::FireOnChanged](#fireonchanged)|Notifica al receptor del contenedor que una propiedad de control ha cambiado.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar y que el objeto está pidiendo al receptor cómo proceder.|
|[CComControl::MessageBox](#messagebox)|Llame a este método para crear, mostrar y utilizar un cuadro de mensaje.|

## <a name="remarks"></a>Comentarios

`CComControl`es un conjunto de funciones auxiliares de control útiles y miembros de datos esenciales para controles ATL. Al crear un control estándar o un control DHTML mediante el Asistente para controles ATL, el asistente derivará automáticamente la clase de `CComControl`. `CComControl`deriva la mayoría de sus métodos de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Para obtener más información sobre la creación de un control, vea el [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md). Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

Para ver una demostración `CComControl` de los métodos y miembros de datos, vea el ejemplo [Circ](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

El constructor.

```
CComControl();
```

### <a name="remarks"></a>Comentarios

Llama al constructor [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) , pasando el `m_hWnd` miembro de datos heredado a través de [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Recupera un puntero a la interfaz solicitada.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de GUID de la interfaz que se solicita.

*ppv*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*, o null si no se encuentra la interfaz.

### <a name="remarks"></a>Comentarios

Solo controla las interfaces de la tabla de asignación COM.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

De forma predeterminada, crea una ventana para el control mediante `CWindowImpl::Create`una llamada a.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
de Identificador de la ventana primaria o propietaria. Se debe proporcionar un identificador de ventana válido. La ventana control se limita al área de su ventana primaria.

*rcPos*<br/>
de El tamaño inicial y la posición de la ventana que se va a crear.

### <a name="remarks"></a>Comentarios

Invalide este método si desea hacer algo distinto de crear una sola ventana, por ejemplo, para crear dos ventanas, una de las cuales se convierte en una barra de herramientas para el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Notifica al receptor del contenedor que una propiedad de control ha cambiado.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
de Identificador de la propiedad que ha cambiado.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la clase de control se deriva de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), este método llama a [CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) para notificar a todas las interfaces conectadas `IPropertyNotifySink` que la propiedad de control especificada ha cambiado. Si la clase de control no se deriva `IPropertyNotifySink`de, este método devuelve S_OK.

Es seguro llamar a este método incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar y que el objeto está pidiendo al receptor cómo proceder.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*dispID*<br/>
de Identificador de la propiedad que se va a cambiar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la clase de control se deriva de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), este método llama a [CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) para notificar a todas las interfaces conectadas `IPropertyNotifySink` que la propiedad de control especificada está a punto de cambiar. Si la clase de control no se deriva `IPropertyNotifySink`de, este método devuelve S_OK.

Es seguro llamar a este método incluso si el control no admite puntos de conexión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Llame a este método para crear, mostrar y utilizar un cuadro de mensaje.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Texto que se va a mostrar en el cuadro de mensaje.

*lpszCaption*<br/>
Título del cuadro de diálogo. Si es NULL (valor predeterminado), se usa el título "error".

*nType*<br/>
Especifica el contenido y el comportamiento del cuadro de diálogo. Vea la entrada [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) en la documentación de Windows SDK para obtener una lista de los diferentes cuadros de mensaje disponibles. El valor predeterminado proporciona un botón **Aceptar** sencillo.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor entero que especifica uno de los valores de elemento de menú que se muestran en [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) en la documentación de Windows SDK.

### <a name="remarks"></a>Comentarios

`MessageBox`es útil durante el desarrollo y como una manera fácil de mostrar un mensaje de error o advertencia al usuario.

## <a name="see-also"></a>Vea también

[CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CComControlBase (clase)](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl (clase)](../../atl/reference/ccomcompositecontrol-class.md)
