---
title: Clase IObjectWithSiteImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IObjectWithSiteImpl
- ATL.IObjectWithSiteImpl<T>
- IObjectWithSiteImpl
- ATL.IObjectWithSiteImpl
- ATL::IObjectWithSiteImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: 18
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
ms.openlocfilehash: 49c52810417650c3d80fe4d0c09ccb2b67208ad4
ms.lasthandoff: 02/24/2017

---
# <a name="iobjectwithsiteimpl-class"></a>Clase IObjectWithSiteImpl
Esta clase proporciona métodos que permiten a un objeto para comunicarse con su sitio.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IObjectWithSiteImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Consulta el sitio para un puntero de interfaz.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Proporciona el objeto con el sitio **IUnknown** puntero.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Proporciona el objeto con el sitio **IUnknown** puntero.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Administra el sitio **IUnknown** puntero.|  
  
## <a name="remarks"></a>Comentarios  
 El [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) interfaz permite que un objeto para comunicarse con su sitio. Clase `IObjectWithSiteImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 `IObjectWithSiteImpl`Especifica dos métodos. El cliente llama primero `SetSite`, pasando el sitio **IUnknown** puntero. Este puntero se almacena dentro del objeto y se puede recuperar después mediante una llamada a `GetSite`.  
  
 Normalmente, derivar su clase de `IObjectWithSiteImpl` cuando se crea un objeto que no es un control. Para los controles, derive la clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio. No derive la clase de ambos `IObjectWithSiteImpl` y `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-namegetsitea--iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite  
 Consulta el sitio para un puntero a la interfaz identificada por `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Si el sitio admite esta interfaz, se devuelve el puntero a través de `ppvSite`. De lo contrario, `ppvSite` está establecido en **NULL**.  
  
 Consulte [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namemspunksitea--iobjectwithsiteimplmspunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite  
 Administra el sitio **IUnknown** puntero.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Comentarios  
 `m_spUnkSite`Recibe inicialmente este puntero mediante una llamada a [SetSite](#setsite).  
  
##  <a name="a-namesetchildsitea--iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite  
 Proporciona el objeto con el sitio **IUnknown** puntero.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnkSite*  
 [in] Puntero a la **IUnknown** el puntero de interfaz del sitio de administración de este objeto. Si es NULL, el objeto debe llamar a `IUnknown::Release` en cualquier momento en que el objeto ya no conoce su sitio de sitio existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
##  <a name="a-namesetsitea--iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite  
 Proporciona el objeto con el sitio **IUnknown** puntero.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

