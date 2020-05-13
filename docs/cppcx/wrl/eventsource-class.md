---
title: EventSource (clase)
ms.date: 09/12/2018
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
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371540"
---
# <a name="eventsource-class"></a>EventSource (clase)

Representa un evento no ágil. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos. Para eventos ágiles, utilice [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
La interfaz a un delegado que representa un controlador de eventos.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

| Nombre                                     | Descripción                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | Inicializa una nueva instancia de la clase `EventSource`. |

### <a name="public-methods"></a>Métodos públicos

| Nombre                                 | Descripción                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | Anexa el controlador de eventos representado por la interfaz de delegado `EventSource` especificada al conjunto de controladores de eventos para el objeto actual.                     |
| [EventSource::GetSize](#getsize)     | Recupera el número de controladores de `EventSource` eventos asociados con el objeto actual.                                                                         |
| [EventSource::InvokeAll](#invokeall) | Llama a cada controlador `EventSource` de eventos asociado con el objeto actual mediante los tipos de argumento y argumentos especificados.                                      |
| [EventSource::Quitar](#remove)       | Elimina el controlador de eventos representado por el token de registro de eventos `EventSource` especificado del conjunto de controladores de eventos asociados con el objeto actual. |

### <a name="protected-data-members"></a>Miembros de datos protegidos

| Nombre                                                    | Descripción                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Sincroniza el acceso a la matriz [targets_](#targets) al agregar, quitar o invocar controladores de eventos.                          |
| [EventSource::targets_](#targets)                       | Matriz de uno o varios controladores de eventos.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Sincroniza el acceso a los miembros de datos internos incluso mientras se agregan, quitan o invocan controladores de eventos para este EventSource. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>EventSource::Add

Anexa el controlador de eventos representado por la interfaz de delegado `EventSource` especificada al conjunto de controladores de eventos para el objeto actual.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parámetros

*delegateInterface*<br/>
La interfaz de un objeto delegado, que representa un controlador de eventos.

*Token*<br/>
Cuando se completa esta operación, un identificador que representa el evento. Utilice este token como parámetro del método [Remove()](#remove) para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>EventSource::addRemoveLock_

Sincroniza el acceso a la matriz [targets_](#targets) al agregar, quitar o invocar controladores de eventos.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>EventSource::EventSource

Inicializa una nueva instancia de la clase `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>EventSource::GetSize

Recupera el número de controladores de `EventSource` eventos asociados con el objeto actual.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de controladores de eventos en [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>EventSource::InvokeAll

Llama a cada controlador `EventSource` de eventos asociado con el objeto actual mediante los tipos de argumento y argumentos especificados.

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

*T0*<br/>
El tipo del argumento de controlador de eventos zeroth.

*T1*<br/>
El tipo del primer argumento de controlador de eventos.

*T2*<br/>
El tipo del segundo argumento de controlador de eventos.

*T3*<br/>
El tipo del tercer argumento de controlador de eventos.

*T4*<br/>
El tipo del cuarto argumento de controlador de eventos.

*T5*<br/>
El tipo del quinto argumento de controlador de eventos.

*T6*<br/>
El tipo del sexto argumento de controlador de eventos.

*T7*<br/>
El tipo del séptimo argumento de controlador de eventos.

*T8*<br/>
El tipo del octavo argumento de controlador de eventos.

*T9*<br/>
El tipo del noveno argumento de controlador de eventos.

*arg0*<br/>
El argumento de controlador de eventos cero.

*arg1*<br/>
El primer argumento de controlador de eventos.

*arg2*<br/>
El segundo argumento de controlador de eventos.

*arg3*<br/>
El tercer argumento de controlador de eventos.

*arg4*<br/>
El cuarto argumento del controlador de eventos.

*arg5*<br/>
El quinto argumento del controlador de eventos.

*arg6*<br/>
El sexto argumento del controlador de eventos.

*arg7*<br/>
El séptimo argumento del controlador de eventos.

*arg8*<br/>
El octavo argumento del controlador de eventos.

*arg9*<br/>
El noveno argumento del controlador de eventos.

## <a name="eventsourceremove"></a><a name="remove"></a>EventSource::Quitar

Elimina el controlador de eventos representado por el token de registro de eventos `EventSource` especificado del conjunto de controladores de eventos asociados con el objeto actual.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parámetros

*Token*<br/>
Identificador que representa un controlador de eventos. Este token se devolvió cuando el método [Add()](#add) registró el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Para obtener más `EventRegistrationToken` información acerca de la estructura, vea el **windows::Foundation::EventRegistrationToken structure** tema en el **Windows Runtime** documentación de referencia.

## <a name="eventsourcetargets_"></a><a name="targets"></a>EventSource::targets_

Matriz de uno o varios controladores de eventos.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Observaciones

Cuando se produce el evento `EventSource` representado por el objeto actual, se llama a los controladores de eventos.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Sincroniza el acceso a los miembros de `EventSource` datos internos incluso mientras se agregan, quitan o invocan controladores de eventos para esto.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
