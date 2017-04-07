---
title: structured_task_group (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
dev_langs:
- C++
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a1817080506150a8a25918988e18b76dd7a04def
ms.lasthandoff: 03/17/2017

---
# <a name="structuredtaskgroup-class"></a>structured_task_group (Clase)
La clase `structured_task_group` representa una colección muy estructurada de trabajos paralelos. Puede poner en cola tareas individuales paralelas a `structured_task_group` mediante objetos `task_handle`, y esperar a que se completen, o cancelar el grupo de tareas antes de que haya finalizado su ejecución, que anulará cualquier tarea cuya ejecución no haya comenzado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class structured_task_group;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[structured_task_group](#ctor)|Sobrecargado. Construye un nuevo objeto `structured_task_group`.|  
|[~ structured_task_group (destructor)](#dtor)|Destruye un objeto `structured_task_group`. Se espera que llame a la `wait` o `run_and_wait` en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredo de pila debido a una excepción.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Cancelar](#cancel)|Realiza un mayor esfuerzo para intentar cancelar el subárbol de trabajo con raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas obtener cancelará de manera transitiva si es posible.|  
|[is_canceling](#is_canceling)|Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó el método en el `structured_task_group` objeto (aunque sin duda califica este método para devolver `true`). Puede darse el caso de que el `structured_task_group` objeto se está ejecutando alineado y un grupo de tareas más seguridad en el árbol de trabajo se ha cancelado. En casos como estos dónde puede determinar el tiempo de ejecución antelación cancelación fluirá a través de este `structured_task_group` objeto, `true` también se devolverán.|  
|[run](#run)|Sobrecargado. Programa una tarea en el `structured_task_group` objeto. El llamador administra la duración de la `task_handle` objeto pasado en el `_Task_handle` parámetro. La versión que toma el parámetro `_Placement` hace que la tarea de estar orientadas a ejecutar en la ubicación especificada por ese parámetro.|  
|[run_and_wait](#run_and_wait)|Sobrecargado. Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `structured_task_group` objeto para la compatibilidad de cancelación completa. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La función, a continuación, espera hasta que todo el trabajo en la `structured_task_group` objeto se haya completado o cancelado.|  
|[esperar](#wait)|Espera hasta que todo el trabajo en el `structured_task_group` ha completado o cancelado.|  
  
## <a name="remarks"></a>Comentarios  
 Hay varias restricciones graves sobre el uso de un `structured_task_group` objeto con el fin de obtener un rendimiento:  
  
-   Una sola `structured_task_group` objeto no puede ser utilizado por varios subprocesos. Todas las operaciones en un `structured_task_group` objeto debe realizarse por el subproceso que creó el objeto. Las dos excepciones a esta regla son las funciones miembro `cancel` y `is_canceling`. El objeto no puede estar en la lista de captura de una expresión lambda y utilizarse dentro de una tarea, a menos que la tarea esté utilizando una de las operaciones de cancelación.  
  
-   Todas las tareas programadas para un `structured_task_group` programadas mediante el uso del objeto `task_handle` que debe administrar explícitamente la duración de objetos.  
  
-   Varios grupos solo pueden usarse en orden completamente anidado. Si dos `structured_task_group` objetos se declaran, lo segundo que se declara (el interno uno) se debe destruir antes de cualquier método excepto `cancel` o `is_canceling` se llama en el primero (el exterior uno). Esta condición es verdadera tanto en el caso de declaración de varios `structured_task_group` objetos dentro de los ámbitos mismos o funcionalmente anidados, así como en el caso de una tarea que se puso en cola para la `structured_task_group` a través de la `run` o `run_and_wait` métodos.  
  
-   A diferencia de general `task_group` (clase), todos los Estados de la `structured_task_group` clase son finales. Después de tener en cola tareas para el grupo y esperado a que finalicen, no puede usar el mismo grupo de nuevo.  
  
 Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `structured_task_group`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="cancel"></a>Cancelar 

 Realiza un mayor esfuerzo para intentar cancelar el subárbol de trabajo con raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas obtener cancelará de manera transitiva si es posible.  
  
```
void cancel();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="is_canceling"></a>is_canceling 

 Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó el método en el `structured_task_group` objeto (aunque sin duda califica este método para devolver `true`). Puede darse el caso de que el `structured_task_group` objeto se está ejecutando alineado y un grupo de tareas más seguridad en el árbol de trabajo se ha cancelado. En casos como estos dónde puede determinar el tiempo de ejecución antelación cancelación fluirá a través de este `structured_task_group` objeto, `true` también se devolverán.  
  
```
bool is_canceling();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una indicación de si la `structured_task_group` objeto está en medio de una cancelación (o se garantiza que en breve).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="run"></a>ejecutar 

 Programa una tarea en el `structured_task_group` objeto. El llamador administra la duración de la `task_handle` objeto pasado en el `_Task_handle` parámetro. La versión que toma el parámetro `_Placement` hace que la tarea de estar orientadas a ejecutar en la ubicación especificada por ese parámetro.  
  
```
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto de función que se invocará para ejecutar el cuerpo del identificador de tarea.  
  
 `_Task_handle`  
 Un identificador para el trabajo está programado. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El runtime continuará esperando que se encuentre activo hasta que el `wait` o `run_and_wait` ha llamado al método en este `structured_task_group` objeto.  
  
 `_Placement`  
 Una referencia a la ubicación donde la tarea representada por la `_Task_handle` parámetro se debe ejecutar.  
  
### <a name="remarks"></a>Comentarios  
 El tiempo de ejecución crea una copia de la función de trabajo que se pasa a este método. Cualquier cambio de estado que se produce en un objeto de función que se pasa a este método no aparecerá en la copia de ese objeto de función.  
  
 Si el `structured_task_group` destructs como resultado de desenredado de una excepción de la pila, no es necesario garantizar que una llamada se ha realizado en la `wait` o `run_and_wait` (método). En este caso, el destructor adecuadamente cancelará y espere a que la tarea representada por la `_Task_handle` parámetro para completar.  
  
 Produce una [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) excepción si la tarea de administrar determinado por la `_Task_handle` parámetro ya se ha programado hacia un objeto de grupo de tareas a través de la `run` (método) y no hay ninguna llamada intermedia a la `wait` o `run_and_wait` método en ese grupo de tareas.  
  
##  <a name="run_and_wait"></a>run_and_wait 

 Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `structured_task_group` objeto para la compatibilidad de cancelación completa. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La función, a continuación, espera hasta que todo el trabajo en la `structured_task_group` objeto se haya completado o cancelado.  
  
```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto de función que se invocará para ejecutar la tarea.  
  
 `_Task_handle`  
 Identificador de la tarea que se ejecutará alineado en el contexto de llamada. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El runtime continuará esperando que se encuentre activo hasta que el `run_and_wait` método finaliza la ejecución.  
  
 `_Func`  
 Una función que se llamará para invocar el cuerpo del trabajo. Este puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.  
  
### <a name="return-value"></a>Valor devuelto  
 Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícita o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que uno o más de las tareas programadas para este `structured_task_group` objeto puede ejecutar alineadas en el contexto de llamada.  
  
 Si una o varias de las tareas programadas para este `structured_task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `run_and_wait` (método).  
  
 Después de que esta función devuelve el `structured_task_group` objeto se considera en un estado final y no debe usarse. Tenga en cuenta que uso después de la `run_and_wait` método devuelve dará como resultado un comportamiento indefinido.  
  
 En la ruta de acceso no excepcional de ejecución, tiene un mandato para llamar a este método o el `wait` método antes que el destructor de la `structured_task_group` se ejecuta.  
  
##  <a name="ctor"></a>structured_task_group 

 Construye un nuevo objeto `structured_task_group`.  
  
```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```  
  
### <a name="parameters"></a>Parámetros  
 `_CancellationToken`  
 Un token de cancelación para asociar a este grupo de tareas estructurado. El grupo de tareas estructurado se cancelará cuando se cancela el token.  
  
### <a name="remarks"></a>Comentarios  
 El constructor que toma un token de cancelación crea una `structured_task_group` que se cancela cuando el origen asociado con el token se cancela. También se proporciona un token de cancelación explícito aísla a este grupo de tareas estructurado de participar en una cancelación implícita de un grupo primario con un token de diferentes o ningún token.  
  
##  <a name="dtor"></a>~ structured_task_group 

 Destruye un objeto `structured_task_group`. Se espera que llame a la `wait` o `run_and_wait` en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredo de pila debido a una excepción.  
  
```
~structured_task_group();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el destructor se ejecuta como resultado de la ejecución normal (por ejemplo, no desenredo de pila debido a una excepción) y no la `wait` ni `run_and_wait` ha llamado a los métodos, el destructor puede producir una [missing_wait](missing-wait-class.md) excepción.  
  
##  <a name="wait"></a>esperar 

 Espera hasta que todo el trabajo en el `structured_task_group` ha completado o cancelado.  
  
```
task_group_status wait();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícita o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md)  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que uno o más de las tareas programadas para este `structured_task_group` objeto puede ejecutar alineadas en el contexto de llamada.  
  
 Si una o varias de las tareas programadas para este `structured_task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `wait` (método).  
  
 Después de que esta función devuelve el `structured_task_group` objeto se considera en un estado final y no debe usarse. Tenga en cuenta que uso después de la `wait` método devuelve dará como resultado un comportamiento indefinido.  
  
 En la ruta de acceso no excepcional de ejecución, tiene un mandato para llamar a este método o el `run_and_wait` método antes que el destructor de la `structured_task_group` se ejecuta.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [task_group (clase)](task-group-class.md)   
 [task_handle (clase)](task-handle-class.md)

