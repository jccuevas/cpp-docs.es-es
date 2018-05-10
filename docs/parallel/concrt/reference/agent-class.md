---
title: Agent (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbc8542af8073b2cb95517ea39d89258afac633c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="agent-class"></a>agent (Clase)
Una clase diseñada para usarse como una clase base para todos los agentes independientes. Se usa para ocultar el estado de otros agentes e interactuar con el paso de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class agent;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Agente](#ctor)|Sobrecargado. Construye a un agente.|  
|[~ agent (destructor)](#dtor)|Destruye al agente.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cancelar](#cancel)|Mueve un agente desde el `agent_created` o `agent_runnable` indica a la `agent_canceled` estado.|  
|[start](#start)|Mueve un agente de la `agent_created` estado para el `agent_runnable` de estado y el programa para su ejecución.|  
|[status](#status)|Un origen sincrónico de la información de estado del agente.|  
|[status_port](#status_port)|Un origen asincrónico de la información de estado del agente.|  
|[espera](#wait)|Espera a que un agente completar su tarea.|  
|[wait_for_all](#wait_for_all)|Espera a que todos los agentes especificados para completar sus tareas.|  
|[wait_for_one](#wait_for_one)|Espera a que cualquiera de los agentes especificados para completar su tarea.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Realiza](#done)|Mueve un agente en el `agent_done` estado, que indica que el agente se ha completado.|  
|[run](#run)|Representa la tarea principal de un agente. `run` se debe invalidar en una clase derivada y especifica lo que debe hacer el agente después de que se ha iniciado.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `agent`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> Agente 

 Construye a un agente.  
  
```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PScheduler`  
 La `Scheduler` objeto en que se programa la tarea de ejecución del agente.  
  
 `_PGroup`  
 La `ScheduleGroup` objeto en que se programa la tarea de ejecución del agente. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifica la `_PScheduler` o `_PGroup` parámetros.  
  
##  <a name="dtor"></a> ~ agente 

 Destruye al agente.  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>Comentarios  
 Es un error para destruir un agente que no está en un estado terminal (ya sea `agent_done` o `agent_canceled`). Esto se puede evitar esperando el agente alcanzar un estado terminal en el destructor de una clase que hereda de la `agent` clase.  
  
##  <a name="cancel"></a> Cancelar 

 Mueve un agente desde el `agent_created` o `agent_runnable` indica a la `agent_canceled` estado.  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si se ha cancelado el agente, `false` en caso contrario. Un agente no se puede cancelar si ya ha empezado a ejecutarse o ya se ha completado.  
  
##  <a name="done"></a> Realiza 

 Mueve un agente en el `agent_done` estado, que indica que el agente se ha completado.  
  
```
bool done();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el agente se mueve a la `agent_done` estado, `false` en caso contrario. No se puede mover un agente que se ha cancelado para el `agent_done` estado.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a este método al final de la `run` método, cuando se sabe que la ejecución del agente ha completado.  
  
##  <a name="run"></a> Ejecutar 

 Representa la tarea principal de un agente. `run` se debe invalidar en una clase derivada y especifica lo que debe hacer el agente después de que se ha iniciado.  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 El estado del agente se cambia a `agent_started` correctamente antes de que se invoca este método. Debe invocar el método `done` en el agente con un estado adecuado antes de regresar y no se puede iniciar ninguna excepción.  
  
##  <a name="start"></a> Inicio 

 Mueve un agente de la `agent_created` estado para el `agent_runnable` de estado y el programa para su ejecución.  
  
```
bool start();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el agente se inicia correctamente, `false` en caso contrario. No se puede iniciar un agente que se ha cancelado.  
  
##  <a name="status"></a> Estado 

 Un origen sincrónico de la información de estado del agente.  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el estado actual del agente. Tenga en cuenta que este estado devuelto podría cambiar inmediatamente después de que se devuelven.  
  
##  <a name="status_port"></a> status_port 

 Un origen asincrónico de la información de estado del agente.  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un origen de mensaje que puede enviar mensajes sobre el estado actual del agente.  
  
##  <a name="wait"></a> espera 

 Espera a que un agente completar su tarea.  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PAgent`  
 Un puntero al agente para esperar.  
  
 `_Timeout`  
 El tiempo máximo para el que se espera, en milisegundos.  
  
### <a name="return-value"></a>Valor devuelto  
 El `agent_status` del agente cuando finaliza la espera. Esto puede ser `agent_canceled` o `agent_done`.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
##  <a name="wait_for_all"></a> wait_for_all 

 Espera a que todos los agentes especificados para completar sus tareas.  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `count`  
 El número de punteros de agente presentes en la matriz `_PAgents`.  
  
 `_PAgents`  
 Una matriz de punteros a los agentes para esperar.  
  
 `_PStatus`  
 Un puntero a una matriz de Estados de agente. Cada valor de estado representará el estado del agente correspondiente cuando el método vuelve.  
  
 `_Timeout`  
 El tiempo máximo para el que se espera, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
##  <a name="wait_for_one"></a> wait_for_one 

 Espera a que cualquiera de los agentes especificados para completar su tarea.  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `count`  
 El número de punteros de agente presentes en la matriz `_PAgents`.  
  
 `_PAgents`  
 Una matriz de punteros a los agentes para esperar.  
  
 `_Status`  
 Una referencia a una variable donde se colocará el estado del agente.  
  
 `_Index`  
 Una referencia a una variable donde se colocará el índice de agente.  
  
 `_Timeout`  
 El tiempo máximo para el que se espera, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
