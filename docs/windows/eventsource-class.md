---
title: EventSource (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 531c4ec218f7e3b694a41cd465090a5b1787c41a
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="eventsource-class"></a>EventSource (clase)
Representa un evento no ágiles. Funciones de miembro EventSource agregarán, quitarán e invocan controladores de eventos. Para los eventos de agile, use [AgileEventSource](agileeventsource-class.md). 
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename TDelegateInterface>  
class EventSource;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TDelegateInterface`  
 La interfaz a un delegado que representa un controlador de eventos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::EventSource (constructor)](../windows/eventsource-eventsource-constructor.md)|Inicializa una nueva instancia de la clase EventSource.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::Add (método)](../windows/eventsource-add-method.md)|Anexa el controlador del evento representado por la interfaz de delegado especificado para el conjunto de controladores de eventos para el objeto de origen de eventos actual.|  
|[EventSource::GetSize (método)](../windows/eventsource-getsize-method.md)|Recupera el número de controladores de eventos asociados con el objeto EventSource actual|  
|[EventSource::InvokeAll (método)](../windows/eventsource-invokeall-method.md)|Llama a cada controlador de eventos asociado con el objeto de EventSource actual utilizando los argumentos y tipos de argumentos especificados.|  
|[EventSource::Remove (método)](../windows/eventsource-remove-method.md)|Elimina el controlador de eventos representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el objeto de origen de eventos actual.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[EventSource::addRemoveLock_ (miembro de datos)](../windows/eventsource-addremovelock-data-member.md)|Sincroniza el acceso a la [targets_](../windows/eventsource-targets-data-member.md) matriz al agregar, quitar o invocar controladores de eventos.|  
|[EventSource::targets_ (miembro de datos)](../windows/eventsource-targets-data-member.md)|Una matriz de uno o más controladores de eventos.|  
|[EventSource::targetsPointerLock_ (miembro de datos)](../windows/eventsource-targetspointerlock-data-member.md)|Sincroniza el acceso a miembros de datos internos incluso mientras se agregan controladores de eventos para este origen de eventos, quitar o invocar.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EventSource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)
[AgileEventSource Class](agileeventsource-class.md)