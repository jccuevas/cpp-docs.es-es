---
title: Clase CWindowImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 76827682e96d2aea80880fa7d70c267abe02ee1c
ms.lasthandoff: 02/24/2017

---
# <a name="cwindowimpl-class"></a>CWindowImpl (clase)
Proporciona métodos para crear una ventana o subclases de una ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
 Un [clase de rasgos](../../atl/understanding-window-traits.md) que define los estilos de la ventana. De manera predeterminada, es `CControlWinTraits`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
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
  
 `CWindowImpl::Create`crea una ventana basada en la información de clase de ventana que es administrada por [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`contiene el [DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (macro), lo que significa que `CWndClassInfo` registra una nueva clase de ventana. Si desea superclase de una clase de ventana existente, derive la clase de `CWindowImpl` e incluya el [DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd) macro. En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza `CWindowImpl::WindowProc`. Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing&#43;](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Dado que `CWndClassInfo` administra la información solo para una clase de ventana, cada ventana creada con una instancia de `CWindowImpl` se basa en la misma clase de ventana.  
  
 `CWindowImpl` también permite crear subclases de una ventana. El método `SubclassWindow` adjunta una ventana existente al objeto `CWindowImpl` y cambia el procedimiento de ventana a `CWindowImpl::WindowProc`. Cada instancia de `CWindowImpl` puede crear subclases de una ventana diferente.  
  
> [!NOTE]
>  Para cualquier `CWindowImpl` objeto, llame a **crear** o `SubclassWindow`. No invoque ambos métodos en el mismo objeto.  
  
 Además `CWindowImpl`, ATL proporciona [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) para crear una ventana que se encuentra en otro objeto.  
  
 El destructor de clase base (~ **CWindowImplRoot**) garantiza que la ventana desaparezca antes de que se destruya el objeto.  
  
 `CWindowImpl`se deriva de **CWindowImplBaseT**, que se deriva de **CWindowImplRoot**, que se deriva de **TBase** y [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Para obtener más información sobre|Vea|  
|--------------------------------|---------|  
|Crear controles|[Tutorial ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
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
 `hWndParent`  
 [in] Identificador de la ventana primaria o propietaria.  
  
 `rect`  
 [in] Un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica la posición de la ventana. El `RECT` se puede pasar por referencia o puntero.  
  
 `szWindowName`  
 [in] Especifica el nombre de la ventana. El valor predeterminado es **NULL**.  
  
 `dwStyle`  
 [in] El estilo de la ventana. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado ofrece a los rasgos clase un control completo sobre el estilo. Para obtener una lista de valores posibles, consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwExStyle`  
 [in] El estilo de ventana extendidos. Este valor se combina con el estilo proporcionado por la clase de rasgos para la ventana. El valor predeterminado ofrece a los rasgos clase un control completo sobre el estilo. Para obtener una lista de valores posibles, consulte [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `MenuOrID`  
 [in] Para una ventana secundaria, el identificador de ventana. Para una ventana de nivel superior, un identificador de menú de la ventana. El valor predeterminado es **0U**.  
  
 `lpCreateParam`  
 [in] Un puntero a los datos de creación de la ventana. Para obtener una descripción completa, consulte la descripción para el parámetro final para [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador de la ventana recién creada. De lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** registra primero la clase de ventana si aún no se ha registrado. La ventana recién creada se adjunta automáticamente a la `CWindowImpl` objeto.  
  
> [!NOTE]
>  No llame a **crear** si ya ha llamado a [SubclassWindow](#subclasswindow).  
  
 Para utilizar una clase de ventana que se basa en una clase de ventana existente, derive la clase de `CWindowImpl` e incluya el [DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd) macro. Procedimiento de ventana de la clase de ventana existente se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Para obtener más información, consulte el [CWindowImpl](../../atl/reference/cwindowimpl-class.md) información general.  
  
> [!NOTE]
>  Si se utiliza 0 como valor para el `MenuOrID` parámetro, se debe especificar como 0U (valor) para evitar un error del compilador.  
  
##  <a name="defwindowproc"></a>CWindowImpl::DefWindowProc  
 Llama a [WindowProc](#windowproc) para procesar los mensajes no controlados por el mapa de mensajes.  
  
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
  
##  <a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage  
 Devuelve el mensaje actual, empaquetado en el `MSG` estructura.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El mensaje actual.  
  
##  <a name="getwindowproc"></a>CWindowImpl::GetWindowProc  
 Devuelve `WindowProc`, el procedimiento de ventana actual.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El procedimiento de ventana actual.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para reemplazar el procedimiento de ventana por el suyo propio.  
  
##  <a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo  
 Llama a [crear](#create) para tener acceso a la información de clase de ventana.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `CWindowImpl` obtiene este método a través de la [DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) macro, que especifica una nueva clase de ventana.  
  
 A la superclase de una clase de ventana existente, derive la clase de `CWindowImpl` e incluyen el [DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd) macro reemplazar `GetWndClassInfo`. Para obtener más información, consulte el [CWindowImpl](../../atl/reference/cwindowimpl-class.md) información general.  
  
 Además de utilizar la `DECLARE_WND_CLASS` y `DECLARE_WND_SUPERCLASS` macros, puede invalidar `GetWndClassInfo` con su propia implementación.  
  
##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc  
 Dependiendo de la ventana, apunta a uno de los siguientes procedimientos de ventana.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Comentarios  
  
|Tipo de ventana|Procedimiento de ventana|  
|--------------------|----------------------|  
|Una ventana basada en una nueva clase de ventana especificada a través de la [DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) macro.|El [DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) función de Win32.|  
|Una ventana basada en una clase de ventana que se modifica una clase existente, especificada mediante el [DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd) macro.|Procedimiento de ventana de la clase de ventana existente.|  
|Una ventana con subclases.|Procedimiento de ventana original de la subclase de la ventana.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) envía un mensaje de información que guardó en el procedimiento de ventana `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage  
 Llamado después de recibir el último mensaje (normalmente `WM_NCDESTROY`).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] Identificador de la ventana que se va a destruir.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de `OnFinalMessage` no hace nada, pero puede reemplazar esta función para controlar la limpieza antes de destruir una ventana. Si desea eliminar automáticamente el objeto tras la destrucción de ventana, puede llamar a `delete this;` en esta función.  
  
##  <a name="subclasswindow"></a>CWindowImpl::SubclassWindow  
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
 Ahora utiliza la ventana subclases [CWindowImpl:: WindowProc](#windowproc). El procedimiento de ventana original se guarda en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  No llame a `SubclassWindow` si ya ha llamado a [crear](#create).  
  
##  <a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow  
 Desasocia la ventana subclases de la `CWindowImpl` objeto y restaura el procedimiento de ventana original guardado en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de la ventana previamente una subclase.  
  
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
 `WindowProc`utiliza el mapa de mensajes predeterminado (declarado con [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)) para dirigir mensajes a los controladores adecuados. Si es necesario, `WindowProc` llamadas [DefWindowProc](#defwindowproc) de procesamiento de mensajes adicionales. Si no se controla el mensaje final, `WindowProc` hace lo siguiente:  
  
-   Realiza unsubclassing si la ventana era unsubclassed.  
  
-   Borra `m_hWnd`.  
  
-   Llamadas [OnFinalMessage](#onfinalmessage) antes de que se destruye la ventana.  
  
 Puede reemplazar `WindowProc` para proporcionar un mecanismo diferente para el tratamiento de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

