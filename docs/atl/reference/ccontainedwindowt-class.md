---
title: CContainedWindowT (clase)
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
ms.openlocfilehash: 660c6c047bb700e531fd941ac8ed19d638866070
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421576"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT (clase)

Esta clase implementa una ventana dentro de otro objeto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parámetros

*TBase*<br/>
La clase base de la nueva clase. La clase base predeterminada es `CWindow`.

*TWinTraits*<br/>
Una clase de rasgos que define los estilos de la ventana. De manera predeterminada, es `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) es una especialización de `CContainedWindowT`. Si desea cambiar la clase base o rasgos, utilice `CContainedWindowT` directamente.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructor. Inicializa los miembros de datos para especificar qué mapa de mensajes procesará los mensajes de la ventana independiente.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CContainedWindowT::Create](#create)|Crea una ventana.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Proporciona el procesamiento de mensajes predeterminado.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Devuelve el mensaje actual.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Registra la clase de ventana de la ventana contenida.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Crea subclases de una ventana.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Cambia el mapa de mensajes se usa para procesar mensajes de ventana independiente.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaura una ventana cuyas subclases se han creado previamente.|
|[CContainedWindowT::WindowProc](#windowproc)|(Estático) Procesa los mensajes enviados a la ventana contenida.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifica el mapa de mensajes procesará los mensajes de la ventana independiente.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Especifica el nombre de una clase de ventana existente en el que se basará la nueva clase de ventana.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|
|[CContainedWindowT::m_pObject](#m_pobject)|Señala al objeto contenedor.|

## <a name="remarks"></a>Comentarios

`CContainedWindowT` implementa una ventana dentro de otro objeto. `CContainedWindowT`'s usos del procedimiento de ventana asignar un mensaje en el objeto contenedor para dirigir los mensajes a los controladores adecuados. Al construir un `CContainedWindowT` de objeto, especifique que debe usarse el mapa de mensajes.

`CContainedWindowT` permite crear una nueva ventana Crear superclases de una clase de ventana existente. El `Create` método registra primero una clase de ventana que se basa en una clase existente, pero usa `CContainedWindowT::WindowProc`. `Create` a continuación, crea una ventana basada en esta nueva clase de ventana. Cada instancia de `CContainedWindowT` puede superclase de una clase de ventana diferente.

`CContainedWindowT` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CContainedWindowT` y cambia el procedimiento de ventana a `CContainedWindowT::WindowProc`. Cada instancia de `CContainedWindowT` puede crear subclases de una ventana diferente.

> [!NOTE]
>  Para cualquier `CContainedWindowT` objeto, llame a `Create` o `SubclassWindow`. No debería invocar ambos métodos en el mismo objeto.

Cuando se usa el **Agregar control basado en** opción en el Asistente para proyectos ATL, el asistente agregará automáticamente un `CContainedWindowT` miembro de datos a la clase que implementa el control. El ejemplo siguiente muestra cómo se declara la ventana contenida:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Para obtener más información sobre|Vea|
|--------------------------------|---------|
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/desktop/winmsg/windows) y los temas siguientes en el SDK de Windows|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT

El constructor inicializa a los miembros de datos.

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
[in] El nombre de una clase de ventana existente en el que se basará la ventana contenida.

*pObject*<br/>
[in] Un puntero al objeto contenedor que declara el mapa de mensajes. Clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Identifica el mapa de mensajes que procesará los mensajes de la ventana independiente. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.

### <a name="remarks"></a>Comentarios

