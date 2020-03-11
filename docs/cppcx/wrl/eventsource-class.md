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
ms.openlocfilehash: 1350e51ff609a888b6a8ad6841be6856b68c7994
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865735"
---
# <a name="eventsource-class"></a>EventSource (clase)

Representa un evento no ágil. Las funciones miembro `EventSource` agregan, quitan e invocan controladores de eventos. En el caso de los eventos Agile, use [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
La interfaz a un delegado que representa un controlador de eventos.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

| Nombre                                     | Descripción                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource:: EventSource](#eventsource) | Inicializa una nueva instancia de la clase `EventSource`. |

### <a name="public-methods"></a>Métodos públicos

| Nombre                                 | Descripción                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: Add](#add)             | Anexa el controlador de eventos representado por la interfaz de delegado especificada al conjunto de controladores de eventos para el objeto `EventSource` actual.                     |
| [EventSource:: se obtiene](#getsize)     | Recupera el número de controladores de eventos asociados al objeto `EventSource` actual.                                                                         |
| [EventSource:: InvokeAll (](#invokeall) | Llama a cada controlador de eventos asociado al objeto `EventSource` actual utilizando los tipos de argumento y los argumentos especificados.                                      |
| [EventSource:: Remove](#remove)       | Elimina el controlador de eventos representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados al objeto `EventSource` actual. |

### <a name="protected-data-members"></a>Miembros de datos protegidos

| Nombre                                                    | Descripción                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource:: addRemoveLock_](#addremovelock)           | Sincroniza el acceso a la matriz de [targets_](#targets) al agregar, quitar o invocar controladores de eventos.                          |
| [EventSource:: targets_](#targets)                       | Matriz de uno o varios controladores de eventos.                                                                                           |
| [EventSource:: targetsPointerLock_](#targetspointerlock) | Sincroniza el acceso a los miembros de datos internos incluso mientras se agregan, quitan o invocan controladores de eventos para este EventSource. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** Event. h

**Espacio de nombres:** Microsoft::WRL

## <a name="add"></a>EventSource:: Add

Anexa el controlador de eventos representado por la interfaz de delegado especificada al conjunto de controladores de eventos para el objeto `EventSource` actual.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parámetros

*delegateInterface*<br/>
La interfaz de un objeto delegado, que representa un controlador de eventos.

*token*<br/>
Cuando se completa esta operación, un identificador que representa el evento. Use este token como parámetro para el método [Remove ()](#remove) para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="addremovelock"></a>EventSource:: addRemoveLock_

Sincroniza el acceso a la matriz de [targets_](#targets) al agregar, quitar o invocar controladores de eventos.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource:: EventSource

Inicializa una nueva instancia de la clase `EventSource`.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource:: se obtiene

Recupera el número de controladores de eventos asociados al objeto `EventSource` actual.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de controladores de eventos en [targets_](#targets).

## <a name="invokeall"></a>EventSource:: InvokeAll (

Llama a cada controlador de eventos asociado al objeto `EventSource` actual utilizando los tipos de argumento y los argumentos especificados.

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

*To*<br/>
Tipo del argumento del controlador de eventos inicial.

*T1*<br/>
Tipo del primer argumento del controlador de eventos.

*T2*<br/>
Tipo del segundo argumento del controlador de eventos.

*T3*<br/>
Tipo del tercer argumento del controlador de eventos.

*T4*<br/>
Tipo del cuarto argumento del controlador de eventos.

*T5*<br/>
Tipo del quinto argumento del controlador de eventos.

*T6*<br/>
Tipo del sexto argumento del controlador de eventos.

*T7*<br/>
Tipo del séptimo argumento del controlador de eventos.

*T8*<br/>
Tipo del octavo argumento del controlador de eventos.

*T9*<br/>
Tipo del noveno argumento de controlador de eventos.

*arg0*<br/>
El argumento del controlador de eventos inicial.

*arg1*<br/>
El primer argumento del controlador de eventos.

*arg2*<br/>
Segundo argumento del controlador de eventos.

*arg3*<br/>
Tercer argumento de controlador de eventos.

*arg4*<br/>
Cuarto argumento de controlador de eventos.

*arg5*<br/>
Quinto argumento del controlador de eventos.

*arg6*<br/>
Sexto argumento del controlador de eventos.

*arg7*<br/>
Séptimo argumento del controlador de eventos.

*arg8*<br/>
Octavo argumento del controlador de eventos.

*arg9*<br/>
Noveno argumento de controlador de eventos.

## <a name="remove"></a>EventSource:: Remove

Elimina el controlador de eventos representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados al objeto `EventSource` actual.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parámetros

*token*<br/>
Identificador que representa un controlador de eventos. Este token se devolvió cuando el método [Add ()](#add) registró el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre la estructura de `EventRegistrationToken`, vea el tema sobre la **estructura Windows:: Foundation:: EventRegistrationToken** en la documentación de referencia de **Windows Runtime** .

## <a name="targets"></a>EventSource:: targets_

Matriz de uno o varios controladores de eventos.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Observaciones

Cuando se produce el evento representado por el objeto `EventSource` actual, se llama a los controladores de eventos.

## <a name="targetspointerlock"></a>EventSource:: targetsPointerLock_

Sincroniza el acceso a los miembros de datos internos incluso mientras se agregan, quitan o invocan controladores de eventos para este `EventSource`.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
