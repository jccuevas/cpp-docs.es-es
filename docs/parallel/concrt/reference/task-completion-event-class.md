---
title: task_completion_event (clase)
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: b3e3093cb76df507f8c707e497c9aec75a065057
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142592"
---
# <a name="task_completion_event-class"></a>task_completion_event (clase)

La clase `task_completion_event` permite retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>Parámetros

*_ResultType*<br/>
El tipo de resultado de esta clase `task_completion_event`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_completion_event](#ctor)|Construye un objeto `task_completion_event`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[set](#set)|Sobrecargado. Establece el evento de finalización de la tarea.|
|[set_exception](#set_exception)|Sobrecargado. Propaga una excepción a todas las tareas asociadas con este evento.|

## <a name="remarks"></a>Observaciones

Use una tarea creada a partir de un evento de finalización de la tarea cuando su escenario requiere la creación de una tarea que completar, y así tendrá las continuaciones programadas para su ejecución en el futuro. `task_completion_event` debe tener el mismo tipo que la tarea que se crea, así como poder llamar al método set en el evento de finalización de la tarea con un valor de ese tipo, lo que provocará que se complete la tarea asociada y proporcionará ese valor como resultado de sus continuaciones.

Si el evento de finalización de la tarea nunca se señala, cualquier tarea creada a partir de ese evento se cancelará cuando se destruye.

El objeto `task_completion_event` se comporta como un puntero inteligente y debe pasar por valor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_completion_event`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks. h

**Espacio de nombres:** simultaneidad

## <a name="set"></a>conjunto

Establece el evento de finalización de la tarea.

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parámetros

*_Result*<br/>
Resultado con el que se va a establecer este evento.

### <a name="return-value"></a>Valor devuelto

El método devuelve **true** si se ha establecido correctamente el evento. Devuelve **false** si ya se ha establecido el evento.

### <a name="remarks"></a>Observaciones

En presencia de varias llamadas o llamadas simultáneas a `set`, solo la primera llamada se realizará correctamente y su resultado (si existe) se almacenará en el evento de finalización de la tarea. Se omiten los conjuntos restantes y el método devolverá FALSE. Cuando se establece un evento de finalización de tarea, todas las tareas creadas a partir de ese evento se completarán inmediatamente y se programarán sus continuaciones, si las hay. Los objetos de finalización de tareas que tienen un `_ResultType` distinto de **void** pasarán el valor a sus continuaciones.

## <a name="set_exception"></a>set_exception

Propaga una excepción a todas las tareas asociadas con este evento.

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parámetros

*_E*<br/>
Tipo de excepción.

*_Except*<br/>
Excepción que se va a establecer.

*_ExceptionPtr*<br/>
Puntero de excepción que se va a establecer.

### <a name="return-value"></a>Valor devuelto

## <a name="ctor"></a>task_completion_event

Construye un objeto `task_completion_event`.

```cpp
task_completion_event();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
