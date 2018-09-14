---
title: EventSource (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 08347b4ccfa44d8645acc2bd5e96775bab4e7740
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601501"
---
# <a name="eventsource-class"></a>EventSource (clase)

Representa un evento no ágiles. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos. Para los eventos de agile, use [AgileEventSource](agileeventsource-class.md).

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

| Name                                     | Descripción                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource](#eventsource) | Inicializa una nueva instancia de la clase `EventSource`. |

### <a name="public-methods"></a>Métodos públicos

| Name                                 | Descripción                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource](#add)             | Anexa el controlador del evento representado por la interfaz de delegado especificado al conjunto de controladores de eventos actual `EventSource` objeto.                     |
| [GetSize](#getsize)     | Recupera el número de controladores de eventos asociados con el actual `EventSource` objeto.                                                                         |
| [InvokeAll](#invokeall) | Llama a cada controlador de eventos asociado con el actual `EventSource` objeto utilizando los argumentos y tipos de argumento especificados.                                      |
| [EventSource](#remove)       | Elimina el controlador del evento representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el actual `EventSource` objeto. |

### <a name="protected-data-members"></a>Miembros de datos protegidos

| nombre                                                    | Descripción                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [Addremovelock_](#addremovelock)           | Sincroniza el acceso a la [targets_](#targets) matriz al agregar, quitar o invocar controladores de eventos.                          |
| [Targets_](#targets)                       | Una matriz de uno o varios controladores de eventos.                                                                                           |
| [Targetspointerlock_](#targetspointerlock) | Sincroniza el acceso a los miembros de datos internos incluso mientras se agregan controladores de eventos para este origen de eventos, quitar o invocar. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL

## <a name="add"></a>EventSource

Anexa el controlador del evento representado por la interfaz de delegado especificado al conjunto de controladores de eventos actual `EventSource` objeto.

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
Cuando se completa esta operación, un identificador que representa el evento. Use este token como parámetro para el [Remove()](#remove) método para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="addremovelock"></a>Addremovelock_

Sincroniza el acceso a la [targets_](#targets) matriz al agregar, quitar o invocar controladores de eventos.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource

Inicializa una nueva instancia de la clase `EventSource`.

```cpp
EventSource();
```

## <a name="getsize"></a>GetSize

Recupera el número de controladores de eventos asociados con el actual `EventSource` objeto.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de controladores de eventos en [targets_](#targets).

## <a name="invokeall"></a>InvokeAll

Llama a cada controlador de eventos asociado con el actual `EventSource` objeto utilizando los argumentos y tipos de argumento especificados.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Parámetros

*T0*  
El tipo del argumento del controlador de evento inicial.

*T1*  
El tipo del primer argumento de controlador de eventos.

*T2*  
El tipo del segundo argumento de controlador de eventos.

*T3*  
El tipo del tercer argumento de controlador de eventos.

*T4*  
El tipo del cuarto argumento de controlador de eventos.

*T5*  
El tipo del quinto argumento de controlador de eventos.

*T6*  
El tipo del sexto argumento de controlador de eventos.

*T7*  
El tipo del séptimo argumento de controlador de eventos.

*T8*  
El tipo del argumento del controlador de evento de identificador de octava.

*T9*  
El tipo del noveno argumento de controlador de eventos.

*arg0*  
El argumento de controlador de evento inicial.

*Arg1*  
El primer argumento de controlador de eventos.

*Arg2*  
El segundo argumento de controlador de eventos.

*Arg3*  
El tercer argumento de controlador de eventos.

*Arg4*  
El cuarto argumento de controlador de eventos.

*Arg5*  
El quinto argumento de controlador de eventos.

*Arg6*  
El sexto argumento de controlador de eventos.

*Arg7*  
El séptimo argumento de controlador de eventos.

*Arg8*  
El argumento de controlador de evento de identificador de octava.

*Arg9*  
El noveno argumento de controlador de eventos.

## <a name="remove"></a>EventSource

Elimina el controlador del evento representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el actual `EventSource` objeto.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parámetros

*símbolo (token)*  
Un identificador que representa un controlador de eventos. Este token se devolvió cuando se registró el controlador de eventos por la [Add()](#add) método.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre la `EventRegistrationToken` estructura, vea el **Windows::Foundation::EventRegistrationToken estructura** tema en el **en tiempo de ejecución de Windows** documentación de referencia.

## <a name="targets"></a>Targets_

Una matriz de uno o varios controladores de eventos.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Comentarios

Cuando el evento representado por el actual `EventSource` se produce el objeto, se llama a los controladores de eventos.

## <a name="targetspointerlock"></a>Targetspointerlock_

Sincroniza el acceso a los miembros de datos internos incluso mientras los controladores de eventos para este `EventSource` se agrega, quita o invocado.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
