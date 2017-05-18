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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1511a9e9ba287d12aade7c393887c6b5f8880b96
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent (clase)
Esta clase proporciona métodos para notificar a los receptores del contenedor con respecto a los cambios de propiedad de control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Estático) Notifica a los receptores del contenedor que ha cambiado una propiedad de control.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Estático) Notifica a los receptores del contenedor que una propiedad de control que se va a cambiar.|  
  
## <a name="remarks"></a>Comentarios  
 `CFirePropNotifyEvent`tiene dos métodos que notifiquen a los receptores del contenedor que una propiedad de control ha cambiado o va a cambiar.  
  
 Si se deriva de la clase que implementa el control `IPropertyNotifySink`, `CFirePropNotifyEvent` los métodos se invocan cuando se llama a `FireOnRequestEdit` o `FireOnChanged`. Si no se deriva de la clase del control `IPropertyNotifySink`, las llamadas a estas funciones devuelven `S_OK`.  
  
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
 Notifica a todos conectados [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaces (en cada punto de conexión del objeto) que es cambiar la propiedad del objeto especificado.  
  
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
 [Información general de la clase](../../atl/atl-class-overview.md)

