---
title: CFirePropNotifyEvent (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ec6fb0d54cd748b707c81b88e09fb7d846aaa2f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194429"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent (clase)
Esta clase proporciona métodos para notificar el receptor del contenedor con respecto a los cambios de propiedad de control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Estático) Notifica a los receptores del contenedor que ha cambiado una propiedad de control.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Estático) Notifica a los receptores del contenedor que una propiedad de control que se va a cambiar.|  
  
## <a name="remarks"></a>Comentarios  
 `CFirePropNotifyEvent` tiene dos métodos que notifiquen a los receptores del contenedor que ha cambiado una propiedad de control o que va a cambiar.  
  
 Si se deriva la clase que implementa el control `IPropertyNotifySink`, `CFirePropNotifyEvent` métodos se invocan cuando se llama a `FireOnRequestEdit` o `FireOnChanged`. Si no se deriva de la clase del control `IPropertyNotifySink`, las llamadas a estas funciones devuelven S_OK.  
  
 Para obtener más información sobre la creación de controles, vea el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged  
 Notifica a todos conectados [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfaces (en cada punto de conexión del objeto) que ha cambiado la propiedad del objeto especificado.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Puntero a la `IUnknown` del objeto que envía la notificación.  
  
 *dispID*  
 [in] Identificador de la propiedad que ha cambiado.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es segura llamar a incluso si el control no admite puntos de conexión.  
  
##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit  
 Notifica a todos conectados [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfaces (en cada punto de conexión del objeto) que la propiedad del objeto especificado que se va a cambiar.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Puntero a la `IUnknown` del objeto que envía la notificación.  
  
 *dispID*  
 [in] Identificador de la propiedad que se va a cambiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es segura llamar a incluso si el control no admite puntos de conexión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
