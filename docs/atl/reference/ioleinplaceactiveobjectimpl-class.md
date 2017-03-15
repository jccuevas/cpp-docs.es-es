---
title: Clase IOleInPlaceActiveObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 766ac40bb0a09902914feab1acc54a960261a768
ms.lasthandoff: 02/24/2017

---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Clase IOleInPlaceActiveObjectImpl
Esta clase proporciona métodos para ayudar a la comunicación entre un control in situ y su contenedor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Habilita la Ayuda contextual. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permite a los cuadros de diálogo no modal. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtiene un identificador de ventana.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Notifica al control cuando se activa o se desactiva la ventana de documento del contenedor. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Notifica al control cuando se activa o se desactiva la ventana de marco de nivel superior del contenedor. Devuelve la implementación de ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informa al control debe cambiar el tamaño de sus bordes. Devuelve la implementación de ATL `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Procesa los mensajes de tecla de método abreviado de menú del contenedor. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
  
## <a name="remarks"></a>Comentarios  
 El [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interfaz facilita la comunicación entre un control in situ y su contenedor; por ejemplo, comunicando el estado activo del control y el contenedor y que informa el control necesita cambiar de tamaño. Clase `IOleInPlaceActiveObjectImpl` proporciona una implementación predeterminada de `IOleInPlaceActiveObject` y es compatible con **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="a-namecontextsensitivehelpa--ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Habilita la Ayuda contextual.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameenablemodelessa--ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless  
 Permite a los cuadros de diálogo no modal.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetwindowa--ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow  
 El contenedor llama a esta función para obtener el identificador de ventana del control.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Comentarios  
 Algunos contenedores no funcionará con un control que ha estado sin ventana, aunque sea actualmente con ventanas. En la implementación de ATL, si la **CComControl::m_bWasOnceWindowless** miembro de datos es **TRUE**, la función devuelve **E_FAIL**. De lo contrario, si \* *phwnd* no **NULL**, `GetWindow` asigna *phwnd* al miembro de datos de la clase control `m_hWnd` y devuelve `S_OK`.  
  
 Consulte [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameondocwindowactivatea--ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Notifica al control cuando se activa o se desactiva la ventana de documento del contenedor.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameonframewindowactivatea--ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Notifica al control cuando se activa o se desactiva la ventana de marco de nivel superior del contenedor.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameresizebordera--ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder  
 Informa al control debe cambiar el tamaño de sus bordes.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nametranslateacceleratora--ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Procesa los mensajes de tecla de método abreviado de menú del contenedor.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método admite los valores devueltos siguientes:  
  
 `S_OK`Si el mensaje se ha traducido correctamente.  
  
 **S_FALSE** si el mensaje no se ha traducido.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)  
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Información general de la clase](../../atl/atl-class-overview.md)

