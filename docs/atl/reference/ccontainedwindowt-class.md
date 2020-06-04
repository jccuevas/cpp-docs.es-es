---
title: Clase CContainedWindowT
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747750"
---
# <a name="ccontainedwindowt-class"></a>Clase CContainedWindowT

Esta clase implementa una ventana contenida dentro de otro objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parámetros

*TBase*<br/>
La clase base de tu nueva clase. La clase base `CWindow`predeterminada es .

*TWinTraits*<br/>
Clase de rasgos que define los estilos de la ventana. De manera predeterminada, es `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) es una `CContainedWindowT`especialización de . Si desea cambiar la clase base `CContainedWindowT` o los rasgos, utilice directamente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructor. Inicializa los miembros de datos para especificar qué mapa de mensajes procesará los mensajes de la ventana contenida.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Crea una ventana.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Proporciona el procesamiento de mensajes predeterminado.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Devuelve el mensaje actual.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Registra la clase de ventana de la ventana contenida.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Crea subclases de una ventana.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Cambia el mapa de mensajes que se utiliza para procesar los mensajes de la ventana contenida.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaura una ventana cuyas subclases se han creado previamente.|
|[CContainedWindowT::WindowProc](#windowproc)|(Estático) Procesa los mensajes enviados a la ventana contenida.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifica qué mapa de mensajes procesará los mensajes de la ventana contenida.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Especifica el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|
|[CContainedWindowT::m_pObject](#m_pobject)|Apunta al objeto contenedor.|

## <a name="remarks"></a>Observaciones

`CContainedWindowT`implementa una ventana contenida en otro objeto. `CContainedWindowT`El procedimiento de ventana 's utiliza un mapa de mensajes en el objeto contenedor para dirigir los mensajes a los controladores adecuados. Al construir `CContainedWindowT` un objeto, especifique qué mapa de mensajes se debe utilizar.

`CContainedWindowT`le permite crear una nueva ventana superclase de una clase de ventana existente. El `Create` método registra primero una clase de ventana que `CContainedWindowT::WindowProc`se basa en una clase existente pero utiliza . `Create`a continuación, crea una ventana basada en esta nueva clase de ventana. Cada instancia `CContainedWindowT` de puede superclase una clase de ventana diferente.

`CContainedWindowT` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CContainedWindowT` y cambia el procedimiento de ventana a `CContainedWindowT::WindowProc`. Cada instancia de `CContainedWindowT` puede crear subclases de una ventana diferente.

> [!NOTE]
> Para cualquier `CContainedWindowT` objeto dado, `SubclassWindow`llame a o `Create` . No debe invocar ambos métodos en el mismo objeto.

Cuando se usa la opción **Agregar control basado en** en el `CContainedWindowT` Asistente para proyectos ATL, el asistente agregará automáticamente un miembro de datos a la clase que implementa el control. En el ejemplo siguiente se muestra cómo se declara la ventana contenida:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Para más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) y temas posteriores en el Windows SDK|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

El constructor inicializa los miembros de datos.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
[en] El nombre de una clase de ventana existente en la que se basará la ventana contenida.

*pObject*<br/>
[en] Puntero al objeto contenedor que declara el mapa de mensajes. La clase de este objeto debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[en] Identifica el mapa de mensajes que procesará los mensajes de la ventana contenida. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para utilizar un mapa de mensajes alternativo declarado `msgMapID`con [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)pase .

### <a name="remarks"></a>Observaciones

