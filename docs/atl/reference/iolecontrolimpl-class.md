---
title: Clase IOleControlImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5e63849a504b931de30141dd91af557f16c67fd8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="iolecontrolimpl-class"></a>Clase IOleControlImpl
Esta clase proporciona una implementación predeterminada de la **IOleControl** interfaz e implementa **IUnknown**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IOleControlImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor ignora o acepta eventos del control.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Escribe información acerca del comportamiento del teclado del control. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor. Devuelve la implementación de ATL `S_OK`.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informa al control que un usuario ha presionado una tecla especificada. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `IOleControlImpl` proporciona una implementación predeterminada de la [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="freezeevents"></a>IOleControlImpl::FreezeEvents  
 En la implementación de ATL, `FreezeEvents` incrementa la clase de control `m_nFreezeEvents` miembro de datos si `bFreeze` es **TRUE**y disminuye `m_nFreezeEvents` si `bFreeze` es **FALSE**.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Comentarios  
 `FreezeEvents`a continuación, devuelve `S_OK`.  
  
 Consulte [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo  
 Escribe información acerca del comportamiento del teclado del control.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
##  <a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange  
 Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onmnemonic"></a>IOleControlImpl::OnMnemonic  
 Informa al control que un usuario ha presionado una tecla especificada.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Información general de la clase](../../atl/atl-class-overview.md)

