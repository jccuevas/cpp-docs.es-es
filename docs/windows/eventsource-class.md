---
title: EventSource (clase) | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f740cbfb8aea1a0e2378d1d2ab42d3c88c77137
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644773"
---
# <a name="eventsource-class"></a>EventSource (clase)
Representa un evento no ágiles. **EventSource** funciones miembro agregar, quitar e invocar controladores de eventos. Para los eventos de agile, use [AgileEventSource](agileeventsource-class.md). 
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<typename TDelegateInterface>  
class EventSource;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TDelegateInterface*  
 La interfaz a un delegado que representa un controlador de eventos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::EventSource (constructor)](../windows/eventsource-eventsource-constructor.md)|Inicializa una nueva instancia de la **EventSource** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::Add (método)](../windows/eventsource-add-method.md)|Anexa el controlador del evento representado por la interfaz de delegado especificado al conjunto de controladores de eventos actual **EventSource** objeto.|  
|[EventSource::GetSize (método)](../windows/eventsource-getsize-method.md)|Recupera el número de controladores de eventos asociados con el actual **EventSource** objeto|  
|[EventSource::InvokeAll (método)](../windows/eventsource-invokeall-method.md)|Llama a cada controlador de eventos asociado con el actual **EventSource** objeto utilizando los argumentos y tipos de argumento especificados.|  
|[EventSource::Remove (método)](../windows/eventsource-remove-method.md)|Elimina el controlador del evento representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el actual **EventSource** objeto.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[EventSource::addRemoveLock_ (miembro de datos)](../windows/eventsource-addremovelock-data-member.md)|Sincroniza el acceso a la [targets_](../windows/eventsource-targets-data-member.md) matriz al agregar, quitar o invocar controladores de eventos.|  
|[EventSource::targets_ (miembro de datos)](../windows/eventsource-targets-data-member.md)|Una matriz de uno o varios controladores de eventos.|  
|[EventSource::targetsPointerLock_ (miembro de datos)](../windows/eventsource-targetspointerlock-data-member.md)|Sincroniza el acceso a los miembros de datos internos incluso mientras se agregan controladores de eventos para este origen de eventos, quitar o invocar.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EventSource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)  
 [Clase AgileEventSource](agileeventsource-class.md)