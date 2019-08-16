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
ms.openlocfilehash: 2eae6e149cf6f7422d0653c1c15f46985d8d55c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496855"
---
# <a name="ccontainedwindowt-class"></a>Clase CContainedWindowT

Esta clase implementa una ventana contenida dentro de otro objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parámetros

*TBase*<br/>
La clase base de la nueva clase. La clase base predeterminada es `CWindow`.

*TWinTraits*<br/>
Una clase traits que define estilos para la ventana. El valor predeterminado es `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) es una especialización de `CContainedWindowT`. Si desea cambiar la clase base o rasgos, use `CContainedWindowT` directamente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructor. Inicializa los miembros de datos para especificar qué mapa de mensajes procesará los mensajes de la ventana contenida.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Crea una ventana.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Proporciona el procesamiento de mensajes predeterminado.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Devuelve el mensaje actual.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Registra la clase de ventana de la ventana contenida.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Crea subclases de una ventana.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Cambia el mapa de mensajes que se utiliza para procesar los mensajes de la ventana contenida.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaura una ventana cuyas subclases se han creado previamente.|
|[CContainedWindowT::WindowProc](#windowproc)|Estático Procesa los mensajes enviados a la ventana contenida.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifica qué mapa de mensajes procesará los mensajes de la ventana contenida.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Especifica el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|
|[CContainedWindowT::m_pObject](#m_pobject)|Apunta al objeto contenedor.|

## <a name="remarks"></a>Comentarios

`CContainedWindowT`implementa una ventana contenida dentro de otro objeto. `CContainedWindowT`el procedimiento de ventana de utiliza un mapa de mensajes en el objeto contenedor para dirigir los mensajes a los controladores adecuados. Al construir un objeto `CContainedWindowT` , se especifica qué mapa de mensajes se debe utilizar.

`CContainedWindowT`permite crear una nueva ventana mediante la superclase de una clase de ventana existente. El `Create` método registra primero una clase de ventana que se basa en una clase existente, pero `CContainedWindowT::WindowProc`utiliza. `Create`después, crea una ventana basada en esta nueva clase de ventana. Cada instancia de `CContainedWindowT` puede superclase en una clase de ventana diferente.

`CContainedWindowT` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CContainedWindowT` y cambia el procedimiento de ventana a `CContainedWindowT::WindowProc`. Cada instancia de `CContainedWindowT` puede crear subclases de una ventana diferente.

> [!NOTE]
>  Para cualquier objeto `CContainedWindowT` dado, `Create` llame a o `SubclassWindow`a. No debe invocar ambos métodos en el mismo objeto.

Cuando se usa la opción **Agregar control basado en** en el Asistente para proyectos ATL, el asistente agregará automáticamente `CContainedWindowT` un miembro de datos a la clase que implementa el control. En el ejemplo siguiente se muestra cómo se declara la ventana contenida:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Para obtener más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Ventanas](/windows/win32/winmsg/windows) y temas posteriores en el Windows SDK|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT

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
de Nombre de una clase de ventana existente en la que se basará la ventana contenida.

*pObject*<br/>
de Un puntero al objeto contenedor que declara el mapa de mensajes. La clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
de Identifica el mapa de mensajes que procesará los mensajes de la ventana contenida. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`pase.

### <a name="remarks"></a>Comentarios

Si desea crear una nueva ventana a través de [Create](#create), debe pasar el nombre de una clase de ventana existente para el parámetro *lpszClassName* . Para obtener un ejemplo, vea la información general de [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) .

Hay tres constructores:

- El constructor con tres argumentos es el que se suele llamar.

- El constructor con dos argumentos utiliza el nombre de clase `TBase::GetWndClassName`de.

- El constructor sin argumentos se utiliza si desea proporcionar los argumentos más adelante. Debe proporcionar el nombre de clase de ventana, el objeto de mapa de mensajes y el identificador de mapa `Create`de mensajes cuando llame posteriormente a.

Si crea subclases de una ventana existente a través de [SubclassWindow](#subclasswindow), no se usará el valor *lpszClassName* . por lo tanto, se puede pasar NULL para este parámetro.

##  <a name="create"></a>  CContainedWindowT::Create

Llama a [RegisterWndSuperclass](#registerwndsuperclass) para registrar una clase de ventana que se basa en una clase existente, pero utiliza [CContainedWindowT:: WindowProc](#windowproc).

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
de Nombre de una clase de ventana existente en la que se basará la ventana contenida.

*pObject*<br/>
de Un puntero al objeto contenedor que declara el mapa de mensajes. La clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
de Identifica el mapa de mensajes que procesará los mensajes de la ventana contenida. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`pase.

*hWndParent*<br/>
de Identificador de la ventana primaria o propietaria.

*rect*<br/>
de Estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que especifica la posición de la ventana. Se `RECT` puede pasar por puntero o por referencia.

*szWindowName*<br/>
de Especifica el nombre de la ventana. El valor predeterminado es NULL.

*dwStyle*<br/>
de Estilo de la ventana. El valor predeterminado es WS_CHILD &#124; WS_VISIBLE. Para obtener una lista de los valores posibles, vea [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK.

