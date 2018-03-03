---
title: Clase IOleInPlaceActiveObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d88f85e83a88b0a1ce2bd4566e3ca479dddc1af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Clase IOleInPlaceActiveObjectImpl
Esta clase proporciona métodos para ayudar a la comunicación entre un control in situ y su contenedor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la Ayuda contextual. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permite cuadros de diálogo no modal. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Notifica al control cuando la ventana de documento del contenedor se activa o desactiva. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Notifica al control cuando se activa o desactiva ventana de marco de nivel superior del contenedor. Devuelve la implementación de ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informa al control que necesite cambiar el tamaño de sus bordes. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Procesa los mensajes de tecla de aceleración de menú del contenedor. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
  
## <a name="remarks"></a>Comentarios  
 El [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfaz ayuda a la comunicación entre un control in situ y su contenedor; por ejemplo, comunicando el estado activo del control y el contenedor y que informa el control debe cambiar el tamaño sí mismo. Clase `IOleInPlaceActiveObjectImpl` proporciona una implementación predeterminada de `IOleInPlaceActiveObject` y es compatible con **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Habilita la Ayuda contextual.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) en el SDK de Windows.  
  
##  <a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless  
 Permite cuadros de diálogo no modal.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) en el SDK de Windows.  
  
##  <a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow  
 El contenedor llama a esta función para obtener el identificador de ventana del control.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Comentarios  
 Algunos contenedores no funcionará con un control que haya estado sin ventana, incluso si está actualmente con ventanas. En la implementación de ATL, si la **CComControl::m_bWasOnceWindowless** miembro de datos es **TRUE**, la función devuelve **E_FAIL**. De lo contrario, si \* *phwnd* no **NULL**, `GetWindow` asigna *phwnd* al miembro de datos de la clase de control `m_hWnd` y devuelve `S_OK`.  
  
 Vea [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) en el SDK de Windows.  
  
##  <a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Notifica al control cuando la ventana de documento del contenedor se activa o desactiva.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceActiveObject:: OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) en el SDK de Windows.  
  
##  <a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Notifica al control cuando se activa o desactiva ventana de marco de nivel superior del contenedor.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceActiveObject:: Onframewindowactivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) en el SDK de Windows.  
  
##  <a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder  
 Informa al control que necesite cambiar el tamaño de sus bordes.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceActiveObject::](http://msdn.microsoft.com/library/windows/desktop/ms680053) en el SDK de Windows.  
  
##  <a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Procesa los mensajes de tecla de aceleración de menú del contenedor.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método admite los valores devueltos siguientes:  
  
 `S_OK`Si el mensaje ha sido traducido correctamente.  
  
 **S_FALSE** si el mensaje no ha sido traducido.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleInPlaceActiveObject:: TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CComControl (clase)](../../atl/reference/ccomcontrol-class.md)  
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Información general de clases](../../atl/atl-class-overview.md)
