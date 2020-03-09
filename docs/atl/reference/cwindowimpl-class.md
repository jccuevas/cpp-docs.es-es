---
title: CWindowImpl (clase)
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
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862985"
---
# <a name="cwindowimpl-class"></a>CWindowImpl (clase)

Proporciona métodos para crear una ventana o subclases de una ventana.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

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
Una [clase traits](../../atl/understanding-window-traits.md) que define estilos para la ventana. El valor predeterminado es `CControlWinTraits`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWindowImpl:: Create](#create)|Crea una ventana.|

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
|[GetWndClassInfo](#getwndclassinfo)|Devuelve una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), que administra la información de la clase de ventana.|
|[WindowProc](#windowproc)|Procesa los mensajes enviados a la ventana.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|

## <a name="remarks"></a>Comentarios

Puede usar `CWindowImpl` para crear una ventana o una subclase de una ventana existente. el procedimiento `CWindowImpl` ventana utiliza un mapa de mensajes para dirigir los mensajes a los controladores adecuados.

`CWindowImpl::Create` crea una ventana basada en la información de la clase de ventana administrada por [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` contiene la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , lo que significa que `CWndClassInfo` registra una nueva clase de ventana. Si desea superclase una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza `CWindowImpl::WindowProc`. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Dado que `CWndClassInfo` administra la información solo para una clase de ventana, cada ventana creada con una instancia de `CWindowImpl` se basa en la misma clase de ventana.

`CWindowImpl` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CWindowImpl` y cambia el procedimiento de ventana a `CWindowImpl::WindowProc`. Cada instancia de `CWindowImpl` puede crear subclases de una ventana diferente.

> [!NOTE]
>  Para cualquier objeto de `CWindowImpl` determinado, llame a `Create` o `SubclassWindow`. No invoque ambos métodos en el mismo objeto.

Además de `CWindowImpl`, ATL proporciona [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) para crear una ventana contenida en otro objeto.

El destructor de clase base (~ `CWindowImplRoot`) garantiza que la ventana ha desaparecido antes de que se destruya el objeto.

`CWindowImpl` deriva de `CWindowImplBaseT`, que deriva de `CWindowImplRoot`, que deriva de `TBase` y [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Para obtener más información sobre|Consulte|
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

**Encabezado:** atlwin. h

##  <a name="create"></a>CWindowImpl:: Create

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
de Identificador de la ventana primaria o propietaria.

*Rect*<br/>
de Estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que especifica la posición de la ventana. El `RECT` se puede pasar por puntero o por referencia.

*szWindowName*<br/>
de Especifica el nombre de la ventana. El valor predeterminado es NULL.

*dwStyle*<br/>
de Estilo de la ventana. Este valor se combina con el estilo proporcionado por la clase traits para la ventana. El valor predeterminado proporciona a la clase traits control total sobre el estilo. Para obtener una lista de los valores posibles, vea [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*dwExStyle*<br/>
de Estilo de ventana extendido. Este valor se combina con el estilo proporcionado por la clase traits para la ventana. El valor predeterminado proporciona a la clase traits control total sobre el estilo. Para obtener una lista de los valores posibles, vea [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*MenuOrID*<br/>
de Para una ventana secundaria, el identificador de la ventana. En el caso de una ventana de nivel superior, un identificador de menú para la ventana. El valor predeterminado es **0U**.

*lpCreateParam*<br/>
de Puntero a los datos de creación de ventanas. Para obtener una descripción completa, vea la descripción del parámetro final en [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador de la ventana recién creada. En caso contrario, NULL.

### <a name="remarks"></a>Comentarios

`Create` registra primero la clase de ventana si aún no se ha registrado. La ventana recién creada se adjunta automáticamente al objeto `CWindowImpl`.

> [!NOTE]
>  No llame a `Create` si ya ha llamado a [SubclassWindow](#subclasswindow).

Para usar una clase de ventana basada en una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . El procedimiento de ventana de la clase de ventana existente se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Para obtener más información, vea la información general sobre [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

> [!NOTE]
>  Si se usa 0 como valor del parámetro *MenuOrID* , debe especificarse como 0U (el valor predeterminado) para evitar un error del compilador.

##  <a name="defwindowproc"></a>CWindowImpl::D efWindowProc

Lo llama [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parámetros

*uMsg*<br/>
de El mensaje enviado a la ventana.

*wParam*<br/>
de Información adicional específica del mensaje.

*lParam*<br/>
de Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

Resultado del procesamiento del mensaje.

### <a name="remarks"></a>Comentarios

De forma predeterminada, `DefWindowProc` llama a la función [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) de Win32 para enviar la información del mensaje al procedimiento de ventana especificado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

La función sin parámetros recupera automáticamente los parámetros necesarios del mensaje actual.

##  <a name="getcurrentmessage"></a>CWindowImpl:: GetCurrentMessage

Devuelve el mensaje actual, empaquetado en la estructura de `MSG`.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valor devuelto

Mensaje actual.

##  <a name="getwindowproc"></a>CWindowImpl:: GetWindowProc

Devuelve `WindowProc`, el procedimiento de ventana actual.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Valor devuelto

El procedimiento de ventana actual.

### <a name="remarks"></a>Comentarios

Invalide este método para reemplazar el procedimiento de ventana por el suyo propio.

##  <a name="getwndclassinfo"></a>CWindowImpl:: GetWndClassInfo

Llamado por [Create](#create) para tener acceso a la información de la clase de ventana.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Valor devuelto

Una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Comentarios

De forma predeterminada, `CWindowImpl` obtiene este método a través de la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , que especifica una nueva clase de ventana.

Para superponer una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) para invalidar `GetWndClassInfo`. Para obtener más información, vea la información general sobre [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

Además de usar las macros DECLARE_WND_CLASS y DECLARE_WND_SUPERCLASS, puede invalidar `GetWndClassInfo` con su propia implementación.

##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl:: m_pfnSuperWindowProc

Dependiendo de la ventana, señala a uno de los siguientes procedimientos de ventana.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Comentarios

|Tipo de ventana|Procedimiento de ventana|
|--------------------|----------------------|
|Ventana basada en una nueva clase de ventana, que se especifica mediante la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) .|La función [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) de Win32.|
|Ventana basada en una clase de ventana que modifica una clase existente, especificada mediante la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) .|El procedimiento de ventana de la clase de ventana existente.|
|Ventana de subclase.|El procedimiento de ventana original de la ventana con subclases.|

[CWindowImpl::D efwindowproc](#defwindowproc) envía información del mensaje al procedimiento de ventana guardado en `m_pfnSuperWindowProc`.

##  <a name="onfinalmessage"></a>CWindowImpl:: OnFinalMessage

Se llama después de recibir el último mensaje (normalmente WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
de Identificador de la ventana que se va a destruir.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de `OnFinalMessage` no hace nada, pero puede invalidar esta función para controlar la limpieza antes de destruir una ventana. Si desea eliminar automáticamente el objeto en el momento de la destrucción de la ventana, puede llamar a **Delete this;** en esta función.

##  <a name="subclasswindow"></a>CWindowImpl:: SubclassWindow

Subclase la ventana identificada por *hWnd* y la adjunta al objeto `CWindowImpl`.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
de Identificador de la ventana de la que se van a subclases.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se ha subclase correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La ventana subclase usa ahora [CWindowImpl:: WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado a [Create](#create).

##  <a name="unsubclasswindow"></a>CWindowImpl:: UnsubclassWindow

Desasocia la ventana de subclase del objeto `CWindowImpl` y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Valor devuelto

Identificador de la ventana con la subclase anterior.

##  <a name="windowproc"></a>CWindowImpl:: WindowProc

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
de Identificador de la ventana.

*uMsg*<br/>
de El mensaje enviado a la ventana.

*wParam*<br/>
de Información adicional específica del mensaje.

*lParam*<br/>
de Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

Resultado del procesamiento del mensaje.

### <a name="remarks"></a>Comentarios

`WindowProc` usa el mapa de mensajes predeterminado (declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) para dirigir los mensajes a los controladores adecuados. Si es necesario, `WindowProc` llama a [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicional. Si no se controla el mensaje final, `WindowProc` hace lo siguiente:

- Realiza unsubclassing si la ventana era unsubclassed.

- Borra `m_hWnd`.

- Llama a [OnFinalMessage](#onfinalmessage) antes de que se destruya la ventana.

Puede invalidar `WindowProc` para proporcionar un mecanismo diferente para controlar los mensajes.

## <a name="see-also"></a>Vea también

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
