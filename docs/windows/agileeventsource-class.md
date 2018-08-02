---
title: Clase AgileEventSource | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7412968069963679db769cc2ce68169e7a8799b9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462074"
---
# <a name="agileeventsource-class"></a>Clase AgileEventSource

Representa un evento provocado por un componente de agile, que es un componente que se puede acceder desde cualquier subproceso. Hereda de [EventSource](eventsource-class.md) e invalida el `Add` función miembro con un parámetro de tipo adicionales para especificar opciones sobre cómo invocar el evento de agile.

## <a name="syntax"></a>Sintaxis

```
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parámetros  
 *TDelegateInterface*  

 La interfaz a un delegado que representa un controlador de eventos.

 *TEventSourceOptions*  
 Un [InvokeModeOptions](invokemodeoptions-structure.md) cuyo campo invokeMode está establecido en una estructura `InvokeMode::StopOnFirstError` o `InvokeMode::FireAll`.

## <a name="remarks"></a>Comentarios

La mayoría de los componentes en tiempo de ejecución de Windows son ágiles componentes. Para obtener más información, consulte [subprocesamiento y serialización (C++ / c++ / CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

 `EventSource` `AgileEventSource`

## <a name="requirements"></a>Requisitos

 **Encabezado:** event.h

 **Espacio de nombres:** Microsoft::WRL

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Método AgileEventSource::Add](#add)|Anexa el controlador de eventos agile representado por la interfaz de delegado especificado al conjunto de controladores de eventos para el objeto AgileEventSource actual.|

## <a name="add"></a> Método AgileEventSource::Add

Anexa el controlador del evento representado por la interfaz de delegado especificado al conjunto de controladores de eventos actual [EventSource](eventsource-class.md) objeto.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parámetros

*delegateInterface*  
La interfaz para un objeto delegado, que representa un controlador de eventos.

*símbolo (token)*  
Cuando se completa esta operación, un identificador que representa el evento. Use este token como parámetro al método Remove() para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.


## <a name="see-also"></a>Vea también
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)