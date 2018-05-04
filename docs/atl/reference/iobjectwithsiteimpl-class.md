---
title: Clase IObjectWithSiteImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c626db62a02fba70f926776ea214e664d2f7f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|Consulta el sitio para un puntero de interfaz.|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Proporciona el objeto con el sitio **IUnknown** puntero.|  
|[IObjectWithSiteImpl::SetSite](#setsite)|Proporciona el objeto con el sitio **IUnknown** puntero.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Administra el sitio **IUnknown** puntero.|  
  
## <a name="remarks"></a>Comentarios  
 El [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) interfaz permite que un objeto para comunicarse con su sitio. Clase `IObjectWithSiteImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 `IObjectWithSiteImpl` Especifica dos métodos. El primer cliente llama `SetSite`, pasando el sitio **IUnknown** puntero. This (puntero) se almacena en el objeto y, más adelante se pueden recuperar mediante una llamada a `GetSite`.  
  
 Por lo general, derive su clase de `IObjectWithSiteImpl` al crear un objeto que no es un control. Para los controles, derive su clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio. No se derivan la clase de ambos `IObjectWithSiteImpl` y `IOleObjectImpl`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite  
 Consulta el sitio para un puntero a la interfaz identificada por `riid`.  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Si el sitio admite esta interfaz, se devuelve el puntero a través de `ppvSite`. En caso contrario, `ppvSite` está establecido en **NULL**.  
  
 Vea [IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) en el SDK de Windows.  
  
##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite  
 Administra el sitio **IUnknown** puntero.  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>Comentarios  
 `m_spUnkSite` Recibe inicialmente this (puntero) a través de una llamada a [SetSite](#setsite).  
  
##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite  
 Proporciona el objeto con el sitio **IUnknown** puntero.  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnkSite*  
 [in] Puntero a la **IUnknown** puntero de interfaz del sitio de administración de este objeto. Si es NULL, el objeto debe llamar a `IUnknown::Release` en cualquier momento en que el objeto ya no conoce su sitio de sitio existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite  
 Proporciona el objeto con el sitio **IUnknown** puntero.  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
