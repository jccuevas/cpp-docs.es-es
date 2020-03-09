---
title: structured_task_group (clase)
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884123"
---
# <a name="structured_task_group-class"></a>structured_task_group (clase)

La clase `structured_task_group` representa una colección muy estructurada de trabajos paralelos. Puede poner en cola tareas individuales paralelas a `structured_task_group` mediante objetos `task_handle`, y esperar a que se completen, o cancelar el grupo de tareas antes de que haya finalizado su ejecución, que anulará cualquier tarea cuya ejecución no haya comenzado.

## <a name="syntax"></a>Sintaxis

```cpp
class structured_task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[structured_task_group](#ctor)|Sobrecargado. Construye un nuevo objeto `structured_task_group`.|
|[~ structured_task_group destructor](#dtor)|Destruye un objeto `structured_task_group`. Se espera llamar al método `wait` o `run_and_wait` en el objeto antes de que se ejecute el destructor, a menos que el destructor se esté ejecutando como resultado del desenredado de la pila debido a una excepción.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancel](#cancel)|Realiza el mejor intento de cancelar el subárbol del trabajo raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas se cancelará de manera transitiva si es posible.|
|[is_canceling](#is_canceling)|Informa al llamador de si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que se llamara al método `cancel` en el objeto `structured_task_group` (aunque, por tanto, se califica este método para que devuelva **true**). Es posible que el objeto de `structured_task_group` se esté ejecutando en línea y que se haya cancelado un grupo de tareas en el árbol de trabajo. En casos como estos en los que el tiempo de ejecución puede determinar con anterioridad el tiempo que pasará la cancelación a través de este objeto `structured_task_group`, también se devolverá **true** .|
|[run](#run)|Sobrecargado. Programa una tarea en el objeto de `structured_task_group`. El autor de la llamada administra la duración del objeto `task_handle` pasado en el parámetro `_Task_handle`. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada por ese parámetro.|
|[run_and_wait](#run_and_wait)|Sobrecargado. Programa una tarea para que se ejecute en línea en el contexto de llamada con la ayuda del objeto `structured_task_group` para la compatibilidad con la cancelación completa. Si se pasa un objeto `task_handle` como un parámetro a `run_and_wait`, el llamador es responsable de administrar la duración del objeto `task_handle`. A continuación, la función espera hasta que todo el trabajo en el objeto de `structured_task_group` se haya completado o cancelado.|
|[currir](#wait)|Espera hasta que se haya completado o cancelado todo el trabajo en el `structured_task_group`.|

## <a name="remarks"></a>Observaciones

Hay una serie de restricciones graves aplicadas al uso de un objeto `structured_task_group` para obtener el rendimiento:

- Varios subprocesos no pueden usar un solo `structured_task_group` objeto. Todas las operaciones en un objeto de `structured_task_group` deben realizarse mediante el subproceso que creó el objeto. Las dos excepciones a esta regla son las funciones miembro `cancel` y `is_canceling`. El objeto puede no estar en la lista de captura de una expresión lambda y usarse dentro de una tarea, a menos que la tarea use una de las operaciones de cancelación.

- Todas las tareas programadas para un objeto de `structured_task_group` se programan mediante el uso de objetos de `task_handle` que debe administrar explícitamente la duración de.

- Varios grupos solo se pueden usar en un orden absolutamente anidado. Si se declaran dos objetos `structured_task_group`, el segundo que se declara (el interno) debe destruirse antes de que se llame a cualquier método excepto a `cancel` o `is_canceling` en el primero (el externo). Esta condición es verdadera en el caso de simplemente declarar varios objetos `structured_task_group` dentro de los mismos ámbitos o anidados funcionalmente, así como el caso de una tarea que se puso en cola en el `structured_task_group` a través de los métodos `run` o `run_and_wait`.

- A diferencia de la clase de `task_group` general, todos los Estados de la clase `structured_task_group` son finales. Una vez que haya puesto en cola las tareas en el grupo y haya esperado a que se completen, no puede volver a usar el mismo grupo.

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`structured_task_group`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="cancel"></a>Cancelar

Realiza el mejor intento de cancelar el subárbol del trabajo raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas se cancelará de manera transitiva si es posible.

```cpp
void cancel();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="is_canceling"></a>is_canceling

Informa al llamador de si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que se llamara al método `cancel` en el objeto `structured_task_group` (aunque, por tanto, se califica este método para que devuelva **true**). Es posible que el objeto de `structured_task_group` se esté ejecutando en línea y que se haya cancelado un grupo de tareas en el árbol de trabajo. En casos como estos en los que el tiempo de ejecución puede determinar con anterioridad el tiempo que pasará la cancelación a través de este objeto `structured_task_group`, también se devolverá **true** .

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Valor devuelto

Una indicación de si el objeto `structured_task_group` está en medio de una cancelación (o se garantiza que sea breve).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="run"></a>realizar

Programa una tarea en el objeto de `structured_task_group`. El autor de la llamada administra la duración del objeto `task_handle` pasado en el parámetro `_Task_handle`. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada por ese parámetro.

