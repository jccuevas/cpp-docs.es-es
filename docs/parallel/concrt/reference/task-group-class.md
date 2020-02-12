---
title: task_group (Clase)
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142569"
---
# <a name="task_group-class"></a>task_group (Clase)

La clase `task_group` representa una colección de trabajo paralelo que es posible esperar o cancelar.

## <a name="syntax"></a>Sintaxis

```cpp
class task_group;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_group](#ctor)|Sobrecargado. Construye un nuevo objeto `task_group`.|
|[~ task_group destructor](#dtor)|Destruye un objeto `task_group`. Se espera llamar al método `wait` o `run_and_wait` en el objeto antes de que se ejecute el destructor, a menos que el destructor se esté ejecutando como resultado del desenredado de la pila debido a una excepción.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[cancel](#cancel)|Realiza el mejor intento de cancelar el subárbol del trabajo raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas se cancelará de manera transitiva si es posible.|
|[is_canceling](#is_canceling)|Informa al llamador de si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que se llamara al método `cancel` en el objeto `task_group` (aunque, por tanto, se califica este método para que devuelva `true`). Es posible que el objeto de `task_group` se esté ejecutando en línea y que se haya cancelado un grupo de tareas en el árbol de trabajo. En casos como estos en los que el tiempo de ejecución puede determinar con anterioridad el tiempo que pasará la cancelación a través de este objeto de `task_group`, `true` se devolverá también.|
|[run](#run)|Sobrecargado. Programa una tarea en el objeto de `task_group`. Si se pasa un objeto `task_handle` como un parámetro a `run`, el llamador es responsable de administrar la duración del objeto `task_handle`. La versión del método que toma una referencia a un objeto de función como parámetro implica la asignación del montón dentro del tiempo de ejecución que puede ser menor que el uso de la versión que toma una referencia a un objeto `task_handle`. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada por ese parámetro.|
|[run_and_wait](#run_and_wait)|Sobrecargado. Programa una tarea para que se ejecute en línea en el contexto de llamada con la ayuda del objeto `task_group` para la compatibilidad con la cancelación completa. A continuación, la función espera hasta que todo el trabajo en el objeto de `task_group` se haya completado o cancelado. Si se pasa un objeto `task_handle` como un parámetro a `run_and_wait`, el llamador es responsable de administrar la duración del objeto `task_handle`.|
|[currir](#wait)|Espera hasta que todo el trabajo en el objeto de `task_group` se haya completado o cancelado.|

## <a name="remarks"></a>Observaciones

A diferencia de la clase de `structured_task_group` muy restringida, la clase `task_group` es una construcción mucho más general. No tiene ninguna de las restricciones descritas en [structured_task_group](structured-task-group-class.md). `task_group` objetos se pueden usar de forma segura en los subprocesos y usarse de forma libre. El inconveniente de la construcción `task_group` es que es posible que no funcione tan bien como la construcción `structured_task_group` para tareas que realizan pequeñas cantidades de trabajo.

Para obtener más información, consulte [paralelismo de tareas](../task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_group`

## <a name="requirements"></a>Requisitos

**Encabezado:** PPL. h

**Espacio de nombres:** simultaneidad

## <a name="cancel"></a>Cancelar

Realiza el mejor intento de cancelar el subárbol del trabajo raíz en este grupo de tareas. Cada tarea programada en el grupo de tareas se cancelará de manera transitiva si es posible.

```cpp
void cancel();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [cancelación](../cancellation-in-the-ppl.md).

## <a name="is_canceling"></a>is_canceling

Informa al llamador de si el grupo de tareas está actualmente en medio de una cancelación. Esto no indica necesariamente que se llamara al método `cancel` en el objeto `task_group` (aunque, por tanto, se califica este método para que devuelva `true`). Es posible que el objeto de `task_group` se esté ejecutando en línea y que se haya cancelado un grupo de tareas en el árbol de trabajo. En casos como estos en los que el tiempo de ejecución puede determinar con anterioridad el tiempo que pasará la cancelación a través de este objeto de `task_group`, `true` se devolverá también.

```cpp
bool is_canceling();
```

### <a name="return-value"></a>Valor devuelto

Una indicación de si el objeto `task_group` está en medio de una cancelación (o se garantiza que sea breve).

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [cancelación](../cancellation-in-the-ppl.md).

## <a name="run"></a>realizar

Programa una tarea en el objeto de `task_group`. Si se pasa un objeto `task_handle` como un parámetro a `run`, el llamador es responsable de administrar la duración del objeto `task_handle`. La versión del método que toma una referencia a un objeto de función como parámetro implica la asignación del montón dentro del tiempo de ejecución que puede ser menor que el uso de la versión que toma una referencia a un objeto `task_handle`. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada por ese parámetro.

```cpp
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
Tipo del objeto de función que se invocará para ejecutar el cuerpo del identificador de la tarea.

*_Func*<br/>
Función a la que se llamará para invocar el cuerpo de la tarea. Puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

*_Placement*<br/>
Referencia a la ubicación donde debe ejecutarse la tarea representada por el parámetro `_Func`.

*_Task_handle*<br/>
Identificador del trabajo que se va a programar. Tenga en cuenta que el autor de la llamada tiene la responsabilidad de la duración de este objeto. El motor en tiempo de ejecución seguirá esperando que esté activo hasta que se haya llamado al método `wait` o `run_and_wait` en este objeto `task_group`.

### <a name="remarks"></a>Observaciones