*dwExStyle*<br/>
de Estilo de ventana extendido. El valor predeterminado es 0, lo que significa que no hay ningún estilo extendido. Para obtener una lista de los valores posibles, vea [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*MenuOrID*<br/>
de Para una ventana secundaria, el identificador de la ventana. En el caso de una ventana de nivel superior, un identificador de menú para la ventana. El valor predeterminado es **0U**.

*lpCreateParam*<br/>
de Puntero a los datos de creación de ventanas. Para obtener una descripción completa, vea la descripción del parámetro final en [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador de la ventana recién creada; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

El nombre de clase de ventana existente se guarda en [m_lpszClassName](#m_lpszclassname). `Create`después, crea una ventana basada en esta nueva clase. La ventana recién creada se adjunta automáticamente al `CContainedWindowT` objeto.

> [!NOTE]
>  No llame a `Create` si ya ha llamado a [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Si se usa 0 como valor del parámetro *MenuOrID* , debe especificarse como 0U (el valor predeterminado) para evitar un error del compilador.

##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc

Lo llama [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

De forma predeterminada `DefWindowProc` , llama a la función [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) de Win32 para enviar la información del mensaje al procedimiento de ventana especificado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage

Devuelve el mensaje actual (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valor devuelto

Mensaje actual, empaquetado en la `MSG` estructura.

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

Contiene el identificador del mapa de mensajes que se está usando actualmente para la ventana contenida.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Comentarios

Este mapa de mensajes se debe declarar en el objeto contenedor.

El mapa de mensajes predeterminado, declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), siempre se identifica por cero. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica `msgMapID`mediante.

`m_dwMsgMapID`primero inicializa el constructor y se puede cambiar llamando a [SwitchMessageMap](#switchmessagemap). Para obtener un ejemplo, consulte la [información general de CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

Especifica el nombre de una clase de ventana existente.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Comentarios

Cuando se crea una ventana, [Create](#create) registra una nueva clase de ventana que se basa en esta clase existente, pero usa [CContainedWindowT:: WindowProc](#windowproc).

`m_lpszClassName`el constructor inicializa. Para obtener un ejemplo, consulte la información general de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

Si la ventana contenida tiene subclases `m_pfnSuperWindowProc` , apunta al procedimiento de ventana original de la clase de ventana.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Comentarios

Si la ventana contenida es superclase, lo que significa que se basa en una clase de ventana que modifica una clase `m_pfnSuperWindowProc` existente, apunta al procedimiento de ventana de la clase de ventana existente.

El método [DefWindowProc](#defwindowproc) envía información del mensaje al procedimiento de ventana guardado `m_pfnSuperWindowProc`en.

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

Apunta al objeto que contiene el `CContainedWindowT` objeto.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Comentarios

Este contenedor, cuya clase debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md), declara el mapa de mensajes utilizado por la ventana contenida.

`m_pObject`el constructor inicializa. Para obtener un ejemplo, consulte la información general de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass

Llamado por [Create](#create) para registrar la clase de ventana de la ventana contenida.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un átomo que identifica de forma única la clase de ventana que se está registrando; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta clase de ventana se basa en una clase existente, pero usa [CContainedWindowT:: WindowProc](#windowproc). El procedimiento de ventana y el nombre de la clase de ventana existente se guardan en [m_lpszClassName](#m_lpszclassname) y [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivamente.

##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow

Subclases la ventana identificada por *hWnd* y la `CContainedWindowT` adjunta al objeto.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
de Identificador de la ventana de la que se van a subclases.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se ha subclase correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La ventana subclase ahora usa [CContainedWindowT:: WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado a [Create](#create).

##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap

Cambia el mapa de mensajes que se utilizará para procesar los mensajes de la ventana contenida.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parámetros

*dwMsgMapID*<br/>
de Identificador del mapa de mensajes. Para usar el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), pase cero. Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), `msgMapID`pase.

### <a name="remarks"></a>Comentarios

El mapa de mensajes debe definirse en el objeto contenedor.

Inicialmente, se especifica el identificador de mapa de mensajes en el constructor.

##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow

Desasocia la ventana de subclase del `CContainedWindowT` objeto y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parámetros

*bForce*<br/>
de Establézcalo en true para obligar a que se restaure el procedimiento de ventana original incluso si el `CContainedWindowT` procedimiento de ventana para este objeto no está activo actualmente. Si *bForce* se establece en false y el procedimiento de ventana para `CContainedWindowT` este objeto no está activo actualmente, no se restaurará el procedimiento de ventana original.

### <a name="return-value"></a>Valor devuelto

Identificador de la ventana con la subclase anterior. Si *bForce* se establece en false y el procedimiento de ventana para `CContainedWindowT` este objeto no está activo actualmente, devuelve NULL.

### <a name="remarks"></a>Comentarios

Use este método solo si desea restaurar el procedimiento de ventana original antes de que se destruya la ventana. De lo contrario, [WindowProc](#windowproc) lo hará automáticamente cuando se destruya la ventana.

##  <a name="windowproc"></a>  CContainedWindowT::WindowProc

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

`WindowProc`dirige los mensajes al mapa de mensajes identificado por [m_dwMsgMapID](#m_dwmsgmapid). Si es necesario `WindowProc` , llama a [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicional.

## <a name="see-also"></a>Vea también

[CWindow (clase)](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap (clase)](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
