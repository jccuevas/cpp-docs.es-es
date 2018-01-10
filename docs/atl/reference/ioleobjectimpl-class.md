---
title: Clase IOleObjectImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f710953a32ccb32c63742ab28e84818f3a330336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ioleobjectimpl-class"></a>Clase IOleObjectImpl
Esta clase implementa **IUnknown** y es la interfaz principal a través del cual un contenedor se comunica con un control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Establece una conexión de consulta con el control.|  
|[IOleObjectImpl::Close](#close)|Cambia el estado del control de ejecución a cargar.|  
|[IOleObjectImpl::DoVerb](#doverb)|Indica al control que realice una de las acciones enumeradas.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Indica al control para descartar cualquier estado de deshacer que mantiene.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Indica al control para quitar su interfaz de usuario de vista.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Se ejecuta el control y su ventana se instala, pero no instala la interfaz de usuario del control.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Hace que el control editarse a abrir en una ventana independiente.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Realiza la acción especificada cuando el usuario hace doble clic en el control. El control define la acción, normalmente para activar el control en contexto.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Muestra un control recién insertado para el usuario.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Activa el control en contexto y muestra la interfaz de usuario del control, como menús y barras de herramientas.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera las conexiones de consulta del control.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera las acciones para el control.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera el sitio de cliente del control.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera los datos desde el Portapapeles. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](#getextent)|Recupera la extensión del área de presentación del control.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera el estado del control.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera el moniker del control. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera el identificador de clase del control.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera el nombre de tipo de usuario del control.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa el control de datos seleccionado. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Comprueba si el control está actualizado. Devuelve la implementación de ATL `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Llamado por el método [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Llamado por el método [DoVerbHide](#doverbhide) después de que el control está oculto.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Llamado por el método [DoVerbInPlaceActivate](#doverbinplaceactivate) después de activa el control en su lugar.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Llamado por el método [DoVerbOpen](#doverbopen) después de que el control se ha abierto para su edición en una ventana independiente.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Llamado por el método [DoVerbShow](#doverbshow) después de que se ha realizado el control visible.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Llamado por el método [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Llamado por el método [DoVerbDiscardUndo](#doverbdiscardundo) antes de la anulación se descarta el estado.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Llamado por el método [DoVerbHide](#doverbhide) antes de que el control está oculto.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Llamado por el método [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control está activado en su lugar.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Llamado por el método [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para su edición en una ventana independiente.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Llamado por el método [DoVerbShow](#doverbshow) antes de que se ha realizado el control visible.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Llamado por el método [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Indica el control sobre su sitio de cliente en el contenedor.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recomienda una combinación de colores a la aplicación del control, si existe. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](#setextent)|Establece la extensión del área de presentación del control.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Indica que el control a los nombres de la aplicación de contenedor y el documento contenedor.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Indica al control ¿cuál es su moniker. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Elimina una conexión de consulta con el control.|  
|[IOleObjectImpl::Update](#update)|Actualiza el control. Devuelve la implementación de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentarios  
 El [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) es la interfaz principal a través del cual un contenedor se comunica con un control. Clase `IOleObjectImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
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
 Vea [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) en el SDK de Windows.  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 Cambia el estado del control de ejecución a cargar.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Comentarios  
 Desactiva el control y destruye la ventana de control, si existe. Si el control de clase miembro de datos [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) es **TRUE** y `dwSaveOption` parámetro sea `OLECLOSE_SAVEIFDIRTY` o `OLECLOSE_PROMPTSAVE`, se guardan las propiedades del control antes de cerrarse.  
  
 Los punteros se mantienen en los miembros de datos de la clase de control [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) y [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) se liberan y los miembros de datos [CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), y [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) se establecen en **FALSE**.  
  
 Vea [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) en el SDK de Windows.  
  
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
 Dependiendo del valor de `iVerb`, uno de la biblioteca ATL `DoVerb` funciones auxiliares se llama como sigue:  
  
|*iVerb* valor|Función auxiliar de DoVerb llama|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 Vea [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) en el SDK de Windows.  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 Indica al control para descartar cualquier estado de deshacer que mantiene.  
  
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
 Se ejecuta el control y su ventana se instala, pero no instala la interfaz de usuario del control.  
  
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
 Activa el control en su lugar mediante una llamada a [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que el miembro de datos de la clase de control `m_bWindowOnly` es **TRUE**, `DoVerbInPlaceActivate` primero intenta activar el control como un control sin ventana (posible únicamente si el contenedor admite [IOleInPlaceSiteWindowless ](http://msdn.microsoft.com/library/windows/desktop/ms682300)). Si se produce un error, la función intenta activar el control con características extendidas (posible únicamente si el contenedor admite [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). Si se produce un error, la función intenta activar el control con ninguna característica extendida (posible únicamente si el contenedor admite [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Si la activación se realiza correctamente, la función notifica el contenedor que se ha activado el control.  
  
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
 De forma predeterminada, establecido para mostrar las páginas de propiedades. Puede invalidar esto en la clase del control para invocar un comportamiento diferente con doble clic; Por ejemplo, reproducir un vídeo o visite activo en contexto.  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 Indica el contenedor para que el control sea visible.  
  
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
 Activa la interfaz de usuario del control y notifica al contenedor que están siendo remplazados sus menús con menús compuestos.  
  
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
 Proporciona una enumeración de conexiones de consulta registradas para este control.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) en el SDK de Windows.  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 Proporciona una enumeración de las acciones registradas (verbos) para este control mediante una llamada a **OleRegEnumVerbs**.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Comentarios  
 Puede agregar verbos para el archivo del proyecto .rgs. Por ejemplo, vea CIRCCTL. RGS en el [CIRC](../../visual-cpp-samples.md) ejemplo.  
  
 Vea [IOleObject:: EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) en el SDK de Windows.  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 Coloca el puntero en el miembro de datos de la clase de control [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) en *ppClientSite* e incrementa el recuento de referencias en el puntero.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) en el SDK de Windows.  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 Recupera los datos desde el Portapapeles.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) en el SDK de Windows.  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 Recupera el tamaño de presentación de un control que se ejecuta en unidades HIMETRIC (0,01 milímetros por unidad).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño se almacena en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 Vea [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) en el SDK de Windows.  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 Devuelve un puntero a la información de estado registrados para el control mediante una llamada a **OleRegGetMiscStatus**.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Comentarios  
 La información de estado incluye comportamientos compatibles con el control y la presentación de datos. Puede agregar información de estado para el archivo del proyecto .rgs.  
  
 Vea [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) en el SDK de Windows.  
  
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
 Vea [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) en el SDK de Windows.  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 Devuelve el identificador de clase del control.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) en el SDK de Windows.  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 Devuelve el nombre de tipo de usuario del control mediante una llamada a **OleRegGetUserType**.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Comentarios  
 El nombre del tipo de usuario se usa para mostrar en elementos de interfaces de usuario como menús y cuadros de diálogo. Puede cambiar el nombre de tipo de usuario en el archivo del proyecto .rgs.  
  
 Vea [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) en el SDK de Windows.  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 Inicializa el control de datos seleccionado.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) en el SDK de Windows.  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 Comprueba si el control está actualizado.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) en el SDK de Windows.  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 Llamado por el método [DoVerbDiscardUndo](#doverbdiscardundo) después de que se descarta el estado de deshacer.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que se descarta el estado de deshacer.  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 Llamado por el método [DoVerbHide](#doverbhide) después de que el control está oculto.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que el control está oculto.  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 Llamado por el método [DoVerbInPlaceActivate](#doverbinplaceactivate) después de activa el control en su lugar.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que el control está activado en su lugar.  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 Llamado por el método [DoVerbOpen](#doverbopen) después de que el control se ha abierto para su edición en una ventana independiente.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que el control se ha abierto para su edición en una ventana independiente.  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 Llamado por el método [DoVerbShow](#doverbshow) después de que se ha realizado el control visible.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que se ha realizado el control visible.  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 Llamado por el método [DoVerbUIActivate](#doverbuiactivate) después de activar la interfaz de usuario del control.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con código que quiere que se ejecuta después de que se ha activado la interfaz de usuario del control.  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 Llamado por el método [DoVerbDiscardUndo](#doverbdiscardundo) antes de la anulación se descarta el estado.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el estado de deshacer que se descartan, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 Llamado por el método [DoVerbHide](#doverbhide) antes de que el control está oculto.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control está oculto, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 Llamado por el método [DoVerbInPlaceActivate](#doverbinplaceactivate) antes de que el control está activado en su lugar.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control está activado en su lugar, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 Llamado por el método [DoVerbOpen](#doverbopen) antes de que el control se ha abierto para su edición en una ventana independiente.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control se abre para su edición en una ventana independiente, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 Llamado por el método [DoVerbShow](#doverbshow) antes de que se ha realizado el control visible.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que el control que se hacen visibles, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 Llamado por el método [DoVerbUIActivate](#doverbuiactivate) antes de que se ha activado la interfaz de usuario del control.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Para evitar que la interfaz de usuario del control está activado, invalide este método para devolver un valor HRESULT de error.  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 Indica el control sobre su sitio de cliente en el contenedor.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Comentarios  
 A continuación, devuelve el método `S_OK`.  
  
 Vea [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) en el SDK de Windows.  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 Recomienda una combinación de colores a la aplicación del control, si existe.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) en el SDK de Windows.  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 Establece la extensión del área de presentación del control.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentarios  
 En caso contrario, `SetExtent` almacena el valor que señala `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Este valor está en unidades HIMETRIC (0,01 milímetros por unidad).  
  
 Si el control de clase miembro de datos [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) es **TRUE**, `SetExtent` también almacena el valor al que señala `psizel` en el miembro de datos de clase de control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Si el control de clase miembro de datos [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) es **TRUE**, `SetExtent` llamadas `SendOnDataChange` y `SendOnViewChange` para notificar a todos los receptores de consultas registrados con el aconseje a titular que ha cambiado el tamaño del control.  
  
 Vea [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) en el SDK de Windows.  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 Indica que el control a los nombres de la aplicación de contenedor y el documento contenedor.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) en el SDK de Windows.  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 Indica al control ¿cuál es su moniker.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) en el SDK de Windows.  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 Elimina la conexión de consulta almacenada en la clase de control `m_spOleAdviseHolder` miembro de datos.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) en el SDK de Windows.  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 Actualiza el control.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Información general de clases](../../atl/atl-class-overview.md)
