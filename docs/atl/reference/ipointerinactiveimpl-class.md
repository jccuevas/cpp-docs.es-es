---
title: Clase IPointerInactiveImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 05cf4b2247cabe713cfc6b0dd54c95c01e5bbddc
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ipointerinactiveimpl-class"></a>Clase IPointerInactiveImpl
Esta clase implementa **IUnknown** y [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) métodos de interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPointerInactiveImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Recupera la directiva de activación actual del objeto. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifica el objeto que se ha movido el puntero del mouse sobre él, que indica el objeto puede desencadenar los eventos del mouse. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Establece el puntero del mouse para el objeto inactivo. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 Un objeto inactivo es aquel que es simplemente cargado o en ejecución. A diferencia de un objeto activo, un objeto inactivo no puede recibir mensajes de mouse y teclado de Windows. Por lo tanto, los objetos inactivos utilizan menos recursos y son normalmente más eficaces.  
  
 El [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) interfaz permite que un objeto admitir un nivel mínimo de interacción con el mouse mientras permanece inactiva. Esta funcionalidad es especialmente útil para los controles.  
  
 Clase `IPointerInactiveImpl` implementa la `IPointerInactive` métodos devolviendo simplemente **E_NOTIMPL**. Sin embargo, implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 Recupera la directiva de activación actual del objeto.  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 Notifica el objeto que se ha movido el puntero del mouse sobre él, que indica el objeto puede desencadenar los eventos del mouse.  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 Establece el puntero del mouse para el objeto inactivo.  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

