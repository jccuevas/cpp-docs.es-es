---
title: agent (clase)
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882943"
---
# <a name="agent-class"></a>agent (clase)

Una clase diseñada para usarse como una clase base para todos los agentes independientes. Se usa para ocultar el estado de otros agentes e interactuar con el paso de mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
class agent;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[directivas](#ctor)|Sobrecargado. Construye un agente.|
|[~ (destructor del agente)](#dtor)|Destruye el agente.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancel](#cancel)|Mueve un agente de los Estados `agent_created` o `agent_runnable` al estado `agent_canceled`.|
|[start](#start)|Mueve un agente del estado `agent_created` al estado `agent_runnable` y lo programa para su ejecución.|
|[status](#status)|Origen sincrónico de la información de estado del agente.|
|[status_port](#status_port)|Origen asincrónico de información de estado del agente.|
|[currir](#wait)|Espera a que un agente complete su tarea.|
|[wait_for_all](#wait_for_all)|Espera a que todos los agentes especificados completen sus tareas.|
|[wait_for_one](#wait_for_one)|Espera a que uno de los agentes especificados complete su tarea.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[done](#done)|Mueve un agente al estado `agent_done`, lo que indica que se ha completado el agente.|
|[run](#run)|Representa la tarea principal de un agente. `run` debe invalidarse en una clase derivada y especifica lo que debe hacer el agente una vez iniciado.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`agent`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>directivas

Construye un agente.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Objeto de `Scheduler` en el que está programada la tarea de ejecución del agente.

*_PGroup*<br/>
Objeto de `ScheduleGroup` en el que está programada la tarea de ejecución del agente. El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PGroup` .

## <a name="dtor"></a>~ agente

Destruye el agente.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Observaciones

Es un error destruir un agente que no está en un estado de terminal (ya sea `agent_done` o `agent_canceled`). Esto se puede evitar esperando a que el agente llegue a un estado de terminal en el destructor de una clase que hereda de la clase `agent`.

## <a name="cancel"></a>Cancelar

Mueve un agente de los Estados `agent_created` o `agent_runnable` al estado `agent_canceled`.

```cpp
bool cancel();
```

### <a name="return-value"></a>Valor devuelto

**true** si se canceló el agente; de lo contrario, **false** . No se puede cancelar un agente si ya ha empezado a ejecutarse o ya se ha completado.

## <a name="done"></a>vertir

Mueve un agente al estado `agent_done`, lo que indica que se ha completado el agente.

```cpp
bool done();
```

### <a name="return-value"></a>Valor devuelto

**true** si el agente se mueve al estado `agent_done`, **false** en caso contrario. Un agente que se ha cancelado no se puede pasar al estado `agent_done`.

### <a name="remarks"></a>Observaciones

Se debe llamar a este método al final del método `run`, cuando sepa que se ha completado la ejecución del agente.

## <a name="run"></a>realizar

Representa la tarea principal de un agente. `run` debe invalidarse en una clase derivada y especifica lo que debe hacer el agente una vez iniciado.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Observaciones

El estado del agente cambia a `agent_started` justo antes de que se invoque este método. El método debe invocar `done` en el agente con un estado adecuado antes de devolver y no puede producir excepciones.

## <a name="start"></a>iniciales

Mueve un agente del estado `agent_created` al estado `agent_runnable` y lo programa para su ejecución.

```cpp
bool start();
```

### <a name="return-value"></a>Valor devuelto

**true** si el agente se ha iniciado correctamente, **false** en caso contrario. No se puede iniciar un agente que se ha cancelado.

## <a name="status"></a>estatus

Origen sincrónico de la información de estado del agente.

```cpp
agent_status status();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado actual del agente. Tenga en cuenta que este estado devuelto podría cambiar inmediatamente después de devolverse.

## <a name="status_port"></a>status_port

Origen asincrónico de información de estado del agente.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un origen de mensaje que puede enviar mensajes sobre el estado actual del agente.

## <a name="wait"></a>currir

Espera a que un agente complete su tarea.

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*_PAgent*<br/>
Puntero al agente que se va a esperar.

*_Timeout*<br/>
Tiempo máximo que se va a esperar, en milisegundos.

### <a name="return-value"></a>Valor devuelto

`agent_status` del agente cuando se completa la espera. Puede ser `agent_canceled` o `agent_done`.

### <a name="remarks"></a>Observaciones

Una tarea del agente se completa cuando el agente entra en los Estados `agent_canceled` o `agent_done`.

Si el parámetro `_Timeout` tiene un valor distinto del `COOPERATIVE_TIMEOUT_INFINITE`constante, se produce la excepción [operation_timed_out](operation-timed-out-class.md) si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.

## <a name="wait_for_all"></a>wait_for_all

Espera a que todos los agentes especificados completen sus tareas.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*count*<br/>
El número de punteros del agente presentes en la matriz `_PAgents`.

*_PAgents*<br/>
Matriz de punteros a los agentes que se van a esperar.

*_PStatus*<br/>
Puntero a una matriz de Estados del agente. Cada valor de estado representará el estado del agente correspondiente cuando se devuelva el método.

*_Timeout*<br/>
Tiempo máximo que se va a esperar, en milisegundos.

### <a name="remarks"></a>Observaciones

Una tarea del agente se completa cuando el agente entra en los Estados `agent_canceled` o `agent_done`.

Si el parámetro `_Timeout` tiene un valor distinto del `COOPERATIVE_TIMEOUT_INFINITE`constante, se produce la excepción [operation_timed_out](operation-timed-out-class.md) si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.

## <a name="wait_for_one"></a>wait_for_one

Espera a que uno de los agentes especificados complete su tarea.

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*count*<br/>
El número de punteros del agente presentes en la matriz `_PAgents`.

*_PAgents*<br/>
Matriz de punteros a los agentes que se van a esperar.

*_Status*<br/>
Referencia a una variable en la que se colocará el estado del agente.

*_Index*<br/>
Referencia a una variable en la que se colocará el índice del agente.

*_Timeout*<br/>
Tiempo máximo que se va a esperar, en milisegundos.

### <a name="remarks"></a>Observaciones

Una tarea del agente se completa cuando el agente entra en los Estados `agent_canceled` o `agent_done`.

Si el parámetro `_Timeout` tiene un valor distinto del `COOPERATIVE_TIMEOUT_INFINITE`constante, se produce la excepción [operation_timed_out](operation-timed-out-class.md) si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
