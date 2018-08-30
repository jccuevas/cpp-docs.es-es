---
title: IOleInPlaceActiveObjectImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f92408c8d8ee4ac1dd1309810ae6282f04ca315
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213328"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl (clase)
Esta clase proporciona métodos para ayudar a la comunicación entre un control in situ y su contenedor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la Ayuda contextual. La implementación de ATL devuelve E_NOTIMPL.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permite a los cuadros de diálogo no modal. La implementación de ATL devuelve S_OK.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Notifica al control cuando la ventana de documento del contenedor se activa o desactiva. La implementación de ATL devuelve S_OK.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Notifica al control cuando la ventana de marco de nivel superior del contenedor se activa o desactiva. Devuelve la implementación de ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informa al control que debe cambiar el tamaño de sus bordes. La implementación de ATL devuelve S_OK.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Procesa los mensajes de tecla de aceleración de menú del contenedor. La implementación de ATL devuelve E_NOTIMPL.|  
  
  
## <a name="remarks"></a>Comentarios  
 El [IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject) interfaz facilita la comunicación entre un control in situ y su contenedor; por ejemplo, comunica el estado activo del control y el contenedor e informa el control debe cambiar el tamaño Sí. Clase `IOleInPlaceActiveObjectImpl` proporciona una implementación predeterminada de `IOleInPlaceActiveObject` y es compatible con `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Habilita la Ayuda contextual.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve E_NOTIMPL.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) en el SDK de Windows.  
  
##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless  
 Permite a los cuadros de diálogo no modal.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) en el SDK de Windows.  
  
##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow  
 El contenedor llama a esta función para obtener el identificador de ventana del control.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Comentarios  
 Algunos contenedores no funcionará con un control que ha sido sin ventanas, incluso si es actualmente con ventanas. En la implementación de ATL, si la `CComControl::m_bWasOnceWindowless` miembro de datos es TRUE, la función devuelve E_FAIL. De lo contrario, si \* *phwnd* no es NULL, `GetWindow` asigna *phwnd* al miembro de datos de la clase control `m_hWnd` y devuelve S_OK.  
  
 Consulte [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) en el SDK de Windows.  
  
##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Notifica al control cuando la ventana de documento del contenedor se activa o desactiva.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) en el SDK de Windows.  
  
##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Notifica al control cuando la ventana de marco de nivel superior del contenedor se activa o desactiva.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) en el SDK de Windows.  
  
##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder  
 Informa al control que debe cambiar el tamaño de sus bordes.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) en el SDK de Windows.  
  
##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Procesa los mensajes de tecla de aceleración de menú del contenedor.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método admite los valores devueltos siguientes:  
  
 S_OK si el mensaje se ha traducido correctamente.  
  
 S_FALSE si no se ha traducido el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CComControl (clase)](../../atl/reference/ccomcontrol-class.md)  
 [Interfaces de controles ActiveX](/windows/desktop/com/activex-controls-interfaces)  
 [Información general de clases](../../atl/atl-class-overview.md)
