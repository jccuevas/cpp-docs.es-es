---
title: Clase CFirePropNotifyEvent | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9571ad4ba928c208c6c028f6e30cf7c27c196d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent (clase)
Esta clase proporciona métodos para notificar a los receptores del contenedor con respecto a los cambios de propiedad de control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
 `CFirePropNotifyEvent`tiene dos métodos que notifiquen a los receptores del contenedor que una propiedad de control ha cambiado o va a cambiar.  
  
 Si se deriva la clase que implementa el control `IPropertyNotifySink`, `CFirePropNotifyEvent` métodos se invocan cuando se llama a `FireOnRequestEdit` o `FireOnChanged`. Si la clase del control no se deriva de `IPropertyNotifySink`, las llamadas a estas funciones devuelven `S_OK`.  
  
 Para obtener más información sobre la creación de controles, consulte el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged  
 Notifica a todos conectados [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaces (en cada punto de conexión del objeto) que ha cambiado la propiedad del objeto especificado.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Puntero a la **IUnknown** del objeto que envía la notificación.  
  
 *dispID*  
 [in] Identificador de la propiedad que ha cambiado.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es segura llamar a incluso si el control no admite puntos de conexión.  
  
##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit  
 Notifica a todos conectados [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaces (en cada punto de conexión del objeto) que la propiedad del objeto especificado que se va a cambiar.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Parámetros  
 *pUnk*  
 [in] Puntero a la **IUnknown** del objeto que envía la notificación.  
  
 *dispID*  
 [in] Identificador de la propiedad que se va a cambiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es segura llamar a incluso si el control no admite puntos de conexión.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