Si desea crear una nueva ventana a través de [Create](#create), debe pasar el nombre de una clase de ventana existente para el parámetro *lpszClassName* . Para obtener un ejemplo, vea el [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) información general.

Hay tres constructores:

- El constructor con tres argumentos es el que normalmente se llama.

- El constructor con dos argumentos `TBase::GetWndClassName`utiliza el nombre de clase de .

- El constructor sin argumentos se utiliza si desea proporcionar los argumentos más adelante. Debe proporcionar el nombre de clase de ventana, el objeto `Create`de mapa de mensajes y el identificador de mapa de mensajes cuando llame más tarde.

Si subclase una ventana existente a través de [SubclassWindow](#subclasswindow), el *lpszClassName* valor no se utilizará; por lo tanto, puede pasar NULL para este parámetro.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>CContainedWindowT::Create

Llama a [RegisterWndSuperclass](#registerwndsuperclass) para registrar una clase de ventana que se basa en una clase existente pero usa [CContainedWindowT::WindowProc](#windowproc).

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszClassName*<br/>
[en] El nombre de una clase de ventana existente en la que se basará la ventana contenida.

*pObject*<br/>
[en] Puntero al objeto contenedor que declara el mapa de mensajes. La clase de este objeto debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[en] Identifica el mapa de mensajes que procesará los mensajes de la ventana contenida. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para utilizar un mapa de mensajes alternativo declarado `msgMapID`con [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)pase .

*hWndParent*<br/>
[en] El identificador de la ventana principal o propietaria.

*Rect*<br/>
[en] Estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que especifica la posición de la ventana. El `RECT` se puede pasar por puntero o por referencia.

*szWindowName*<br/>
[en] Especifica el nombre de la ventana. El valor predeterminado es NULL.

*dwStyle*<br/>
[en] El estilo de la ventana. El valor predeterminado es WS_CHILD WS_VISIBLE &#124;. Para obtener una lista de valores posibles, vea [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*dwExStyle*<br/>
[en] El estilo de ventana extendida. El valor predeterminado es 0, lo que significa que no hay estilo extendido. Para obtener una lista de valores posibles, vea [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*MenuOrID*<br/>
[en] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú para la ventana. El valor predeterminado es **0U**.

*lpCreateParam*<br/>
[en] Puntero a los datos de creación de ventanas. Para obtener una descripción completa, consulte la descripción del parámetro final en [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador de la ventana recién creada; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

El nombre de clase de ventana existente se guarda en [m_lpszClassName.](#m_lpszclassname) `Create`a continuación, crea una ventana basada en esta nueva clase. La ventana recién creada se `CContainedWindowT` adjunta automáticamente al objeto.

> [!NOTE]
> No llame `Create` si ya ha llamado a [SubclassWindow](#subclasswindow).

> [!NOTE]
> Si se utiliza 0 como valor para el *parámetro MenuOrID,* debe especificarse como 0U (el valor predeterminado) para evitar un error del compilador.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc

Llamado por [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Devuelve el mensaje`m_pCurrentMsg`actual ( ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valor devuelto

El mensaje actual, `MSG` empaquetado en la estructura.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Contiene el identificador del mapa de mensajes que se utiliza actualmente para la ventana contenida.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Observaciones

Este mapa de mensajes debe declararse en el objeto contenedor.

El mapa de mensajes predeterminado, declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), siempre se identifica por cero. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.

`m_dwMsgMapID`Primero se inicializa por el constructor y se puede cambiar llamando a [SwitchMessageMap](#switchmessagemap). Para obtener un ejemplo, vea [información general sobre CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Especifica el nombre de una clase de ventana existente.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Observaciones

Al crear una ventana, [Create](#create) registra una nueva clase de ventana que se basa en esta clase existente pero usa [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName`es inicializado por el constructor. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Si la ventana contenida está `m_pfnSuperWindowProc` subclase, apunta al procedimiento de ventana original de la clase de ventana.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Observaciones

Si la ventana contenida está superclase, lo que significa que se basa `m_pfnSuperWindowProc` en una clase de ventana que modifica una clase existente, apunta al procedimiento de ventana de la clase de ventana existente.

El método [DefWindowProc](#defwindowproc) envía información de `m_pfnSuperWindowProc`mensaje al procedimiento de ventana guardado en .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject

Apunta al objeto `CContainedWindowT` que contiene el objeto.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Observaciones

Este contenedor, cuya clase debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md), declara el mapa de mensajes utilizado por la ventana contenida.

`m_pObject`es inicializado por el constructor. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Llamado por [Create](#create) para registrar la clase de ventana de la ventana contenida.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un átomo que identifica de forma única la clase de ventana que se está registrando; de lo contrario, cero.

### <a name="remarks"></a>Observaciones

Esta clase de ventana se basa en una clase existente, pero utiliza [CContainedWindowT::WindowProc](#windowproc). El nombre y el procedimiento de ventana de la clase de ventana existente se guardan en [m_lpszClassName](#m_lpszclassname) y [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivamente.

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

Subclases de la ventana identificada por *hWnd* y la adjunta al `CContainedWindowT` objeto.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[en] El identificador de la ventana que se va a subclases.

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana se subclase correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

La ventana con subclases ahora utiliza [CContainedWindowT::WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> No llame `SubclassWindow` si ya ha llamado a [Crear](#create).

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Cambia el mapa de mensajes que se utilizará para procesar los mensajes de la ventana contenida.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parámetros

*dwMsgMapID*<br/>
[en] El identificador del mapa de mensajes. Para utilizar el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), pase cero. Para utilizar un mapa de mensajes alternativo declarado `msgMapID`con [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)pase .

### <a name="remarks"></a>Observaciones

El mapa de mensajes debe definirse en el objeto contenedor.

Inicialmente se especifica el identificador de mapa de mensajes en el constructor.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Separa la ventana subclase `CContainedWindowT` del objeto y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parámetros

*bFuerza*<br/>
[en] Establezca en TRUE para forzar que se restaure el `CContainedWindowT` procedimiento de ventana original incluso si el procedimiento de ventana para este objeto no está activo actualmente. Si *bForce* se establece en FALSE `CContainedWindowT` y el procedimiento de ventana para este objeto no está activo actualmente, no se restaurará el procedimiento de ventana original.

### <a name="return-value"></a>Valor devuelto

El identificador de la ventana subclaseanteriormente. Si *bForce* se establece en FALSE `CContainedWindowT` y el procedimiento de ventana para este objeto no está activo actualmente, devuelve NULL.

### <a name="remarks"></a>Observaciones

Utilice este método solo si desea restaurar el procedimiento de ventana original antes de que se destruya la ventana. De lo contrario, [WindowProc](#windowproc) lo hará automáticamente cuando se destruya la ventana.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc

Este método estático implementa el procedimiento de ventana.

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

`WindowProc`dirige los mensajes al mapa de mensajes identificado por [m_dwMsgMapID](#m_dwmsgmapid). Si es `WindowProc` necesario, llame a [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicional.

## <a name="see-also"></a>Vea también

[Clase CWindow](../../atl/reference/cwindow-class.md)<br/>
[Clase CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Clase CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