```cpp
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
Tipo del objeto de función que se invocará para ejecutar el cuerpo del identificador de la tarea.

*_Task_handle*<br/>
Identificador del trabajo que se va a programar. Tenga en cuenta que el autor de la llamada tiene la responsabilidad de la duración de este objeto. El motor en tiempo de ejecución seguirá esperando que esté activo hasta que se haya llamado al método `wait` o `run_and_wait` en este objeto `structured_task_group`.

*_Placement*<br/>
Referencia a la ubicación donde debe ejecutarse la tarea representada por el parámetro `_Task_handle`.

### <a name="remarks"></a>Observaciones

El tiempo de ejecución crea una copia de la función de trabajo que se pasa a este método. Los cambios de estado que se producen en un objeto de función que se pasa a este método no aparecerán en la copia de ese objeto de función.

Si el `structured_task_group` se destruye como resultado del desenredado de la pila de una excepción, no es necesario garantizar que se ha realizado una llamada al método `wait` o `run_and_wait`. En este caso, el destructor se cancelará correctamente y se esperará a que se complete la tarea representada por el parámetro `_Task_handle`.

Produce una excepción [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) si el identificador de tarea proporcionado por el parámetro `_Task_handle` ya se ha programado en un objeto de grupo de tareas a través del método `run` y no hay ninguna llamada intermedia al método `wait` o `run_and_wait` en ese grupo de tareas.

## <a name="run_and_wait"></a>run_and_wait

Programa una tarea para que se ejecute en línea en el contexto de llamada con la ayuda del objeto `structured_task_group` para la compatibilidad con la cancelación completa. Si se pasa un objeto `task_handle` como un parámetro a `run_and_wait`, el llamador es responsable de administrar la duración del objeto `task_handle`. A continuación, la función espera hasta que todo el trabajo en el objeto de `structured_task_group` se haya completado o cancelado.

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se invocará para ejecutar la tarea.

*_Task_handle*<br/>
Identificador de la tarea que se ejecutará insertada en el contexto de la llamada. Tenga en cuenta que el autor de la llamada tiene la responsabilidad de la duración de este objeto. El motor en tiempo de ejecución seguirá esperando que esté activo hasta que el método `run_and_wait` termine la ejecución.

*_Func*<br/>
Función a la que se llamará para invocar el cuerpo del trabajo. Puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="return-value"></a>Valor devuelto

Indica si se ha satisfecho la espera o si se ha cancelado el grupo de tareas, debido a una operación de cancelación explícita o a que se ha producido una excepción desde una de sus tareas. Para obtener más información, vea [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Observaciones

Tenga en cuenta que una o varias de las tareas programadas para este `structured_task_group` objeto pueden ejecutarse alineadas en el contexto de la llamada.

Si una o varias de las tareas programadas para este objeto `structured_task_group` producen una excepción, el tiempo de ejecución seleccionará una de estas excepciones de su elección y la propagará fuera de la llamada al método `run_and_wait`.

Una vez que la función devuelve, el objeto de `structured_task_group` se considera en un estado final y no debe usarse. Tenga en cuenta que el uso después de que el método `run_and_wait` devuelva el resultado será un comportamiento indefinido.

En la ruta de acceso no excepcional de la ejecución, tiene un mandato para llamar a este método o al método `wait` antes de que se ejecute el destructor del `structured_task_group`.

## <a name="ctor"></a>structured_task_group

Construye un nuevo objeto `structured_task_group`.

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>Parámetros

*_CancellationToken*<br/>
Token de cancelación que se va a asociar a este grupo de tareas estructurado. El grupo de tareas estructurado se cancelará cuando se cancele el token.

### <a name="remarks"></a>Observaciones

El constructor que toma un token de cancelación crea una `structured_task_group` que se cancelará cuando se cancele el origen asociado al token. Proporcionar un token de cancelación explícito también aísla este grupo de tareas estructurado de participar en una cancelación implícita de un grupo primario con un token diferente o sin token.

## <a name="dtor"></a>~ structured_task_group

Destruye un objeto `structured_task_group`. Se espera llamar al método `wait` o `run_and_wait` en el objeto antes de que se ejecute el destructor, a menos que el destructor se esté ejecutando como resultado del desenredado de la pila debido a una excepción.

```cpp
~structured_task_group();
```

### <a name="remarks"></a>Observaciones

Si el destructor se ejecuta como resultado de la ejecución normal (por ejemplo, no desenredado de pila debido a una excepción) y no se ha llamado a los métodos `wait` ni `run_and_wait`, el destructor puede producir una excepción [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>currir

Espera hasta que se haya completado o cancelado todo el trabajo en el `structured_task_group`.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Valor devuelto

Indica si se ha satisfecho la espera o si se ha cancelado el grupo de tareas, debido a una operación de cancelación explícita o a que se ha producido una excepción desde una de sus tareas. Para obtener más información, vea [task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>Observaciones

Tenga en cuenta que una o varias de las tareas programadas para este `structured_task_group` objeto pueden ejecutarse alineadas en el contexto de la llamada.

Si una o varias de las tareas programadas para este objeto `structured_task_group` producen una excepción, el tiempo de ejecución seleccionará una de estas excepciones de su elección y la propagará fuera de la llamada al método `wait`.

Una vez que la función devuelve, el objeto de `structured_task_group` se considera en un estado final y no debe usarse. Tenga en cuenta que el uso después de que el método `wait` devuelva el resultado será un comportamiento indefinido.

En la ruta de acceso no excepcional de la ejecución, tiene un mandato para llamar a este método o al método `run_and_wait` antes de que se ejecute el destructor del `structured_task_group`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[task_group (clase)](task-group-class.md)<br/>
[task_handle (clase)](task-handle-class.md)