El motor en tiempo de ejecución programa la función de trabajo proporcionada para que se ejecute en un momento posterior, que puede ser después de que la función de llamada vuelva. Este método usa un objeto [task_handle](task-handle-class.md) para contener una copia de la función de trabajo proporcionada. Por lo tanto, los cambios de estado que se producen en un objeto de función que se pasa a este método no aparecerán en la copia de ese objeto de función. Además, asegúrese de que la duración de los objetos que pase por puntero o por referencia a la función de trabajo siga siendo válida hasta que se devuelva la función de trabajo.

Si el `task_group` se destruye como resultado del desenredado de la pila de una excepción, no es necesario garantizar que se ha realizado una llamada al método `wait` o `run_and_wait`. En este caso, el destructor se cancelará correctamente y se esperará a que se complete la tarea representada por el parámetro `_Task_handle`.

El método produce una excepción [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md) si el identificador de tarea proporcionado por el parámetro `_Task_handle` ya se ha programado en un objeto de grupo de tareas a través del método `run` y no hay ninguna llamada intermedia al método `wait` o `run_and_wait` en ese grupo de tareas.

## <a name="run_and_wait"></a>run_and_wait

Programa una tarea para que se ejecute en línea en el contexto de llamada con la ayuda del objeto `task_group` para la compatibilidad con la cancelación completa. A continuación, la función espera hasta que todo el trabajo en el objeto de `task_group` se haya completado o cancelado. Si se pasa un objeto `task_handle` como un parámetro a `run_and_wait`, el llamador es responsable de administrar la duración del objeto `task_handle`.

```cpp
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
Tipo del objeto de función que se invocará para ejecutar el cuerpo de la tarea.

*_Task_handle*<br/>
Identificador de la tarea que se ejecutará insertada en el contexto de la llamada. Tenga en cuenta que el autor de la llamada tiene la responsabilidad de la duración de este objeto. El motor en tiempo de ejecución seguirá esperando que esté activo hasta que el método `run_and_wait` termine la ejecución.

*_Func*<br/>
Función a la que se llamará para invocar el cuerpo del trabajo. Puede ser una expresión lambda u otro objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="return-value"></a>Valor devuelto

Indica si se ha satisfecho la espera o si se ha cancelado el grupo de tareas, debido a una operación de cancelación explícita o a que se ha producido una excepción desde una de sus tareas. Para obtener más información, vea [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Observaciones

Tenga en cuenta que una o varias de las tareas programadas para este `task_group` objeto pueden ejecutarse alineadas en el contexto de la llamada.

Si una o varias de las tareas programadas para este objeto `task_group` producen una excepción, el tiempo de ejecución seleccionará una de estas excepciones de su elección y la propagará fuera de la llamada al método `run_and_wait`.

Al volver del método `run_and_wait` en un objeto `task_group`, el tiempo de ejecución restablece el objeto a un estado limpio en el que se puede volver a usar. Esto incluye el caso en el que se canceló el objeto de `task_group`.

En la ruta de acceso no excepcional de la ejecución, tiene un mandato para llamar a este método o al método `wait` antes de que se ejecute el destructor del `task_group`.

## <a name="ctor"></a>task_group

Construye un nuevo objeto `task_group`.

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>Parámetros

*_CancellationToken*<br/>
Token de cancelación que se va a asociar a este grupo de tareas. El grupo de tareas se cancelará cuando se cancele el token.

### <a name="remarks"></a>Observaciones

El constructor que toma un token de cancelación crea una `task_group` que se cancelará cuando se cancele el origen asociado al token. Proporcionar un token de cancelación explícito también aísla este grupo de tareas de participar en una cancelación implícita de un grupo primario con un token diferente o sin token.

## <a name="dtor"></a>~ task_group

Destruye un objeto `task_group`. Se espera llamar al método `wait` o `run_and_wait` en el objeto antes de que se ejecute el destructor, a menos que el destructor se esté ejecutando como resultado del desenredado de la pila debido a una excepción.

```cpp
~task_group();
```

### <a name="remarks"></a>Observaciones

Si el destructor se ejecuta como resultado de la ejecución normal (por ejemplo, no desenredado de pila debido a una excepción) y no se ha llamado a los métodos `wait` ni `run_and_wait`, el destructor puede producir una excepción [missing_wait](missing-wait-class.md) .

## <a name="wait"></a>currir

Espera hasta que todo el trabajo en el objeto de `task_group` se haya completado o cancelado.

```cpp
task_group_status wait();
```

### <a name="return-value"></a>Valor devuelto

Indica si se ha satisfecho la espera o si se ha cancelado el grupo de tareas, debido a una operación de cancelación explícita o a que se ha producido una excepción desde una de sus tareas. Para obtener más información, vea [task_group_status](concurrency-namespace-enums.md#task_group_status).

### <a name="remarks"></a>Observaciones

Tenga en cuenta que una o varias de las tareas programadas para este `task_group` objeto pueden ejecutarse alineadas en el contexto de la llamada.

Si una o varias de las tareas programadas para este objeto `task_group` producen una excepción, el tiempo de ejecución seleccionará una de estas excepciones de su elección y la propagará fuera de la llamada al método `wait`.

La llamada a `wait` en un objeto `task_group` lo restablece a un estado limpio en el que se puede volver a usar. Esto incluye el caso en el que se canceló el objeto de `task_group`.

En la ruta de acceso no excepcional de la ejecución, tiene un mandato para llamar a este método o al método `run_and_wait` antes de que se ejecute el destructor del `task_group`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[structured_task_group (clase)](structured-task-group-class.md)<br/>
[task_handle (clase)](task-handle-class.md)
