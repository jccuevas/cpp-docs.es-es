---
title: Clase IOleObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
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
ms.openlocfilehash: b0b471b997bfdb4062f00b40864c347db78b114a
ms.lasthandoff: 02/24/2017

---
# <a name="ioleobjectimpl-class"></a>Clase IOleObjectImpl
Esta clase implementa **IUnknown** y es la interfaz principal a través del cual se comunica un contenedor con un control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IOleObjectImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Establece una conexión de consulta con el control.|  
|[IOleObjectImpl::Close](#close)|Cambia el estado de control de ejecución para cargar.|  
|[IOleObjectImpl::DoVerb](#doverb)|Indica al control que realice una de las acciones enumeradas.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indica el control que se va a descartar cualquier estado de deshacer que mantiene.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indica el control que se va a quitar de la interfaz de usuario de la vista.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Ejecuta el control e instala su ventana, pero no instalar la interfaz de usuario del control.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Hace que el control editarse a abrir en una ventana independiente.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Realiza la acción especificada cuando el usuario hace doble clic en el control. El control define la acción, normalmente para activar el control en contexto.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Muestra un control recién insertado para el usuario.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Activa el control in situ y muestra la interfaz de usuario del control, como menús y barras de herramientas.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera las conexiones de consulta del control.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera las acciones para el control.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera el sitio de cliente del control.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera datos del Portapapeles. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](#getextent)|Recupera la extensión del área de presentación del control.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera el estado del control.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera el moniker del control. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera el identificador de clase del control.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera el nombre de tipo de usuario del control.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa el control de datos seleccionados. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Comprueba si el control está actualizado. Devuelve la implementación de ATL `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Llama a [DoVerbDiscardUndo](#doverbdiscardundo) una vez descartado el estado de deshacer.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Llama a [DoVerbHide](#doverbhide) después de que el control está oculto.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Llama a [DoVerbInPlaceActivate](#doverbinplaceactivate) después de que el control se activa en contexto.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Llama a [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Llama a [DoVerbShow](#doverbshow) después de que el control se ha hecho visible.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Llama a [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Llama a [DoVerbDiscardUndo](#doverbdiscardundo) antes de la anulación se descarta el estado.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Llama a [DoVerbHide](#doverbhide) antes de que el control está oculto.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Llama a [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control se activa en contexto.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Llama a [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para editarlo en una ventana independiente.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Llama a [DoVerbShow](#doverbshow) antes de que el control se ha hecho visible.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Llama a [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indica el control sobre su sitio de cliente en el contenedor.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recomienda una combinación de colores a la aplicación del control, si existe. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](#setextent)|Establece la extensión del área de presentación del control.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indica que el control a los nombres de la aplicación contenedora y el documento contenedor.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indica que el control de su moniker que es. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Elimina una conexión de consulta con el control.|  
|[IOleObjectImpl::Update](#update)|Actualiza el control. Devuelve la implementación de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentarios  
 El [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) es la interfaz principal a través del cual se comunica un contenedor con un control. Clase `IOleObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 Establece una conexión de consulta con el control.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 Cambia el estado de control de ejecución para cargar.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Comentarios  
 Desactiva el control y destruye la ventana de control, si existe. Si el control de clase de miembro de datos [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) es **TRUE** y `dwSaveOption` parámetro sea `OLECLOSE_SAVEIFDIRTY` o `OLECLOSE_PROMPTSAVE`, las propiedades del control se guardan antes de cerrarse.  
  
 Los punteros se mantienen en los miembros de datos de la clase de control [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) y [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) se liberan y los miembros de datos [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), y [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) se establecen en **FALSE**.  
  
 Consulte [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 Indica al control que realice una de las acciones enumeradas.  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>Comentarios  
 Dependiendo del valor de `iVerb`, uno de ATL `DoVerb` funciones auxiliares se llama como sigue:  
  
|*iVerb* valor|Función auxiliar de DoVerb llamada|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 Consulte [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 Indica el control que se va a descartar cualquier estado de deshacer que mantiene.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
##  <a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 Desactiva y quita la interfaz de usuario del control y oculta el control.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 Ejecuta el control e instala su ventana, pero no instalar la interfaz de usuario del control.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 Activa el control en su lugar mediante una llamada a [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que el miembro de datos de la clase control `m_bWindowOnly` es **TRUE**, `DoVerbInPlaceActivate` primero intenta activar el control como un control sin ventana (posible únicamente si el contenedor admite [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)). Si se produce un error, la función intenta activar el control con características extendidas (posible únicamente si el contenedor admite [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). Si se produce un error, la función intenta activar el control con ninguna característica extendida (posible únicamente si el contenedor admite [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Si la activación se realiza correctamente, la función notifica el contenedor que se ha activado el control.  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 Hace que el control editarse a abrir en una ventana independiente.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
##  <a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 Define la acción realizada cuando el usuario hace doble clic en el control.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, establecido para mostrar las páginas de propiedades. Puede invalidar esto en su clase de control para invocar un comportamiento diferente con doble clic; Por ejemplo, reproducir un vídeo o visite activo en contexto.  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 Indica al contenedor para hacer visible el control.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 Activa la interfaz de usuario del control y notifica al contenedor que los menús están siendo remplazados por menús compuestos.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parámetros  
 `prcPosRec`  
 [in] Puntero al rectángulo el contenedor desea dibujar en el control.  
  
 *hwndParent*  
 [in] Identificador de la ventana que contiene el control. No se utiliza en la implementación de ATL.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 Proporciona una enumeración de las conexiones de consulta registradas para este control.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 Proporciona una enumeración de las acciones registradas (verbos) para este control mediante una llamada a **OleRegEnumVerbs**.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Comentarios  
 Puede agregar verbos al archivo del proyecto. Por ejemplo, vea CIRCCTL. RGS en el [CIRC](../../visual-cpp-samples.md) ejemplo.  
  
 Consulte [IOleObject:: EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 Coloca el puntero en el miembro de datos de la clase de control [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* e incrementa el recuento de referencias del puntero.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 Recupera datos del Portapapeles.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 Recupera el tamaño de presentación de un control que se ejecuta en unidades HIMETRIC (0,01 milímetros por unidad).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño se almacena en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 Consulte [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 Devuelve un puntero a la información de estado de registro para el control mediante una llamada a **OleRegGetMiscStatus**.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Comentarios  
 La información de estado incluye comportamientos admitidos por los datos de control y la presentación. Puede agregar información de estado para el archivo del proyecto.  
  
 Consulte [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 Recupera el moniker del control.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 Devuelve el identificador de clase del control.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 Devuelve el nombre de tipo de usuario del control mediante una llamada a **OleRegGetUserType**.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Comentarios  
 El nombre del tipo de usuario se utiliza para mostrar elementos de interfaces de usuario, como menús y cuadros de diálogo. Puede cambiar el nombre de tipo de usuario en el archivo del proyecto.  
  
 Consulte [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 Inicializa el control de datos seleccionados.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 Comprueba si el control está actualizado.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 Llama a [DoVerbDiscardUndo](#doverbdiscardundo) una vez descartado el estado de deshacer.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desea ejecutado una vez descartado el estado de deshacer.  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 Llama a [DoVerbHide](#doverbhide) después de que el control está oculto.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desee ejecutado después de que el control está oculto.  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 Llama a [DoVerbInPlaceActivate](#doverbinplaceactivate) después de que el control se activa en contexto.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desee ejecutado después de que el control se activa en contexto.  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 Llama a [DoVerbOpen](#doverbopen) después de que el control se ha abierto para editarlo en una ventana independiente.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desee ejecutar después de que el control se ha abierto para editarlo en una ventana independiente.  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 Llama a [DoVerbShow](#doverbshow) después de que el control se ha hecho visible.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desee ejecutar después de que el control se ha hecho visible.  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 Llama a [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con el código que desee ejecutar después de que se ha activado la interfaz de usuario del control.  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 Llama a [DoVerbDiscardUndo](#doverbdiscardundo) antes de la anulación se descarta el estado.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el estado de deshacer descartados, invalide este método para devolver un error HRESULT.  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 Llama a [DoVerbHide](#doverbhide) antes de que el control está oculto.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control está oculto, invalide este método para devolver un error HRESULT.  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 Llama a [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control se activa en contexto.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control está activado en su lugar, invalide este método para devolver un error HRESULT.  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 Llama a [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para editarlo en una ventana independiente.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control que se va a abrir para editarlo en una ventana independiente, invalide este método para devolver un error HRESULT.  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 Llama a [DoVerbShow](#doverbshow) antes de que el control se ha hecho visible.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control está visible, invalide este método para devolver un error HRESULT.  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 Llama a [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que la interfaz de usuario del control está activado, invalide este método para devolver un error HRESULT.  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 Indica el control sobre su sitio de cliente en el contenedor.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Comentarios  
 El método devuelve `S_OK`.  
  
 Consulte [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 Recomienda una combinación de colores a la aplicación del control, si existe.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 Establece la extensión del área de presentación del control.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentarios  
 De lo contrario, `SetExtent` almacena el valor al que señala `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Este valor está en unidades HIMETRIC (0,01 milímetros por unidad).  
  
 Si el control de clase de miembro de datos [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) es **TRUE**, `SetExtent` también almacena el valor al que señala `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Si el control de clase de miembro de datos [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) es **TRUE**, `SetExtent` llamadas `SendOnDataChange` y `SendOnViewChange` para notificar a los receptores de todas las consultas registrados con el titular de la notificación que ha cambiado el tamaño del control.  
  
 Consulte [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 Indica que el control a los nombres de la aplicación contenedora y el documento contenedor.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 Indica que el control de su moniker que es.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 Elimina la conexión de consulta almacenada en la clase de control `m_spOleAdviseHolder` miembro de datos.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 Actualiza el control.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Información general de la clase](../../atl/atl-class-overview.md)

