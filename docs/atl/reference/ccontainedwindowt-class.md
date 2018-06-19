---
title: Clase de CContainedWindowT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f3f90e23eed3bd1eba80bbf90fe73de45eb7cfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366489"
---
# <a name="ccontainedwindowt-class"></a>Clase de CContainedWindowT
Esta clase implementa una ventana dentro de otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>Parámetros  
 *TBase*  
 La clase base de la nueva clase. La clase base predeterminada es `CWindow`.  
  
 `TWinTraits`  
 Una clase de rasgos que define los estilos de la ventana. De manera predeterminada, es `CControlWinTraits`.  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) es una especialización de `CContainedWindowT`. Si desea cambiar la clase base o rasgos, use `CContainedWindowT` directamente.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructor. Inicializa los miembros de datos para especificar qué mapa de mensajes procesará los mensajes de la ventana independiente.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT:: Create](#create)|Crea una ventana.|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Proporciona el procesamiento de mensajes predeterminado.|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Devuelve el mensaje actual.|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Registra la clase de ventana de la ventana independiente.|  
|[CContainedWindowT:: SubclassWindow](#subclasswindow)|Crea subclases de una ventana.|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Cambia el mapa de mensajes se usa para procesar mensajes de ventana independiente.|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaura una ventana cuyas subclases se han creado previamente.|  
|[CContainedWindowT::WindowProc](#windowproc)|(Estático) Procesa los mensajes enviados a la ventana independiente.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifica qué mapa de mensajes procesará los mensajes de la ventana independiente.|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Especifica el nombre de una clase de ventana existente en el que se basará una nueva clase de ventana.|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Señala al procedimiento de ventana original de la clase de la ventana.|  
|[CContainedWindowT::m_pObject](#m_pobject)|Señala al objeto contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 `CContainedWindowT` implementa una ventana dentro de otro objeto. `CContainedWindowT`'s usos de procedimiento de ventana mapa de un mensaje en el objeto contenedor para dirigir los mensajes a los controladores adecuados. Al construir un `CContainedWindowT` de objeto, especifique qué mapa de mensajes debe utilizarse.  
  
 `CContainedWindowT` le permite crear una nueva ventana de creación de superclases una clase de ventana existente. El **crear** método registra primero una clase de ventana que se basa en una clase existente pero utiliza `CContainedWindowT::WindowProc`. **Crear** , a continuación, crea una ventana basada en esta nueva clase de ventana. Cada instancia de `CContainedWindowT` puede superclase de una clase de ventana diferente.  
  
 `CContainedWindowT` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CContainedWindowT` y cambia el procedimiento de ventana a `CContainedWindowT::WindowProc`. Cada instancia de `CContainedWindowT` puede crear subclases de una ventana diferente.  
  
> [!NOTE]
>  Para cualquier `CContainedWindowT` objeto, llame a **crear** o `SubclassWindow`. No debe invocar los métodos en el mismo objeto.  
  
 Cuando se usa el **Agregar control basado en** opción en el Asistente para proyectos ATL, el asistente agregará automáticamente una `CContainedWindowT` miembro de datos a la clase que implementa el control. En el ejemplo siguiente se muestra cómo se declara la ventana independiente:  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|Para obtener más información sobre|Vea|  
|--------------------------------|---------|  
|Crear controles|[Tutorial ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595) y los temas siguientes en el SDK de Windows|  
  
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
 `lpszClassName`  
 [in] El nombre de una clase de ventana existente en el que se basará la ventana independiente.  
  
 `pObject`  
 [in] Un puntero al objeto contenedor que declara el mapa de mensajes. Clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identifica el mapa de mensajes que procesará los mensajes de la ventana independiente. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declara con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.  
  
### <a name="remarks"></a>Comentarios  
 Si desea crear una nueva ventana a través de [crear](#create), debe pasar el nombre de una clase de ventana existente para la `lpszClassName` parámetro. Para obtener un ejemplo, vea el [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) información general.  
  
 Hay tres constructores:  
  
-   El constructor con tres argumentos es la que se suelen denominar simplemente.  
  
-   El constructor con dos argumentos usa el nombre de clase de **TBase::GetWndClassName**.  
  
-   Si desea proporcionar los argumentos más adelante, se utiliza el constructor sin argumentos. Debe proporcionar el nombre de la clase de ventana, el objeto de mapa de mensajes y el Id. de asignación de mensaje al llamar posteriormente **crear**.  
  
 Si deriva una subclase de una ventana existente a través de [SubclassWindow](#subclasswindow), `lpszClassName` no se usará el valor; por lo tanto, puede pasar **NULL** para este parámetro.  
  
##  <a name="create"></a>  CContainedWindowT:: Create  
 Llamadas [RegisterWndSuperclass](#registerwndsuperclass) para registrar una clase de ventana que se basa en una clase existente pero utiliza [CContainedWindowT::WindowProc](#windowproc).  
  
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
 `lpszClassName`  
 [in] El nombre de una clase de ventana existente en el que se basará la ventana independiente.  
  
 `pObject`  
 [in] Un puntero al objeto contenedor que declara el mapa de mensajes. Clase de este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] Identifica el mapa de mensajes que procesará los mensajes de la ventana independiente. El valor predeterminado, 0, especifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para usar un mapa de mensajes alternativo declara con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.  
  
 `hWndParent`  
 [in] El identificador de la ventana primaria o propietaria.  
  
 `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura especifican la posición de la ventana. La `RECT` puede pasarse por referencia o puntero.  
  
 `szWindowName`  
 [in] Especifica el nombre de la ventana. El valor predeterminado es **NULL**.  
  
 `dwStyle`  
 [in] El estilo de la ventana. El valor predeterminado es **WS_CHILD &#124; WS_VISIBLE**. Para obtener una lista de valores posibles, consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) del SDK de Windows.  
  
 `dwExStyle`  
 [in] El estilo de ventana extendidos. El valor predeterminado es 0, lo que significa que ningún estilo extendido. Para obtener una lista de valores posibles, consulte [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `MenuOrID`  
 [in] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú de la ventana. El valor predeterminado es **0U**.  
  
 `lpCreateParam`  
 [in] Un puntero a datos de creación de la ventana. Para obtener una descripción completa, vea la descripción para el último parámetro para [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la ventana recién creada; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El nombre de clase de ventana existente se guarda en [m_lpszClassName](#m_lpszclassname). **Crear** , a continuación, crea una ventana basada en esta nueva clase. La ventana recién creada se adjunta automáticamente a la `CContainedWindowT` objeto.  
  
> [!NOTE]
>  No llame a **crear** si ya ha llamado [SubclassWindow](#subclasswindow).  
  
> [!NOTE]
>  Si se utiliza 0 como el valor de la `MenuOrID` parámetro, se debe especificar como 0U (valor predeterminado) para evitar un error del compilador.  
  
##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc  
 Llamado por el método [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.  
  
```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `uMsg`  
 [in] El mensaje enviado a la ventana.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `DefWindowProc` llamadas el [CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) función de Win32 para enviar la información del mensaje al procedimiento de ventana especificado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage  
 Devuelve el mensaje actual ( **m_pCurrentMsg**).  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El mensaje actual, empaquetado en el `MSG` estructura.  
  
##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID  
 Contiene el identificador del mapa de mensajes que se usa actualmente para la ventana independiente.  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>Comentarios  
 Este mapa de mensajes se debe declarar en el objeto contenedor.  
  
 El mapa de mensajes de forma predeterminada, se declara con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), siempre se identifica por cero. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.  
  
 `m_dwMsgMapID` primero se inicializa el constructor y puede modificarse mediante una llamada a [SwitchMessageMap](#switchmessagemap). Para obtener un ejemplo, vea el [información general de CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).  
  
##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName  
 Especifica el nombre de una clase de ventana existente.  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se crea una ventana, [crear](#create) registra una nueva clase de ventana que se basa en la clase existente pero usa [CContainedWindowT::WindowProc](#windowproc).  
  
 `m_lpszClassName` se inicializa el constructor. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc  
 Si la ventana independiente es una subclase, `m_pfnSuperWindowProc` señala al procedimiento de ventana original de la clase de ventana.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Comentarios  
 Si la ventana independiente es superclase, lo que significa que se basa en una clase de ventana que se modifica una clase existente, `m_pfnSuperWindowProc` señala al procedimiento de ventana de la clase de ventana existente.  
  
 El [DefWindowProc](#defwindowproc) método envía información del mensaje al procedimiento de ventana que se guarda en `m_pfnSuperWindowProc`.  
  
##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject  
 Señala al objeto que contiene el `CContainedWindowT` objeto.  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>Comentarios  
 Este contenedor, cuya clase debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md), declara el mapa de mensajes utilizado por la ventana independiente.  
  
 `m_pObject` se inicializa el constructor. Para obtener un ejemplo, vea el [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) información general.  
  
##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass  
 Llamado por el método [crear](#create) para registrar la clase de ventana de la ventana independiente.  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, una atom que identifica de forma única la clase de ventana que se va a registrar; en caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase de ventana se basa en una clase existente pero usa [CContainedWindowT::WindowProc](#windowproc). Procedimiento de nombre y la ventana de la clase de ventana existente se guardan en [m_lpszClassName](#m_lpszclassname) y [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivamente.  
  
##  <a name="subclasswindow"></a>  CContainedWindowT:: SubclassWindow  
 Las subclases de la ventana identificada por `hWnd` y lo adjunta a la `CContainedWindowT` objeto.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] El identificador de la ventana que se va a crear subclase.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la ventana está correctamente con subclases; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La subclase ventana ahora usa [CContainedWindowT::WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado [crear](#create).  
  
##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap  
 Cambia el mapa de mensajes se usarán para procesar mensajes de ventana independiente.  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMsgMapID`  
 [in] El identificador del mapa de mensajes. Para usar la asignación de mensaje predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), pasar cero. Para usar un mapa de mensajes alternativo declara con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de mensajes debe definirse en el objeto contenedor.  
  
 Inicialmente, se especifique el identificador del mapa de mensajes en el constructor.  
  
##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow  
 Desasocia la ventana subclases de la `CContainedWindowT` objeto y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bForce`  
 [in] Establecido en **TRUE** para forzar que el procedimiento de ventana original que se restaurarán incluso si el procedimiento de ventana para este `CContainedWindowT` objeto no está activo actualmente. Si `bForce` está establecido en **FALSE** y el procedimiento de ventana para este `CContainedWindowT` objeto no está actualmente activo, el procedimiento de ventana original no se restaurarán.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de la ventana previamente una subclase. Si `bForce` está establecido en **FALSE** y el procedimiento de ventana para este `CContainedWindowT` objeto no está activo actualmente, se devuelve **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método únicamente si desea restaurar el procedimiento de ventana original antes de que se destruya la ventana. En caso contrario, [WindowProc](#windowproc) automáticamente se hace esto cuando se destruye la ventana.  
  
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
 `hWnd`  
 [in] El identificador de la ventana.  
  
 `uMsg`  
 [in] El mensaje enviado a la ventana.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado del procesamiento del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 `WindowProc` dirige los mensajes para el mapa de mensajes identificado por [m_dwMsgMapID](#m_dwmsgmapid). Si es necesario, `WindowProc` llamadas [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicionales.  
  
## <a name="see-also"></a>Vea también  
 [Clase CWindow](../../atl/reference/cwindow-class.md)   
 [Clase de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Clase de CMessageMap](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Información general de clases](../../atl/atl-class-overview.md)
