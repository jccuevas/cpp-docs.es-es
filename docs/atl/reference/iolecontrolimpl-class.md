---
title: Clase IOleControlImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a54067f53e83d78f063ae5f3694460452e24b26
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="iolecontrolimpl-class"></a>Clase IOleControlImpl
Esta clase proporciona una implementación predeterminada de la **IOleControl** interfaz e implementa **IUnknown**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor pasa por alto o acepta eventos procedentes del control.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Escribe información acerca del comportamiento de teclado del control. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor. Devuelve la implementación de ATL `S_OK`.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informa al control que un usuario ha presionado una pulsación de tecla especificado. Devuelve la implementación de ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Comentarios  
 Clase `IOleControlImpl` proporciona una implementación predeterminada de la [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 En la implementación de ATL, `FreezeEvents` incrementa la clase de control `m_nFreezeEvents` miembro de datos si `bFreeze` es **TRUE**y disminuye `m_nFreezeEvents` si `bFreeze` es **FALSE**.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Comentarios  
 `FreezeEvents` a continuación, devuelve `S_OK`.  
  
 Vea [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) en el SDK de Windows.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Escribe información acerca del comportamiento de teclado del control.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) en el SDK de Windows.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informa al control que un usuario ha presionado una pulsación de tecla especificado.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Información general de clases](../../atl/atl-class-overview.md)
