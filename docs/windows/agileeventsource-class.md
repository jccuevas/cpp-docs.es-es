---
title: Clase AgileEventSource | Documentos de Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d025fc2be86fb5b59107d1deee39962c3c6db04
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="agileeventsource-class"></a>Clase AgileEventSource
Representa un evento de agile. Hereda de [EventSource](eventsource-class.md) e invalida el `Add` función miembro con un parámetro de tipo adicionales para especificar opciones de cómo invocar el evento agile.
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `TDelegateInterface`  
 La interfaz a un delegado que representa un controlador de eventos.

 `TEventSourceOptions` Un [InvokeModeOptions](invokemodeoptions-structure.md) estructura cuyo campo invokeMode está establecido en `InvokeMode::StopOnFirstError` o `InvokeMode::FireAll`.

## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AgileEventSource::Add (método)](#add)|Anexa el controlador de eventos agile representado por la interfaz de delegado especificado para el conjunto de controladores de eventos para el objeto de AgileEventSource actual.|  

## <a name="add"></a> AgileEventSource::Add (método)

Anexa el controlador del evento representado por la interfaz de delegado especificado para el conjunto de controladores de eventos para el objeto de origen de eventos actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);
```

### <a name="parameters"></a>Parámetros

*delegateInterface*

La interfaz a un objeto de delegado, que representa un controlador de eventos.

*símbolo (token)* cuando se completa esta operación, un identificador que representa el evento. Usar este token como parámetro al método Remove() para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto
S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EventSource`  
 `AgileEventSource`
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)