Si desea crear una nueva ventana a través de [crear](#create), debe pasar el nombre de una clase de ventana existente para la *lpszClassName* parámetro. Para obtener un ejemplo, vea el [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) información general.

Hay tres constructores:

- El constructor con tres argumentos es lo que se suelen denominar simplemente.

- El constructor con dos argumentos usa el nombre de clase de `TBase::GetWndClassName`.

- Si desea proporcionar los argumentos más adelante, se utiliza el constructor sin argumentos. Debe proporcionar el nombre de la clase de ventana, objeto de mapa de mensajes e Id. de asignación de mensaje cuando se llama a más adelante `Create`.

Si deriva una subclase de una ventana existente a través de [SubclassWindow](#subclasswindow), *lpszClassName* no se usará el valor; por lo tanto, puede pasar NULL para este parámetro.

##  <a name="create"></a>  CContainedWindowT::Create

Las llamadas [RegisterWndSuperclass](#registerwndsuperclass) para registrar una clase de ventana que se basa en una clase existente, pero usa [CContainedWindowT::WindowProc](#windowproc).

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
[in] El nombre de una clase de ventana existente en el que se basará la ventana contenida.

*pObject*<br/>
[in] Un puntero al objeto contenedor que declara el mapa de mensajes. Clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Identifica el mapa de mensajes que procesará los mensajes de la ventana independiente. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.

*hWndParent*<br/>
[in] El identificador de la ventana principal o propietaria.

*rect*<br/>
[in] Un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que especifica la posición de la ventana. El `RECT` puede pasarse por referencia o puntero.

*szWindowName*<br/>
[in] Especifica el nombre de la ventana. El valor predeterminado es NULL.

*dwStyle*<br/>
[in] El estilo de la ventana. El valor predeterminado es WS_CHILD &#124; WS_VISIBLE. Para obtener una lista de valores posibles, vea [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) en el SDK de Windows.

*dwExStyle*<br/>
[in] El estilo extendido de ventana. El valor predeterminado es 0, lo que significa que ningún estilo extendido. Para obtener una lista de valores posibles, vea [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*MenuOrID*<br/>
[in] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú de la ventana. El valor predeterminado es **0U**.

*lpCreateParam*<br/>
[in] Un puntero a datos de creación de la ventana. Para obtener una descripción completa, vea la descripción para el parámetro final a [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa).

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador de la ventana recién creado. en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

El nombre de clase de ventana existente se guarda en [m_lpszClassName](#m_lpszclassname). `Create` a continuación, crea una ventana basada en esta nueva clase. La ventana recién creada se adjunta automáticamente a la `CContainedWindowT` objeto.

> [!NOTE]
>  No llame a `Create` si ya ha llamado a [SubclassWindow](#subclasswindow).

> [!NOTE]
>  Si se utiliza 0 como valor para el *MenuOrID* parámetro, se debe especificar como 0U (usar el valor predeterminado) para evitar un error del compilador.

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
[in] El mensaje enviado a la ventana.

*wParam*<br/>
[in] Información adicional específica del mensaje.

*lParam*<br/>
[in] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El resultado del procesamiento del mensaje.

### <a name="remarks"></a>Comentarios

De forma predeterminada, `DefWindowProc` llamadas la [CallWindowProc](/windows/desktop/api/winuser/nf-winuser-callwindowproca) Win32/función para enviar la información del mensaje al procedimiento de ventana especificado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage

Devuelve el mensaje actual (`m_pCurrentMsg`).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valor devuelto

El mensaje actual, empaquetado en la `MSG` estructura.

##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID

Contiene el identificador del mapa de mensajes se utiliza actualmente para la ventana contenida.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Comentarios

Este mapa de mensajes debe declararse en el objeto contenedor.

El mapa de mensajes de forma predeterminada, se declara con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), siempre se identifica por cero. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.

`m_dwMsgMapID` se inicializa por primera vez el constructor y se puede cambiar mediante una llamada a [SwitchMessageMap](#switchmessagemap). Para obtener un ejemplo, vea el [CContainedWindowT Introducción](../../atl/reference/ccontainedwindowt-class.md).

##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName

Especifica el nombre de una clase de ventana existente.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Comentarios

Cuando se crea una ventana, [crear](#create) registra una nueva clase de ventana que se basa en esta clase ya existente, pero usa [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName` el constructor inicializa. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.

##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc

Si la ventana de contenido es una subclase, `m_pfnSuperWindowProc` apunta al procedimiento de ventana original de la clase de ventana.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Comentarios

Si la ventana contenida superclase, lo que significa que se basa en una clase de ventana que se modifica una clase existente, `m_pfnSuperWindowProc` apunta al procedimiento de ventana de la clase de ventana existente.

El [DefWindowProc](#defwindowproc) método envía información del mensaje al procedimiento de ventana que se guardan en `m_pfnSuperWindowProc`.

##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject

Señala al objeto que contiene el `CContainedWindowT` objeto.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Comentarios

Este contenedor, cuya clase se debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md), declara el mapa de mensajes utilizado por la ventana contenida.

`m_pObject` el constructor inicializa. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.

##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass

Lo llama [crear](#create) para registrar la clase de ventana de la ventana contenida.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un átomo que identifica la clase de ventana que se está registra; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta clase de ventana se basa en una clase existente, pero usa [CContainedWindowT::WindowProc](#windowproc). Procedimiento de nombre y la ventana de la clase de ventana existente se guardan en [m_lpszClassName](#m_lpszclassname) y [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivamente.

##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow

Las subclases de la ventana identificada por *hWnd* y lo asocia a la `CContainedWindowT` objeto.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[in] El identificador de la ventana que se va a crear subclase.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana es una subclase correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Ahora se utiliza la ventana con subclases [CContainedWindowT::WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado a [crear](#create).

##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap

Cambia el mapa de mensajes que se usará para procesar los mensajes de la ventana independiente.

```
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parámetros

*dwMsgMapID*<br/>
[in] Identificador de asignación de mensaje. Para usar el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), pasar cero. Para usar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.

### <a name="remarks"></a>Comentarios

El mapa de mensajes debe definirse en el objeto contenedor.

Inicialmente, se especifica el identificador del mapa de mensajes en el constructor.

##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow

Desasocia la ventana con subclases de la `CContainedWindowT` de objetos y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parámetros

*bForce*<br/>
[in] Establézcalo en True para forzar el procedimiento de ventana original restaurarse incluso si el procedimiento de ventana para este `CContainedWindowT` objeto no está activo actualmente. Si *bForce* se establece en FALSE y el procedimiento de ventana para este `CContainedWindowT` objeto no está activo actualmente, no se restaurará el procedimiento de ventana original.

### <a name="return-value"></a>Valor devuelto

El identificador de la ventana previamente una subclase. Si *bForce* se establece en FALSE y el procedimiento de ventana para este `CContainedWindowT` objeto no está actualmente activo, se devuelve NULL.

### <a name="remarks"></a>Comentarios

Use este método solo si desea restaurar el procedimiento de ventana original antes de que se destruye la ventana. En caso contrario, [WindowProc](#windowproc) automáticamente hará esto cuando se destruye la ventana.

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
[in] El identificador de la ventana.

*uMsg*<br/>
[in] El mensaje enviado a la ventana.

*wParam*<br/>
[in] Información adicional específica del mensaje.

*lParam*<br/>
[in] Información adicional específica del mensaje.

### <a name="return-value"></a>Valor devuelto

El resultado del procesamiento del mensaje.

### <a name="remarks"></a>Comentarios

`WindowProc` dirige los mensajes para el mapa de mensajes identificado por [m_dwMsgMapID](#m_dwmsgmapid). Si es necesario, `WindowProc` llamadas [DefWindowProc](#defwindowproc) para procesar los mensajes adicionales.

## <a name="see-also"></a>Vea también

[CWindow (clase)](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap (clase)](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
