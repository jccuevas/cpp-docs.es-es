---
title: Clase IPropertyPageImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyPageImpl
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: 21
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
ms.openlocfilehash: 1179e13eb33f09a363c7a3f4425a9ebf13c73b91
ms.lasthandoff: 02/24/2017

---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl (clase)
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPropertyPageImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl](#activate)|Crea la ventana del cuadro de diálogo página de propiedades.|  
|[IPropertyPageImpl:: Apply](#apply)|Se aplica a valores de la página de propiedad actuales a los objetos subyacentes especificados a través de `SetObjects`. Devuelve la implementación de ATL `S_OK`.|  
|[IPropertyPageImpl::Deactivate](#deactivate)|Destruye la ventana creada con **activar**.|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Recupera información acerca de la página de propiedades.|  
|[IPropertyPageImpl::Help](#help)|Invoca la Ayuda de Windows para la página de propiedades.|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Indica si la página de propiedad ha cambiado desde que se activó.|  
|[IPropertyPageImpl::Move](#move)|Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.|  
|[IPropertyPageImpl:: SetDirty](#setdirty)|Indicadores de estado de la página de propiedades como modificado o no modificado.|  
|[SetObjects](#setobjects)|Proporciona una matriz de **IUnknown** punteros para los objetos asociados a la página de propiedades. Estos objetos reciben los valores de la página de propiedad actuales a través de una llamada a **aplicar**.|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Proporciona la página de propiedades con un `IPropertyPageSite` puntero, a través del cual la página de propiedades se comunica con el marco de propiedad.|  
|[IPropertyPageImpl::Show](#show)|Hace que el cuadro de diálogo de la página de propiedades visible o invisible.|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Procesa una pulsación de tecla especificada.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Especifica si el estado de la página de propiedad ha cambiado.|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Almacena el identificador de recurso asociado a la cadena de texto que describe la página de propiedades.|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Almacena el identificador de contexto del tema de ayuda asociado a la página de propiedades.|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Almacena el identificador de recurso asociado a la cadena de texto que aparece en la ficha de la página de propiedades.|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Almacena el número de objetos asociados a la página de propiedades.|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Apunta a la `IPropertyPageSite` a través del cual la página de propiedades se comunica con el marco de propiedad de interfaz.|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Apunta a una matriz de **IUnknown** punteros a los objetos asociados a la página de propiedades.|  
|[IPropertyPageImpl::m_size](#m_size)|Almacena el alto y ancho de la página de propiedades cuadro de diálogo, en píxeles.|  
  
## <a name="remarks"></a>Comentarios  
 El [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interfaz permite que un objeto administrar una determinada página de propiedades dentro de una hoja de propiedades. Clase `IPropertyPageImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="a-nameactivatea--ipropertypageimplactivate"></a><a name="activate"></a>IPropertyPageImpl  
 Crea la ventana del cuadro de diálogo página de propiedades.  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el cuadro de diálogo siempre es no modal, independientemente del valor de la *bModal* parámetro.  
  
 Consulte [IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameapplya--ipropertypageimplapply"></a><a name="apply"></a>IPropertyPageImpl:: Apply  
 Se aplica a valores de la página de propiedad actuales a los objetos subyacentes especificados a través de `SetObjects`.  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namedeactivatea--ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Deactivate  
 Destruye la ventana del cuadro de diálogo creada con [activar](#activate).  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetpageinfoa--ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo  
 Rellena el *pPageInfo* estructura con la información contenida en los miembros de datos.  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Comentarios  
 `GetPageInfo`carga los recursos de cadena asociados [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), y [m_dwTitle](#m_dwtitle).  
  
 Consulte [IPropertyPage:: GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namehelpa--ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Help  
 Invoca la Ayuda de Windows para la página de propiedades.  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameipropertypageimpla--ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl  
 El constructor.  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a todos los miembros de datos.  
  
##  <a name="a-nameispagedirtya--ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty  
 Indica si la página de propiedad ha cambiado desde que se activó.  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>Comentarios  
 `IsPageDirty`Devuelve `S_OK` si la página ha cambiado desde que se activó.  
  
##  <a name="a-namembdirtya--ipropertypageimplmbdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty  
 Especifica si el estado de la página de propiedad ha cambiado.  
  
```
BOOL m_bDirty;
```  
  
##  <a name="a-namemnobjectsa--ipropertypageimplmnobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects  
 Almacena el número de objetos asociados a la página de propiedades.  
  
```
ULONG m_nObjects;
```  
  
##  <a name="a-namemdwhelpcontexta--ipropertypageimplmdwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext  
 Almacena el identificador de contexto del tema de ayuda asociado a la página de propiedades.  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="a-namemdwdocstringa--ipropertypageimplmdwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString  
 Almacena el identificador de recurso asociado a la cadena de texto que describe la página de propiedades.  
  
```
UINT m_dwDocString;
```  
  
##  <a name="a-namemdwhelpfilea--ipropertypageimplmdwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile  
 Almacena el identificador de recurso asociado con el nombre del archivo de ayuda que describe la página de propiedades.  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="a-namemdwtitlea--ipropertypageimplmdwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle  
 Almacena el identificador de recurso asociado a la cadena de texto que aparece en la ficha de la página de propiedades.  
  
```
UINT m_dwTitle;
```  
  
##  <a name="a-namemppagesitea--ipropertypageimplmppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite  
 Apunta a la [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) a través del cual la página de propiedades se comunica con el marco de propiedad de interfaz.  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="a-namemppunka--ipropertypageimplmppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk  
 Apunta a una matriz de **IUnknown** punteros a los objetos asociados a la página de propiedades.  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="a-namemsizea--ipropertypageimplmsize"></a><a name="m_size"></a>IPropertyPageImpl::m_size  
 Almacena el alto y ancho de la página de propiedades cuadro de diálogo, en píxeles.  
  
```
SIZE m_size;
```  
  
##  <a name="a-namemovea--ipropertypageimplmove"></a><a name="move"></a>IPropertyPageImpl::Move  
 Coloca y cambia el tamaño del cuadro de diálogo de la página de propiedades.  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetdirtya--ipropertypageimplsetdirty"></a><a name="setdirty"></a>IPropertyPageImpl:: SetDirty  
 Indicadores de estado de la página de propiedades como modificado o no modificado, según el valor de `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDirty`  
 [in] Si **TRUE**, estado de la página de propiedad está marcado como modificada. De lo contrario, se marca como sin cambios.  
  
### <a name="remarks"></a>Comentarios  
 Si es necesario, `SetDirty` informa el marco de la página de propiedad ha cambiado.  
  
##  <a name="a-namesetobjectsa--ipropertypageimplsetobjects"></a><a name="setobjects"></a>SetObjects  
 Proporciona una matriz de **IUnknown** punteros para los objetos asociados a la página de propiedades.  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetpagesitea--ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>IPropertyPageImpl::SetPageSite  
 Proporciona la página de propiedades con un [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) puntero, a través del cual la página de propiedades se comunica con el marco de propiedad.  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameshowa--ipropertypageimplshow"></a><a name="show"></a>IPropertyPageImpl::Show  
 Hace que el cuadro de diálogo de la página de propiedades visible o invisible.  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nametranslateacceleratora--ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator  
 Procesa la tecla especificada en `pMsg`.  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)   
 [Clase IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Clase de ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

