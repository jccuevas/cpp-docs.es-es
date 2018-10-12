---
title: structured_task_group (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e87ebd4523b5211c94955b5bec7905ed848946
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161689"
---
# <a name="structuredtaskgroup-class"></a>structured_task_group (Clase)

La clase `structured_task_group` representa una colección muy estructurada de trabajos paralelos. Puede poner en cola tareas individuales paralelas a `structured_task_group` mediante objetos `task_handle`, y esperar a que se completen, o cancelar el grupo de tareas antes de que haya finalizado su ejecución, que anulará cualquier tarea cuya ejecución no haya comenzado.

## <a name="syntax"></a>Sintaxis

```
class structured_task_group;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[structured_task_group](#ctor)|Sobrecargado. Construye un nuevo objeto `structured_task_group`.|
|[~ structured_task_group (destructor)](#dtor)|Destruye un objeto `structured_task_group`. Se espera que llamar a la `wait` o `run_and_wait` método en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredo de pila debido a una excepción.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Cancelar](#cancel)|Realiza un esfuerzo intenta cancelar el subárbol cuya raíz comienza en este grupo de tareas de trabajo. Todas las tareas programadas en el grupo de tareas obtener cancelará de manera transitiva si es posible.|
|[is_canceling](#is_canceling)|Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó al método en el `structured_task_group` objeto (aunque sin duda califica este método para devolver **true**). Puede darse el caso de que el `structured_task_group` objeto está ejecutando alineado y un grupo de tareas aún más seguridad en el árbol de trabajo se canceló. En casos como estos dónde puede determinar el tiempo de ejecución antes de tiempo que la cancelación fluirá a través de este `structured_task_group` objeto, **true** devolverá también.|
|[run](#run)|Sobrecargado. Programa una tarea en el `structured_task_group` objeto. El llamador administra la duración de la `task_handle` objeto pasado en el `_Task_handle` parámetro. La versión que toma el parámetro `_Placement` hace que la tarea se orientadas a ejecutar en la ubicación especificada por ese parámetro.|
|[run_and_wait](#run_and_wait)|Sobrecargado. Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `structured_task_group` objeto para la compatibilidad de cancelación completa. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La función, a continuación, espera hasta que todo funcione en el `structured_task_group` objeto se haya completado o cancelado.|
|[Espere](#wait)|Espera hasta que todo funcione en el `structured_task_group` se cancela o se ha completado.|

## <a name="remarks"></a>Comentarios

Hay una serie de restricciones graves en el uso de un `structured_task_group` objeto con el fin de obtener un rendimiento:

- Una sola `structured_task_group` objeto no se puede usar varios subprocesos. Todas las operaciones en un `structured_task_group` objeto debe realizarse por el subproceso que creó el objeto. Las dos excepciones a esta regla son las funciones miembro `cancel` y `is_canceling`. El objeto no puede estar en la lista de captura de una expresión lambda y utilizarse dentro de una tarea, a menos que la tarea está usando una de las operaciones de cancelación.

- Todas las tareas programadas para un `structured_task_group` objeto se programan mediante el uso de `task_handle` que debe administrar explícitamente la duración de objetos.

- Solo pueden usarse varios grupos en orden completamente anidado. Si dos `structured_task_group` se declaran objetos, la segunda se va a declarar (lo interna) se debe destruir antes de cualquier método excepto `cancel` o `is_canceling` se llama en la primera de ellas (el exterior uno). Esta condición se cumple tanto en el caso de simplemente declarando varias `structured_task_group` objetos dentro de los ámbitos mismos o funcionalmente anidados, así como en el caso de una tarea que se puso en cola para el `structured_task_group` a través de la `run` o `run_and_wait` métodos.

- A diferencia de general `task_group` clase, todos los Estados de la `structured_task_group` clase son definitivas. Después de haber puesto en cola las tareas para el grupo y espera a que finalicen, no puede usar el mismo grupo de nuevo.

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`structured_task_group`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppl.h

**Espacio de nombres:** simultaneidad

##  <a name="cancel"></a> Cancelar

Realiza un esfuerzo intenta cancelar el subárbol cuya raíz comienza en este grupo de tareas de trabajo. Todas las tareas programadas en el grupo de tareas obtener cancelará de manera transitiva si es posible.

```
void cancel();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="is_canceling"></a> is_canceling

Informa al llamador si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que el `cancel` se llamó al método en el `structured_task_group` objeto (aunque sin duda califica este método para devolver **true**). Puede darse el caso de que el `structured_task_group` objeto está ejecutando alineado y un grupo de tareas aún más seguridad en el árbol de trabajo se canceló. En casos como estos dónde puede determinar el tiempo de ejecución antes de tiempo que la cancelación fluirá a través de este `structured_task_group` objeto, **true** devolverá también.

```
bool is_canceling();
```

### <a name="return-value"></a>Valor devuelto

Una indicación de si el `structured_task_group` objeto está en medio de una cancelación (o se garantiza que en breve).

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="run"></a> ejecutar

Programa una tarea en el `structured_task_group` objeto. El llamador administra la duración de la `task_handle` objeto pasado en el `_Task_handle` parámetro. La versión que toma el parámetro `_Placement` hace que la tarea se orientadas a ejecutar en la ubicación especificada por ese parámetro.

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

*_Function*<br/>
El tipo de objeto de función que se invocará para ejecutar el cuerpo del identificador de tarea.

*_Task_handle*<br/>
Un identificador para el trabajo está programado. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El tiempo de ejecución continuará esperando que se encuentre activo hasta que el `wait` o `run_and_wait` se ha llamado al método en este `structured_task_group` objeto.

*_Este*<br/>
Una referencia a la ubicación donde la tarea representada por la `_Task_handle` parámetro se debe ejecutar.

### <a name="remarks"></a>Comentarios

El tiempo de ejecución crea una copia de la función de trabajo que se pasa a este método. Cualquier cambio de estado que se produce en un objeto de función que se pasa a este método no aparecerá en la copia de ese objeto de función.

Si el `structured_task_group` destructs como resultado de desenredado de una excepción de la pila, no es necesario garantizar que se ha realizado una llamada a la `wait` o `run_and_wait` método. En este caso, el destructor se adecuadamente Cancelar y espere a que la tarea representada por la `_Task_handle` parámetro para completar.

Produce una [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) excepción si la tarea controla determinado por la `_Task_handle` parámetro ya se ha programado en un objeto de grupo de tareas a través de la `run` método y no ha habido ninguna llamada intermedia a ya sea el `wait` o `run_and_wait` método en ese grupo de tareas.

##  <a name="run_and_wait"></a> run_and_wait

Programa una tarea que se ejecuta alineada en el contexto de llamada con la Ayuda de la `structured_task_group` objeto para la compatibilidad de cancelación completa. Si un `task_handle` objeto se pasa como parámetro a `run_and_wait`, el llamador es responsable de administrar la duración de la `task_handle` objeto. La función, a continuación, espera hasta que todo funcione en el `structured_task_group` objeto se haya completado o cancelado.

```
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
El tipo de objeto de función que se invocará para ejecutar la tarea.

*_Task_handle*<br/>
Identificador de la tarea que se va a ejecutar en línea en el contexto de llamada. Tenga en cuenta que el llamador tiene la responsabilidad de la duración de este objeto. El tiempo de ejecución continuará esperando que se encuentre activo hasta que el `run_and_wait` método finaliza la ejecución.

*_Func*<br/>
Una función que se llamará para invocar el cuerpo del trabajo. Esto puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="return-value"></a>Valor devuelto

Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícito o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Comentarios

Tenga en cuenta que una o varias de las tareas programadas para esto `structured_task_group` objeto puede ejecutarse en línea en el contexto de llamada.

Si una o varias de las tareas programadas para esto `structured_task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `run_and_wait` método.

Después de esta función que devuelve el `structured_task_group` objeto se considera en un estado final y no debe usarse. Tenga en cuenta que uso después de la `run_and_wait` método devuelve dará como resultado un comportamiento indefinido.

En la ruta de acceso sin excepciones de ejecución, tiene un mandato para llamar a este método o el `wait` método antes que el destructor de la `structured_task_group` ejecuta.

##  <a name="ctor"></a> structured_task_group

Construye un nuevo objeto `structured_task_group`.

```
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parámetros

*_CancellationToken*<br/>
Un token de cancelación para asociar a este grupo de tareas estructurado. El grupo de tareas estructurado se cancelará cuando se cancela el token.

### <a name="remarks"></a>Comentarios

El constructor que toma un token de cancelación crea una `structured_task_group` que se cancela cuando el origen asociado con el token se cancela. También se proporciona un token de cancelación explícito aísla a este grupo de tareas estructurado que no participe en una cancelación implícita de un grupo primario con un token distinto o ningún token.

##  <a name="dtor"></a> ~structured_task_group

Destruye un objeto `structured_task_group`. Se espera que llamar a la `wait` o `run_and_wait` método en el objeto antes de la ejecución del destructor, a menos que el destructor se ejecuta como resultado de desenredo de pila debido a una excepción.

```
~structured_task_group();
```

### <a name="remarks"></a>Comentarios

Si el destructor se ejecuta como el resultado de la ejecución normal (por ejemplo, no desenredo de pila debido a una excepción) y no el `wait` ni `run_and_wait` se ha llamado a los métodos, el destructor puede producir un [missing_wait](missing-wait-class.md) excepción.

##  <a name="wait"></a> Espere

Espera hasta que todo funcione en el `structured_task_group` se cancela o se ha completado.

```
task_group_status wait();
```

### <a name="return-value"></a>Valor devuelto

Se canceló una indicación de si se satisfizo la espera o el grupo de tareas, debido a una operación de cancelación explícito o una excepción desde una de sus tareas. Para obtener más información, consulte [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Comentarios

Tenga en cuenta que una o varias de las tareas programadas para esto `structured_task_group` objeto puede ejecutarse en línea en el contexto de llamada.

Si una o varias de las tareas programadas para esto `structured_task_group` objeto produce una excepción, el runtime seleccionará una de las excepciones de su elección y propagará fuera de la llamada a la `wait` método.

Después de esta función que devuelve el `structured_task_group` objeto se considera en un estado final y no debe usarse. Tenga en cuenta que uso después de la `wait` método devuelve dará como resultado un comportamiento indefinido.

En la ruta de acceso sin excepciones de ejecución, tiene un mandato para llamar a este método o el `run_and_wait` método antes que el destructor de la `structured_task_group` ejecuta.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[task_handle (clase)](task-handle-class.md)
