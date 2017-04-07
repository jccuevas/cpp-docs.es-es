---
title: Clase IViewObjectExImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 20
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
ms.openlocfilehash: 2b585a056324507cc631e64e6dbe9d0ed610361d
ms.lasthandoff: 02/24/2017

---
# <a name="iviewobjecteximpl-class"></a>Clase IViewObjectExImpl
Esta clase implementa **IUnknown** y proporciona implementaciones predeterminadas de la [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), y [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) interfaces.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IViewObjectExImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|Dibuja una representación del control en un contexto de dispositivo.|  
|[IViewObjectExImpl::Freeze](#freeze)|Se bloquea la representación de un control dibujada por lo que no cambiarán hasta un `Unfreeze`. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|Recupera una conexión de receptor de consulta existente en el control, si hay alguno.|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Devuelve la paleta lógica utilizada por el control para dibujar. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetExtent](#getextent)|Recupera el tamaño de presentación del control en unidades HIMETRIC (0,01 milímetros por unidad) desde el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Proporciona sugerencias de ajuste de tamaño del contenedor para el objeto que se va a usar como el usuario lo modifica.|  
|[IViewObjectExImpl::GetRect](#getrect)|Devuelve un rectángulo que describe un aspecto de dibujo solicitado. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Devuelve información acerca de la opacidad del objeto y qué aspectos de dibujo se admiten.|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Comprueba si el punto especificado está en el rectángulo especificado y devuelve un [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) valor en `pHitResult`.|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Comprueba si el rectángulo de presentación del control superpone a cualquier punto en el rectángulo de la ubicación especificada y devuelve un **HITRESULT** valor en `pHitResult`.|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|Establece una conexión entre el control y un receptor con notificación por lo que el receptor puede recibir notificaciones de cambios en la vista del control.|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Libera la representación del control dibujada. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 El [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), y [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) interfaces permiten un control para que se muestre directamente y crear y administrar un receptor con notificación para notificar al contenedor de los cambios en la presentación del control. El **IViewObjectEx** interfaz proporciona compatibilidad para las características de control extendido como dibujar parpadeo, controles transparentes y no rectangulares y prueba de posicionamiento (por ejemplo, cómo cerrar un clic del mouse debe considerarse en el control). Clase `IViewObjectExImpl` proporciona una implementación predeterminada de estas interfaces e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="draw"></a>IViewObjectExImpl::Draw  
 Dibuja una representación del control en un contexto de dispositivo.  
  
```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a **CComControl::OnDrawAdvanced** que a su vez llama a su clase de control `OnDraw` (método). Un `OnDraw` método se agrega automáticamente a la clase del control cuando se crea el control con el Asistente para controles ATL. Valor predeterminado del asistente `OnDraw` dibuja un rectángulo con la etiqueta "ATL 3.0".  
  
 Consulte [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="freeze"></a>IViewObjectExImpl::Freeze  
 Se bloquea la representación de un control dibujada por lo que no cambiarán hasta un `Unfreeze`. Devuelve la implementación de ATL **E_NOTIMPL**.  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 Recupera una conexión de receptor de consulta existente en el control, si hay alguno.  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>Comentarios  
 El receptor de consulta se almacena en el miembro de datos de la clase de control [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).  
  
 Consulte [IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 Devuelve la paleta lógica utilizada por el control para dibujar. Devuelve la implementación de ATL **E_NOTIMPL**.  
  
```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getextent"></a>IViewObjectExImpl::GetExtent  
 Recupera el tamaño de presentación del control en unidades HIMETRIC (0,01 milímetros por unidad) desde el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent  
 Proporciona sugerencias de ajuste de tamaño del contenedor para el objeto que se va a usar como el usuario lo modifica.  
  
```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="remarks"></a>Comentarios  
 Si `dwAspect` es `DVASPECT_CONTENT` y *pExtentInfo-> dwExtentMode* es **DVEXTENT_CONTENT**, establece * `psizel` al miembro de datos de la clase control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). De lo contrario, devuelve un error `HRESULT`.  
  
 Consulte [IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getrect"></a>IViewObjectExImpl::GetRect  
 Devuelve un rectángulo que describe un aspecto de dibujo solicitado. Devuelve la implementación de ATL **E_NOTIMPL**.  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 Devuelve información acerca de la opacidad del objeto y qué aspectos de dibujo se admiten.  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, se establece ATL `pdwStatus` para indicar que el control admite **VIEWSTATUS_OPAQUE** (los valores posibles son en el [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) enumeración).  
  
 Consulte [IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 Comprueba si el punto especificado está en el rectángulo especificado y devuelve un [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) valor en `pHitResult`.  
  
```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Comentarios  
 El valor puede ser **HITRESULT_HIT** o **HITRESULT_OUTSIDE**.  
  
 Si `dwAspect` es igual a [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), el método devuelve `S_OK`. De lo contrario, el método devuelve **E_FAIL**.  
  
 Consulte [IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 Comprueba si el rectángulo de presentación del control superpone a cualquier punto en el rectángulo de la ubicación especificada y devuelve un [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) valor en `pHitResult`.  
  
```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Comentarios  
 El valor puede ser **HITRESULT_HIT** o **HITRESULT_OUTSIDE**.  
  
 Si `dwAspect` es igual a [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), el método devuelve `S_OK`. De lo contrario, el método devuelve **E_FAIL**.  
  
 Consulte [IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 Establece una conexión entre el control y un receptor con notificación por lo que el receptor puede recibir notificaciones de cambios en la vista del control.  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>Comentarios  

 El puntero a la [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfaz al receptor con notificación se almacena en el miembro de datos de la clase de control [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).  

  
 Consulte [IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 Libera la representación del control dibujada. Devuelve la implementación de ATL **E_NOTIMPL**.  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 Implemente este método para cerrar el identificador asociado a este objeto.  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>Parámetros  
 *hHandle*  
 El identificador se cierra.  
  
### <a name="return-value"></a>Valor devuelto  
 Éxito o un error HRESULT en caso contrario, devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 El identificador pasado a este método se ha asociado previamente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Ejemplo  
 El código siguiente muestra una implementación sencilla de `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities&#135;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwParam`  
 El parámetro de usuario.  
  
 `hObject`  
 El identificador que se convertirá en señalado.  
  
### <a name="return-value"></a>Valor devuelto  
 Éxito o un error HRESULT en caso contrario, devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 El identificador y se pasa a este método DWORD o puntero estaban asociados anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Ejemplo  
 El código siguiente muestra una implementación sencilla de `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities&#136;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Tutorial](../../atl/active-template-library-atl-tutorial.md)   
 [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

