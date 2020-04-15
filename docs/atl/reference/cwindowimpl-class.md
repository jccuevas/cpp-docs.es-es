---
title: Clase CWindowImpl
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: d7f7f7363eb123181bd6e0389663810346094cba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330292"
---
# <a name="cwindowimpl-class"></a>Clase CWindowImpl

Proporciona métodos para crear una ventana o subclases de una ventana.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Nueva clase derivada de `CWindowImpl`.

*TBase*<br/>
Clase base de la clase. De forma predeterminada, la clase base es [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
Clase de [rasgos](../../atl/understanding-window-traits.md) que define estilos para la ventana. El valor predeterminado es `CControlWinTraits`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWindowImpl::Crear](#create)|Crea una ventana.|

### <a name="cwindowimplbaset-methods"></a>Métodos de CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Proporciona el procesamiento de mensajes predeterminado.|
|[GetCurrentMessage](#getcurrentmessage)|Devuelve el mensaje actual.|
|[GetWindowProc](#getwindowproc)|Devuelve el procedimiento de ventana actual.|
|[OnFinalMessage](#onfinalmessage)|Se llama después de recibir el último mensaje (normalmente WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Crea subclases de una ventana.|
|[UnsubclassWindow](#unsubclasswindow)|Restaura una ventana cuyas subclases se han creado previamente.|

### <a name="static-methods"></a>Métodos estáticos

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Devuelve una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), que administra la información de clase de ventana.|
|[WindowProc](#windowproc)|Procesa los mensajes enviados a la ventana.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|

## <a name="remarks"></a>Observaciones

Puede utilizar `CWindowImpl` para crear una ventana o subclase una ventana existente. el `CWindowImpl` procedimiento de ventana utiliza un mapa de mensajes para dirigir los mensajes a los controladores adecuados.

`CWindowImpl::Create`crea una ventana basada en la información de clase de ventana administrada por [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`contiene la [macro DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) lo que significa `CWndClassInfo` que registra una nueva clase de ventana. Si desea superclase de una clase de `CWindowImpl` ventana existente, derive la clase e incluya la [macro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza `CWindowImpl::WindowProc`. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Dado que `CWndClassInfo` administra la información solo para una clase de ventana, cada ventana creada con una instancia de `CWindowImpl` se basa en la misma clase de ventana.

`CWindowImpl` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CWindowImpl` y cambia el procedimiento de ventana a `CWindowImpl::WindowProc`. Cada instancia de `CWindowImpl` puede crear subclases de una ventana diferente.

> [!NOTE]
> Para cualquier `CWindowImpl` objeto dado, `SubclassWindow`llame a o `Create` . No invoque ambos métodos en el mismo objeto.

Además `CWindowImpl`de , ATL proporciona [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) para crear una ventana que se encuentra en otro objeto.

El destructor de `CWindowImplRoot`la clase base (-) garantiza que la ventana se haya ido antes de que se destruya el objeto.

`CWindowImpl`deriva de `CWindowImplBaseT`, que `CWindowImplRoot`deriva de , `TBase` que deriva de y [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Para más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Crear

Crea una ventana basada en una nueva clase de ventana.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
[en] El identificador de la ventana principal o propietaria.

*Rect*<br/>
[en] Estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que especifica la posición de la ventana. El `RECT` se puede pasar por puntero o por referencia.

*szWindowName*<br/>
[en] Especifica el nombre de la ventana. El valor predeterminado es NULL.

*dwStyle*<br/>
[en] El estilo de la ventana. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado proporciona a la clase de rasgos control total sobre el estilo. Para obtener una lista de valores posibles, vea [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*dwExStyle*<br/>
[en] El estilo de ventana extendida. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado proporciona a la clase de rasgos control total sobre el estilo. Para obtener una lista de valores posibles, vea [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*MenuOrID*<br/>
[en] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú para la ventana. El valor predeterminado es **0U**.

*lpCreateParam*<br/>
[en] Puntero a los datos de creación de ventanas. Para obtener una descripción completa, consulte la descripción del parámetro final en [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador de la ventana recién creada. En caso contrario, NULL.

### <a name="remarks"></a>Observaciones

`Create`primero registra la clase de ventana si aún no se ha registrado. La ventana recién creada se `CWindowImpl` adjunta automáticamente al objeto.

> [!NOTE]
> No llame `Create` si ya ha llamado a [SubclassWindow](#subclasswindow).

Para utilizar una clase de ventana que se basa `CWindowImpl` en una clase de ventana existente, derive la clase e incluya la [macro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) El procedimiento de ventana de la clase de ventana existente se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Para obtener más información, consulte la información general de [CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

> [!NOTE]
> Si se utiliza 0 como valor para el *parámetro MenuOrID,* debe especificarse como 0U (el valor predeterminado) para evitar un error del compilador.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

Llamado por [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parámetros

*uMsg*<br/>
[en] El mensaje enviado a la ventana.

*wParam*<br/>
[en] Información adicional específica del mensaje.

*lParam*<br/>
[en] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El resultado del procesamiento de mensajes.

### <a name="remarks"></a>Observaciones

De forma `DefWindowProc` predeterminada, llama a la función [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 para enviar la información del mensaje al procedimiento de ventana especificado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

La función sin parámetros recupera automáticamente los parámetros necesarios del mensaje actual.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Devuelve el mensaje actual, `MSG` empaquetado en la estructura.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valor devuelto

Mensaje actual.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Devuelve `WindowProc`, el procedimiento de ventana actual.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Valor devuelto

El procedimiento de ventana actual.

### <a name="remarks"></a>Observaciones

Invalide este método para reemplazar el procedimiento de ventana por el suyo propio.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Llamado por [Create](#create) para tener acceso a la información de la clase de ventana.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Valor devuelto

Una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Observaciones

De forma `CWindowImpl` predeterminada, obtiene este método a través de la [macro DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) que especifica una nueva clase de ventana.

Para superclase una clase de ventana `CWindowImpl` existente, derive la `GetWndClassInfo`clase e incluya la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) para invalidar . Para obtener más información, consulte la información general de [CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

Además de utilizar las macros `GetWndClassInfo` DECLARE_WND_CLASS y DECLARE_WND_SUPERCLASS, puede invalidar con su propia implementación.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

Dependiendo de la ventana, señala uno de los siguientes procedimientos de ventana.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Observaciones

|Tipo de ventana|Procedimiento de ventana|
|--------------------|----------------------|
|Una ventana basada en una nueva clase de ventana, especificada a través de la [macro DECLARE_WND_CLASS.](window-class-macros.md#declare_wnd_class)|La función [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32.|
|Una ventana basada en una clase de ventana que modifica una clase existente, especificada a través de la [macro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass)|Procedimiento de ventana de la clase de ventana existente.|
|Una ventana subclase.|Procedimiento de ventana original de la ventana subclase.|

[CWindowImpl::DefWindowProc](#defwindowproc) envía información de mensaje `m_pfnSuperWindowProc`al procedimiento de ventana guardado en .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Se llama después de recibir el último mensaje (normalmente WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] Un mango a la ventana que se está destruyendo.

### <a name="remarks"></a>Observaciones

La implementación `OnFinalMessage` predeterminada de no hace nada, pero puede invalidar esta función para controlar la limpieza antes de destruir una ventana. Si desea eliminar automáticamente el objeto tras la destrucción de la ventana, puede llamar a **delete this;** en esta función.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::SubclassWindow

Subclases de la ventana identificada por *hWnd* y la adjunta al `CWindowImpl` objeto.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] El identificador de la ventana que se va a subclases.

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana se subclase correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

La ventana subclase ahora utiliza [CWindowImpl::WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> No llame `SubclassWindow` si ya ha llamado a [Crear](#create).

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Separa la ventana subclase `CWindowImpl` del objeto y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Valor devuelto

El identificador de la ventana subclaseanteriormente.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc

Esta función estática implementa el procedimiento de ventana.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] El mango de la ventana.

*uMsg*<br/>
[en] El mensaje enviado a la ventana.

*wParam*<br/>
[en] Información adicional específica del mensaje.

*lParam*<br/>
[en] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El resultado del procesamiento de mensajes.

### <a name="remarks"></a>Observaciones

`WindowProc`utiliza el mapa de mensajes predeterminado (declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) para dirigir los mensajes a los controladores adecuados. Si es `WindowProc` necesario, llame a [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicional. Si no se controla `WindowProc` el mensaje final, haga lo siguiente:

- Realiza la subclase si la ventana no se ha subclase.

- Borra `m_hWnd`.

- Llama a [OnFinalMessage](#onfinalmessage) antes de que se destruya la ventana.

Puede invalidar `WindowProc` para proporcionar un mecanismo diferente para controlar los mensajes.

## <a name="see-also"></a>Consulte también

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
