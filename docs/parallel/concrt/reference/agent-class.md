---
title: Agent (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 1e6e23e742137bffd9035ecf69ecc32d199ca0c5
ms.lasthandoff: 03/17/2017

---
# <a name="agent-class"></a>agent (Clase)
Una clase diseñada para usarse como una clase base para todos los agentes independientes. Se usa para ocultar el estado de otros agentes e interactuar con el paso de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class agent;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[agente](#ctor)|Sobrecargado. Construye a un agente.|  
|[~ agent (destructor)](#dtor)|Destruye al agente.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Cancelar](#cancel)|Mueve un agente desde el `agent_created` o `agent_runnable` Estados la `agent_canceled` estado.|  
|[start](#start)|Mueve un agente de la `agent_created` estado del `agent_runnable` de estado y el programa para su ejecución.|  
|[status](#status)|Un origen sincrónico de información de estado del agente.|  
|[status_port](#status_port)|Un origen asincrónico de información de estado del agente.|  
|[esperar](#wait)|Espera a que un agente completar su tarea.|  
|[wait_for_all](#wait_for_all)|Espera a que todos los agentes especificados completen sus tareas.|  
|[wait_for_one](#wait_for_one)|Espera a que cualquiera de los agentes especificados complete su tarea.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[hecho](#done)|Mueve un agente en el `agent_done` estado, que indica que el agente se ha completado.|  
|[run](#run)|Representa la tarea principal de un agente. `run`se debe invalidar en una clase derivada y especifica lo que debe hacer el agente después de que se ha iniciado.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `agent`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>agente 

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
  
##  <a name="dtor"></a>~ agent 

 Destruye al agente.  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>Comentarios  
 Es un error para destruir un agente que no está en un estado terminal (ya sea `agent_done` o `agent_canceled`). Esto se puede evitar esperando el agente llegue a un estado terminal en el destructor de una clase que hereda de la `agent` clase.  
  
##  <a name="cancel"></a>Cancelar 

 Mueve un agente desde el `agent_created` o `agent_runnable` Estados la `agent_canceled` estado.  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el agente se ha cancelado, `false` en caso contrario. Un agente no se puede cancelar si ya ha empezado a ejecutarse o ya se ha completado.  
  
##  <a name="done"></a>hecho 

 Mueve un agente en el `agent_done` estado, que indica que el agente se ha completado.  
  
```
bool done();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el agente se mueve a la `agent_done` estado, `false` en caso contrario. No se pueden mover un agente que se ha cancelado la `agent_done` estado.  
  
### <a name="remarks"></a>Comentarios  
 Este método debe llamarse al final de la `run` ha completado el método, cuando se sabe que la ejecución del agente.  
  
##  <a name="run"></a>ejecutar 

 Representa la tarea principal de un agente. `run`se debe invalidar en una clase derivada y especifica lo que debe hacer el agente después de que se ha iniciado.  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 El estado del agente cambia a `agent_started` correctamente antes de que se invoca este método. Debe invocar el método `done` en el agente con un estado adecuado antes de regresar y no se puede producir ninguna excepción.  
  
##  <a name="start"></a>Inicio 

 Mueve un agente de la `agent_created` estado del `agent_runnable` de estado y el programa para su ejecución.  
  
```
bool start();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el agente se inicia correctamente, `false` en caso contrario. No se puede iniciar un agente que se ha cancelado.  
  
##  <a name="status"></a>estado 

 Un origen sincrónico de información de estado del agente.  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el estado actual del agente. Tenga en cuenta que este estado devuelto podría cambiar inmediatamente después de ser devuelto.  
  
##  <a name="status_port"></a>status_port 

 Un origen asincrónico de información de estado del agente.  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el origen de los mensajes que puede enviar mensajes sobre el estado actual del agente.  
  
##  <a name="wait"></a>esperar 

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
 El tiempo máximo de espera, en milisegundos.  
  
### <a name="return-value"></a>Valor devuelto  
 El `agent_status` del agente cuando finaliza la espera. Esto puede ser `agent_canceled` o `agent_done`.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
##  <a name="wait_for_all"></a>wait_for_all 

 Espera a que todos los agentes especificados completen sus tareas.  
  
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
 Puntero a una matriz de Estados de agente. Cada valor de estado representará el estado del agente correspondiente cuando el método devuelve.  
  
 `_Timeout`  
 El tiempo máximo de espera, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
##  <a name="wait_for_one"></a>wait_for_one 

 Espera a que cualquiera de los agentes especificados complete su tarea.  
  
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
 El tiempo máximo de espera, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Se completa una tarea de agente cuando el agente entra en el `agent_canceled` o `agent_done` Estados.  
  
 Si el parámetro `_Timeout` tiene un valor distinto de la constante `COOPERATIVE_TIMEOUT_INFINITE`, la excepción [operation_timed_out](operation-timed-out-class.md) se produce si la cantidad de tiempo especificada expira antes de que el agente haya completado su tarea.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

