---
title: task_continuation_context (clase)
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142577"
---
# <a name="task_continuation_context-class"></a>task_continuation_context (clase)

La clase `task_continuation_context` permite especificar dónde se desea que se ejecute una continuación. Solo es útil usar esta clase desde una aplicación Windows Runtime. En el caso de las aplicaciones que no son Windows Runtime, el tiempo de ejecución determina el contexto de ejecución de la continuación de la tarea y no se puede configurar.

## <a name="syntax"></a>Sintaxis

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto del subproceso de winrt actual.|
|[use_arbitrary](#use_arbitrary)|Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el tiempo de ejecución.|
|[use_current](#use_current)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.|
|[use_default](#use_default)|Crea el contexto de continuación de tarea predeterminado.|
|[use_synchronous_execution](#use_synchronous_execution)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónico.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks. h

**Espacio de nombres:** simultaneidad

## <a name="get_current_winrt_context"></a>get_current_winrt_context

Devuelve un objeto de contexto de continuación de tarea que representa el contexto del subproceso de WinRT actual.

### <a name="syntax"></a>Sintaxis

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Valor devuelto

Contexto actual del subproceso de Windows Runtime. Devuelve un task_continuation_context vacío si se llama desde un contexto que no es de Windows Runtime.

### <a name="remarks"></a>Observaciones

El método `get_current_winrt_context` captura el contexto del subproceso de Windows Runtime del llamador. Devuelve un contexto vacío a los llamadores que no son de Windows Runtime.

El valor devuelto por `get_current_winrt_context` se puede usar para indicar al tiempo de ejecución que la continuación debe ejecutarse en el modelo de apartamento del contexto capturado (STA vs MTA), independientemente de si la tarea antecedente es compatible con apartamentos. Una tarea compatible con apartamentos es una tarea que desencapsula un Windows Runtime `IAsyncInfo` interfaz o una tarea que desciende de esta tarea.

Este método es similar al método `use_current`, pero también está disponible para el código nativo C++ sin C++compatibilidad con la extensión/CX. Está pensada para que la usen usuarios avanzados C++que escriben código de biblioteca/CX-agnostic para llamadores nativos y Windows Runtime. A menos que necesite esta funcionalidad, se recomienda el método `use_current`, que solo está disponible C++para los clientes de/CX.

## <a name="use_arbitrary"></a>use_arbitrary

Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el tiempo de ejecución.

### <a name="syntax"></a>Sintaxis

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Valor devuelto

Contexto de continuación de tarea que representa una ubicación arbitraria.

### <a name="remarks"></a>Observaciones

Cuando se usa este contexto de continuación, la continuación se ejecutará en un contexto que el Runtime elija aunque la tarea antecedente sea compatible con apartamentos.

`use_arbitrary` se puede usar para desactivar el comportamiento predeterminado de una continuación en una tarea compatible con apartamentos creada en un STA.

Este método solo está disponible para Windows Runtime aplicaciones.

## <a name="use_current"></a>use_current

Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>Valor devuelto

Contexto de ejecución actual.

### <a name="remarks"></a>Observaciones

Este método captura el contexto de Windows Runtime del llamador para que las continuaciones se puedan ejecutar en el apartamento derecho.

El valor devuelto por `use_current` se puede usar para indicar al tiempo de ejecución que la continuación debe ejecutarse en el contexto capturado (STA frente a MTA) independientemente de si la tarea antecedente es o no compatible con apartamentos. Una tarea compatible con apartamentos es una tarea que desencapsula un Windows Runtime `IAsyncInfo` interfaz o una tarea que desciende de esta tarea.

Este método solo está disponible para Windows Runtime aplicaciones.

## <a name="use_default"></a>use_default

Crea el contexto de continuación de tarea predeterminado.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>Valor devuelto

Contexto de continuación predeterminado.

### <a name="remarks"></a>Observaciones

El contexto predeterminado se usa si no se especifica un contexto de continuación cuando se llama al método `then`. En aplicaciones de Windows para Windows 7 y versiones anteriores, así como aplicaciones de escritorio en Windows 8 y versiones posteriores, el tiempo de ejecución determina dónde se ejecutarán las continuaciones de tareas. Sin embargo, en una aplicación Windows Runtime, el contexto de continuación predeterminado para una continuación en una tarea compatible con apartamentos es el apartamento donde se invoca `then`.

Una tarea compatible con apartamentos es una tarea que desencapsula un Windows Runtime `IAsyncInfo` interfaz o una tarea que desciende de esta tarea. Por lo tanto, si programa una continuación en una tarea compatible con el apartamento en un Windows Runtime STA, la continuación se ejecutará en ese STA.

Una continuación en una tarea que no sea compatible con apartamentos se ejecutará en un contexto que elija el tiempo de ejecución.

## <a name="use_synchronous_execution"></a>task_continuation_context:: use_synchronous_execution

Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónico.

### <a name="syntax"></a>Sintaxis

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Valor devuelto

Contexto de ejecución sincrónica.

### <a name="remarks"></a>Observaciones

El método `use_synchronous_execution` fuerza a la tarea de continuación a ejecutarse sincrónicamente en el contexto, lo que provoca la finalización de la tarea antecedente.

Si la tarea antecedente ya se ha completado cuando se adjunta la continuación, la continuación se ejecuta de forma sincrónica en el contexto que asocia la continuación.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
