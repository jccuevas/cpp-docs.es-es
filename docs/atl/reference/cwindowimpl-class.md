---
title: Clase de CWindowImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4884bbacd03675d00cb1a49b937265ab5faa2835
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cwindowimpl-class"></a>Clase de CWindowImpl
Proporciona métodos para crear una ventana o subclases de una ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Nueva clase derivada de `CWindowImpl`.  
  
 *TBase*  
 Clase base de la clase. De forma predeterminada, es la clase base [CWindow](../../atl/reference/cwindow-class.md).  
  
 `TWinTraits`  
 A [clase traits](../../atl/understanding-window-traits.md) que define los estilos de la ventana. De manera predeterminada, es `CControlWinTraits`.  
  
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
|[OnFinalMessage](#onfinalmessage)|Se llama después de recibir el último mensaje (normalmente `WM_NCDESTROY`).|  
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
  
## <a name="remarks"></a>Comentarios  
 Puede usar `CWindowImpl` para crear una ventana o una subclase de una ventana existente. el `CWindowImpl` procedimiento de ventana utiliza un mapa de mensajes para dirigir mensajes a los controladores adecuados.  
  
 `CWindowImpl::Create` crea una ventana basada en la información de clase de ventana que está administrada por [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` contiene el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (macro), lo que significa `CWndClassInfo` registra una nueva clase de ventana. Si desea superclase de una clase de ventana existente, derive su clase de `CWindowImpl` e incluya el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro. En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza `CWindowImpl::WindowProc`. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Dado que `CWndClassInfo` administra la información solo para una clase de ventana, cada ventana creada con una instancia de `CWindowImpl` se basa en la misma clase de ventana.  
  
 `CWindowImpl` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CWindowImpl` y cambia el procedimiento de ventana a `CWindowImpl::WindowProc`. Cada instancia de `CWindowImpl` puede crear subclases de una ventana diferente.  
  
> [!NOTE]
>  Para cualquier `CWindowImpl` objeto, llame a **crear** o `SubclassWindow`. No invoque ambos métodos en el mismo objeto.  
  
 Además `CWindowImpl`, ATL proporciona [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) para crear una ventana que se encuentra en otro objeto.  
  
 El destructor de clase base (~ **CWindowImplRoot**) garantiza que la ventana desaparezca antes de que se destruya el objeto.  
  
 `CWindowImpl` se deriva de **CWindowImplBaseT**, que deriva de **CWindowImplRoot**, que deriva de **TBase** y [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Para obtener más información sobre|Vea|  
|--------------------------------|---------|  
|Crear controles|[Tutorial ATL](../../atl/active-template-library-atl-tutorial.md)|  
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
  
##  <a name="create"></a>  CWindowImpl:: Create  
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
 `hWndParent`  
 [in] El identificador de la ventana primaria o propietaria.  
  
 `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura especifican la posición de la ventana. La `RECT` puede pasarse por referencia o puntero.  
  
 `szWindowName`  
 [in] Especifica el nombre de la ventana. El valor predeterminado es **NULL**.  
  
 `dwStyle`  
 [in] El estilo de la ventana. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado proporciona los rasgos de control completo sobre el estilo de la clase. Para obtener una lista de valores posibles, consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) del SDK de Windows.  
  
 `dwExStyle`  
 [in] El estilo de ventana extendidos. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado proporciona los rasgos de control completo sobre el estilo de la clase. Para obtener una lista de valores posibles, consulte [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `MenuOrID`  
 [in] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú de la ventana. El valor predeterminado es **0U**.  
  
 `lpCreateParam`  
 [in] Un puntero a datos de creación de la ventana. Para obtener una descripción completa, vea la descripción para el último parámetro para [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la ventana recién creada. En caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** registra primero la clase de ventana si aún no se ha registrado. La ventana recién creada se adjunta automáticamente a la `CWindowImpl` objeto.  
  
> [!NOTE]
>  No llame a **crear** si ya ha llamado [SubclassWindow](#subclasswindow).  
  
 Para utilizar una clase de ventana que se basa en una clase de ventana existente, derive su clase de `CWindowImpl` e incluya el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro. Procedimiento de ventana de la clase de ventana existente se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Para obtener más información, consulte el [CWindowImpl](../../atl/reference/cwindowimpl-class.md) información general.  
  
> [!NOTE]
>  Si se utiliza 0 como el valor de la `MenuOrID` parámetro, se debe especificar como 0U (valor predeterminado) para evitar un error del compilador.  
  
##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc  
 Llamado por el método [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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
  
 La función sin parámetros recupera automáticamente los parámetros necesarios desde el mensaje actual.  
  
##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage  
 Devuelve el mensaje actual, empaquetado en el `MSG` estructura.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El mensaje actual.  
  
##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc  
 Devuelve `WindowProc`, el procedimiento de ventana actual.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El procedimiento de ventana actual.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para reemplazar el procedimiento de ventana por los suyos propios.  
  
##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo  
 Llamado por el método [crear](#create) para tener acceso a la información de clase de ventana.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CWindowImpl` obtiene este método a través de la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro, que especifica una nueva clase de ventana.  
  
 Para superclase de una clase de ventana existente, derive su clase de `CWindowImpl` e incluya el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro invalidar `GetWndClassInfo`. Para obtener más información, consulte el [CWindowImpl](../../atl/reference/cwindowimpl-class.md) información general.  
  
 Además de utilizar el `DECLARE_WND_CLASS` y `DECLARE_WND_SUPERCLASS` macros, puede invalidar `GetWndClassInfo` con su propia implementación.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc  
 Dependiendo de la ventana, apunta a uno de los siguientes procedimientos de ventana.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Comentarios  
  
|Tipo de ventana|Procedimiento de ventana|  
|--------------------|----------------------|  
|Una ventana basada en una nueva clase de ventana especificada a través de la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro.|El [DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) función de Win32.|  
|Una ventana basada en una clase de ventana que se modifica una clase existente, especificada mediante el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro.|Procedimiento de ventana de la clase de ventana existente.|  
|Una ventana de la subclase.|Procedimiento de ventana original de la subclase de la ventana.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) envía mensaje información al procedimiento de ventana que se guarda en `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage  
 Llamado después de recibir el último mensaje (normalmente `WM_NCDESTROY`).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] Identificador de la ventana que se destruya.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de `OnFinalMessage` no hace nada, pero puede invalidar esta función para controlar la limpieza antes de destruir una ventana. Si desea eliminar automáticamente el objeto tras la destrucción de ventanas, puede llamar a `delete this;` en esta función.  
  
##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow  
 Las subclases de la ventana identificada por `hWnd` y lo adjunta a la `CWindowImpl` objeto.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] El identificador de la ventana que se va a crear subclase.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la ventana está correctamente con subclases; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La subclase ventana ahora usa [CWindowImpl:: WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado [crear](#create).  
  
##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow  
 Desasocia la ventana subclases de la `CWindowImpl` objeto y restaura el procedimiento de ventana original, guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de la ventana previamente una subclase.  
  
##  <a name="windowproc"></a>  CWindowImpl:: WindowProc  
 Esta función estática implementa el procedimiento de ventana.  
  
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
 `WindowProc` utiliza la asignación de mensaje de forma predeterminada (declarados con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) para dirigir los mensajes a los controladores adecuados. Si es necesario, `WindowProc` llamadas [DefWindowProc](#defwindowproc) para el procesamiento de mensajes adicionales. Si no se controla el mensaje final, `WindowProc` hace lo siguiente:  
  
-   Lleva a cabo unsubclassing si la ventana es unsubclassed.  
  
-   Borra `m_hWnd`.  
  
-   Llamadas [OnFinalMessage](#onfinalmessage) antes de que se destruya la ventana.  
  
 Puede invalidar `WindowProc` para proporcionar un mecanismo diferente para el tratamiento de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
