---
title: Clase IOleInPlaceObjectWindowlessImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5616258405eb8346132d32b8f7fd71d0b4794d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365007"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Clase IOleInPlaceObjectWindowlessImpl
Esta clase implementa **IUnknown** y proporciona métodos que permiten un control sin ventana que se va a recibir mensajes de ventana como participar en operaciones de arrastrar y colocar.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IOleInPlaceObjectWindowlessImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la Ayuda contextual. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Proporciona el `IDropTarget` interfaz para un objeto en contexto activo, sin ventana que permite arrastrar y colocar. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Desactiva un control en el contexto activo.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Envía un mensaje desde el contenedor a un control sin ventana que está activo en contexto.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Vuelve a activar un control desactivado anteriormente. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Indica qué parte del control en el contexto está visible.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Desactiva y quita la interfaz de usuario que admite la activación en contexto.|  
  
## <a name="remarks"></a>Comentarios  
 El [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) interfaz administra la reactivación y desactivación de in situ controles y determina la cantidad del control debe ser visible. El [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) interfaz permite que un control sin ventana que se va a recibir mensajes de ventana como participar en operaciones de arrastrar y colocar. Clase `IOleInPlaceObjectWindowlessImpl` proporciona una implementación predeterminada de `IOleInPlaceObject` y `IOleInPlaceObjectWindowless` e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 Devuelve **E_NOTIMPL**.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) en el SDK de Windows.  
  
##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Devuelve **E_NOTIMPL**.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) en el SDK de Windows.  
  
##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow  
 El contenedor llama a esta función para obtener el identificador de ventana del control.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Comentarios  
 Algunos contenedores no funcionará con un control que haya estado sin ventana, incluso si está actualmente con ventanas. En la implementación de ATL, si el miembro de datos de la clase de control `m_bWasOnceWindowless` es **TRUE**, la función devuelve **E_FAIL**. De lo contrario, si *phwnd* no **NULL**, `GetWindow` establece \* *phwnd* al miembro de datos de la clase de control `m_hWnd` y devuelve `S_OK`.  
  
 Vea [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) en el SDK de Windows.  
  
##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Llamado por el contenedor para desactivar un control activo en contexto.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Comentarios  
 Este método realiza una desactivación completa o parcial según el estado del control. Si es necesario, se desactiva la interfaz de usuario del control y la ventana del control, si existe, se destruye. El contenedor se notifica que el control ya no está activo en su lugar. El **IOleInPlaceUIWindow** interfaz utilizada por el contenedor para negociar los menús y espacio de borde se libera.  
  
 Vea [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) en el SDK de Windows.  
  
##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 Envía un mensaje desde un contenedor a un control sin ventana que está activo en contexto.  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) en el SDK de Windows.  
  
##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Devuelve **E_NOTIMPL**.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) en el SDK de Windows.  
  
##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 El contenedor llama para informar al control que ha cambiado su tamaño o la posición.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el control `m_rcPos` miembro de datos y la presentación del control. Se muestra solo la parte del control que forma una intersección con la región de recorte. Si anteriormente se recorta la presentación del control, pero se ha quitado el recorte, esta función puede llamarse para volver a dibujar una vista completa del control.  
  
 Vea [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) en el SDK de Windows.  
  
##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Desactiva y quita la interfaz de usuario del control que admite la activación en contexto.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece el miembro de datos de la clase de control `m_bUIActive` a **FALSE**. La implementación de ATL de esta función siempre devuelve `S_OK`.  
  
 Vea [IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
