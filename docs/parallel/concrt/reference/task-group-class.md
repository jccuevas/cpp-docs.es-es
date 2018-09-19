---
title: task_group (clase) | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
dev_langs:
- C++
helpviewer_keywords:
- task_group class
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7ee8fa674174d95c3e538889f6d5538be049b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020725"
---
# <a name="taskgroup-class"></a>task_group (Clase)
La clase `task_group` representa una colección de trabajo paralelo que es posible esperar o cancelar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class task_group;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task_group](#ctor)|Sobrecargado. Construye un nuevo objeto `task_group`.|  
|[~ task_group (destructor)](#dtor)|Destruye un objeto `task_group`. Se espera que se llame a cualquiera la `wait` o `run_and_wait` método en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredado debido a una excepción de la pila.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cancelar](#cancel)|Realiza un esfuerzo intenta cancelar el subárbol cuya raíz comienza en este grupo de tareas de trabajo. Todas las tareas programadas en el grupo de tareas obtener cancelará de manera transitiva si es posible.|  
|[is_canceling](#is_canceling)|Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó al método en el `task_group` objeto (aunque sin duda califica este método para devolver `true`). Puede darse el caso de que el `task_group` objeto está ejecutando alineado y un grupo de tareas aún más seguridad en el árbol de trabajo se canceló. En casos como estos dónde puede determinar el tiempo de ejecución antes de tiempo que la cancelación fluirá a través de este `task_group` objeto, `true` devolverá también.|  
|[run](#run)|Sobrecargado. Programa una tarea en el `task_group` objeto. Si un `task_handle` objeto se pasa como parámetro a `run`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La versión del método que toma una referencia a un objeto de función como un parámetro implica la asignación del montón dentro del runtime que puede ejecutarse bien que el uso de la versión que toma una referencia a un `task_handle` objeto. La versión que toma el parámetro `_Placement` hace que la tarea se orientadas a ejecutar en la ubicación especificada por ese parámetro.|  
|[run_and_wait](#run_and_wait)|Sobrecargado. Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `task_group` objeto para la compatibilidad de cancelación completa. La función, a continuación, espera hasta que todo funcione en el `task_group` objeto se haya completado o cancelado. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto.|  
|[Espere](#wait)|Espera hasta que todo funcione en el `task_group` objeto se haya completado o cancelado.|  
  
## <a name="remarks"></a>Comentarios  
 A diferencia de muy restringido `structured_task_group` (clase), el `task_group` clase es una construcción mucho más general. No tiene ninguna de las restricciones descritas por [structured_task_group](structured-task-group-class.md). `task_group` objetos de forma segura pueden utilizarse a través de subprocesos y utilizan de maneras de forma libre. La desventaja de la `task_group` construcción es que no puede realizar, así como la `structured_task_group` construir para las tareas que realizan cantidades pequeñas de trabajo.  
  
 Para obtener más información, consulte [paralelismo de tareas](../task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `task_group`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="cancel"></a> Cancelar 

 Realiza un esfuerzo intenta cancelar el subárbol cuya raíz comienza en este grupo de tareas de trabajo. Todas las tareas programadas en el grupo de tareas obtener cancelará de manera transitiva si es posible.  
  
```  
void cancel();  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [cancelación](../cancellation-in-the-ppl.md).  
  
##  <a name="is_canceling"></a> is_canceling 

 Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó al método en el `task_group` objeto (aunque sin duda califica este método para devolver `true`). Puede darse el caso de que el `task_group` objeto está ejecutando alineado y un grupo de tareas aún más seguridad en el árbol de trabajo se canceló. En casos como estos dónde puede determinar el tiempo de ejecución antes de tiempo que la cancelación fluirá a través de este `task_group` objeto, `true` devolverá también.  
  
```  
bool is_canceling();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una indicación de si el `task_group` objeto está en medio de una cancelación (o se garantiza que en breve).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [cancelación](../cancellation-in-the-ppl.md).  
  
##  <a name="run"></a> ejecutar 

 Programa una tarea en el `task_group` objeto. Si un `task_handle` objeto se pasa como parámetro a `run`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La versión del método que toma una referencia a un objeto de función como un parámetro implica la asignación del montón dentro del runtime que puede ejecutarse bien que el uso de la versión que toma una referencia a un `task_handle` objeto. La versión que toma el parámetro `_Placement` hace que la tarea se orientadas a ejecutar en la ubicación especificada por ese parámetro.  
  
```  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func  
);  
  
template<  
   typename _Function  
>  
void run(  
   const _Function& _Func,  
   location& _Placement  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   typename _Function  
>  
void run(  
   task_handle<_Function>& _Task_handle,  
   location& _Placement  
);  
```  
  
### <a name="parameters"></a>Parámetros  
*_Function*<br/>
El tipo de objeto de función que se invocará para ejecutar el cuerpo del identificador de tarea.  
  
*_Func*<br/>
Una función que se llamará para invocar el cuerpo de la tarea. Esto puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.  
  
*_Este*<br/>
Una referencia a la ubicación donde la tarea representada por la `_Func` parámetro se debe ejecutar.  
  
*_Task_handle*<br/>
Un identificador para el trabajo está programado. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El tiempo de ejecución continuará esperando que se encuentre activo hasta que el `wait` o `run_and_wait` se ha llamado al método en este `task_group` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El runtime programa la función de trabajo proporcionada para ejecutarse en un momento posterior, que puede ser después de que devuelva la función de llamada. Este método usa un [task_handle](task-handle-class.md) objeto para mantener una copia de la función de trabajo proporcionada. Por lo tanto, cualquier cambio de estado que se produce en un objeto de función que se pasa a este método no aparecerá en la copia de ese objeto de función. Además, asegúrese de que la duración de todos los objetos que se pasan mediante el puntero o referencia a la función de trabajo siguen siendo válida hasta que devuelve la función de trabajo.  
  
 Si el `task_group` destructs como resultado de desenredado de una excepción de la pila, no es necesario garantizar que se ha realizado una llamada a la `wait` o `run_and_wait` método. En este caso, el destructor se adecuadamente Cancelar y espere a que la tarea representada por la `_Task_handle` parámetro para completar.  
  
 El método produce una [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) excepción si la tarea controla determinado por la `_Task_handle` parámetro ya se ha programado en un objeto de grupo de tareas a través de la `run` método y se ha producido ningún llamada intermedia en el `wait` o `run_and_wait` método en ese grupo de tareas.  
  
##  <a name="run_and_wait"></a> run_and_wait 

 Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `task_group` objeto para la compatibilidad de cancelación completa. La función, a continuación, espera hasta que todo funcione en el `task_group` objeto se haya completado o cancelado. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto.  
  
```  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   task_handle<_Function>& _Task_handle  
);  
  
template<  
   class _Function  
>  
task_group_status run_and_wait(  
   const _Function& _Func  
);  
```  
  
### <a name="parameters"></a>Parámetros  
*_Function*<br/>
El tipo de objeto de función que se invocará para ejecutar el cuerpo de la tarea.  
  
*_Task_handle*<br/>
Identificador de la tarea que se va a ejecutar en línea en el contexto de llamada. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El tiempo de ejecución continuará esperando que se encuentre activo hasta que el `run_and_wait` método finaliza la ejecución.  
  
*_Func*<br/>
Una función que se llamará para invocar el cuerpo del trabajo. Esto puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.  
  
### <a name="return-value"></a>Valor devuelto  
 Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícito o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que una o varias de las tareas programadas para esto `task_group` objeto puede ejecutarse en línea en el contexto de llamada.  
  
 Si una o varias de las tareas programadas para esto `task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `run_and_wait` método.  
  
 Cuando se devuelve desde el `run_and_wait` método en un `task_group` de objeto, el tiempo de ejecución, restablece el objeto a un estado limpio donde se puede reutilizar. Esto incluye el caso donde la `task_group` objeto se ha cancelado.  
  
 En la ruta de acceso sin excepciones de ejecución, tiene un mandato para llamar a este método o el `wait` método antes que el destructor de la `task_group` ejecuta.  
  
##  <a name="ctor"></a> task_group 

 Construye un nuevo objeto `task_group`.  
  
```  
task_group();  
  
task_group(  
   cancellation_token _CancellationToken  
);  
```  
  
### <a name="parameters"></a>Parámetros  
*_CancellationToken*<br/>
Un token de cancelación para asociar a este grupo de tareas. El grupo de tareas se cancelará cuando se cancela el token.  
  
### <a name="remarks"></a>Comentarios  
 El constructor que toma un token de cancelación crea una `task_group` que se cancela cuando el origen asociado con el token se cancela. Proporcionar un token de cancelación explícita también aísla a este grupo de tareas que no participe en una cancelación implícita de un grupo primario con un token distinto o ningún token.  
  
##  <a name="dtor"></a> ~ task_group 

 Destruye un objeto `task_group`. Se espera que se llame a cualquiera la `wait` o `run_and_wait` método en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredado debido a una excepción de la pila.  
  
```  
~task_group();  
```  
  
### <a name="remarks"></a>Comentarios  
 Si el destructor se ejecuta como el resultado de la ejecución normal (por ejemplo, no desenredo de pila debido a una excepción) y no el `wait` ni `run_and_wait` se ha llamado a los métodos, el destructor puede producir un [missing_wait](missing-wait-class.md) excepción.  
  
##  <a name="wait"></a> Espere 

 Espera hasta que todo funcione en el `task_group` objeto se haya completado o cancelado.  
  
```  
task_group_status wait();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícito o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md#task_group_status).  

  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que una o varias de las tareas programadas para esto `task_group` objeto puede ejecutarse en línea en el contexto de llamada.  
  
 Si una o varias de las tareas programadas para esto `task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `wait` método.  
  
 Una llamada a `wait` en un `task_group` objeto restablece a un estado limpio donde se puede reutilizar. Esto incluye el caso donde la `task_group` objeto se ha cancelado.  
  
 En la ruta de acceso sin excepciones de ejecución, tiene un mandato para llamar a este método o el `run_and_wait` método antes que el destructor de la `task_group` ejecuta.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [structured_task_group (clase)](structured-task-group-class.md)   
 [task_handle (clase)](task-handle-class.md)