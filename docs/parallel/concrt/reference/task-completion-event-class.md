---
title: task_completion_event (Clase)
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
ms.openlocfilehash: 9d0ab271b20eb02c1dc4cb8e54cf2632eead4325
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293893"
---
# <a name="taskcompletionevent-class"></a>task_completion_event (Clase)

La clase `task_completion_event` permite retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo.

## <a name="syntax"></a>Sintaxis

```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

#### <a name="parameters"></a>Parámetros

*_ResultType*<br/>
El tipo de resultado de esta clase `task_completion_event`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[task_completion_event](#ctor)|Construye un objeto `task_completion_event`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[set](#set)|Sobrecargado. Establece el evento de finalización de la tarea.|
|[set_exception](#set_exception)|Sobrecargado. Propaga una excepción a todas las tareas asociadas con este evento.|

## <a name="remarks"></a>Comentarios

Use una tarea creada a partir de un evento de finalización de la tarea cuando su escenario requiere la creación de una tarea que completar, y así tendrá las continuaciones programadas para su ejecución en el futuro. `task_completion_event` debe tener el mismo tipo que la tarea que se crea, así como poder llamar al método set en el evento de finalización de la tarea con un valor de ese tipo, lo que provocará que se complete la tarea asociada y proporcionará ese valor como resultado de sus continuaciones.

Si el evento de finalización de la tarea nunca se señala, cualquier tarea creada a partir de ese evento se cancelará cuando se destruye.

El objeto `task_completion_event` se comporta como un puntero inteligente y debe pasar por valor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_completion_event`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

##  <a name="set"></a> Conjunto

Establece el evento de finalización de la tarea.

```
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parámetros

*_Result*<br/>
Para establecer este evento con el resultado.

### <a name="return-value"></a>Valor devuelto

El método devuelve **true** si tuvo éxito y establecer el evento. Devuelve **false** si ya está establecido el evento.

### <a name="remarks"></a>Comentarios

En presencia de varias llamadas simultáneas a o `set`, solo la primera llamada se realizará correctamente y su resultado (si existe) se almacenará en el evento de finalización de tarea. Los conjuntos restantes se omiten y el método devolverá false. Al establecer un evento de finalización de tarea, todas las tareas creadas desde que se completarán inmediatamente los eventos y sus continuaciones, si existe, se programará. Tareas de los objetos de finalización que tienen un `_ResultType` distinto **void** pasará el valor a sus continuaciones.

##  <a name="set_exception"></a> set_exception

Propaga una excepción a todas las tareas asociadas con este evento.

```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parámetros

*_E*<br/>
Tipo de la excepción.

*_Except*<br/>
La excepción que se va a establecer.

*_ExceptionPtr*<br/>
Puntero a la excepción para establecer.

### <a name="return-value"></a>Valor devuelto

##  <a name="ctor"></a> task_completion_event

Construye un objeto `task_completion_event`.

```
task_completion_event();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
