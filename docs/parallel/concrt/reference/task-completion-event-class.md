---
title: task_completion_event (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs: C++
helpviewer_keywords: task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48bf640d75a02b9033102b1c8fc7b824dc4a5be0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 `_ResultType`  
 El tipo de resultado de esta clase `task_completion_event`.  
  
 `T`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task_completion_event)](#ctor)|Construye un objeto `task_completion_event`.|  
  
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
  
##  <a name="set"></a>conjunto 

 Establece el evento de finalización de la tarea.  
  
```
bool set(_ResultType _Result) const ;

bool set() const ;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Result`  
 El resultado para establecer este evento con.  
  
### <a name="return-value"></a>Valor devuelto  
 El método devuelve `true` si tuvo éxito y establecer el evento. Devuelve `false` si el evento se ha establecido.  
  
### <a name="remarks"></a>Comentarios  
 En presencia de varios o de llamadas simultáneas a `set`, solo la primera llamada se realizará correctamente y su resultado (si existe) se almacenará en el evento de finalización de tarea. Los conjuntos restantes se omiten y el método devolverá false. Cuando se establece un evento de finalización de tarea, todas las tareas se crean desde que eventos finalizará inmediatamente y sus continuaciones, si los hay, se programará. Tareas de objetos de finalización que tienen un `_ResultType` distinto de `void` pasará el valor de sus continuaciones.  
  
##  <a name="set_exception"></a>set_exception 

 Propaga una excepción a todas las tareas asociadas con este evento.  
  
```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```  
  
### <a name="parameters"></a>Parámetros  
 `_E`  
 `_Except`  
 `_ExceptionPtr`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="ctor"></a>task_completion_event) 

 Construye un objeto `task_completion_event`.  
  
```
task_completion_event();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
