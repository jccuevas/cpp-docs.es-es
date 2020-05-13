---
title: tarea (Clase) (Motor Runtime de simultaneidad)
ms.date: 07/30/2019
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358735"
---
# <a name="task-class-concurrency-runtime"></a>tarea (Clase) (Motor Runtime de simultaneidad)

La clase `task` de la biblioteca de patrones de procesamiento paralelo (PPL). Un `task` objeto representa el trabajo que se puede ejecutar de forma asincrónica y simultánea con otras tareas y el trabajo paralelo generado por algoritmos paralelos en el Runtime de simultaneidad. Genera un resultado de tipo `_ResultType` al finalizar correctamente. Las tareas de tipo `task<void>` no producen ningún resultado. Es posible esperar y cancelar una tarea de forma independiente al resto de tareas. También se puede componer con otras `then`tareas utilizando los patrones continuations( y join( `when_all`) y choice( `when_any`). Cuando se asigna un objeto de tarea a `std::shared_ptr`una nueva variable, el comportamiento es el de ; en otras palabras, ambos objetos representan la misma tarea subyacente.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parámetros

*_ResultType*<br/>
El tipo del resultado que produce la tarea.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`result_type`|El tipo del resultado que un objeto de esta clase produce.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Tarea](#ctor)|Sobrecargado. Construye un objeto `task`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get](#get)|Sobrecargado. Devuelve el resultado que esta tarea generó. Si la tarea no está en un estado terminal, una llamada a `get` esperará a que finalice la tarea. Este método no devuelve un valor cuando se llama en una tarea con un `result_type` de `void`.|
|[is_apartment_aware](#is_apartment_aware)|Determina si la tarea desempaqueta una interfaz `IAsyncInfo` de Windows en tiempo de ejecución o si desciende de esta tarea.|
|[is_done](#is_done)|Determina si se completa la tarea.|
|[Programador](#scheduler)|Devuelve el programador para esta tarea|
|[Entonces](#then)|Sobrecargado. Agrega una tarea de continuación a esta tarea.|
|[Esperar](#wait)|Espera que esta tarea alcance un estado terminal. Es posible que `wait` ejecute la tarea alineada, si se cumplen todas las dependencias de tareas, y todavía no se ha detectado para la ejecución de un trabajador en segundo plano.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[¡Operador!](#operator_neq)|Sobrecargado. Determina si dos objetos `task` representan diferentes tareas internas.|
|[operador](#operator_eq)|Sobrecargado. Reemplaza el contenido de un objeto `task` con otro.|
|[operadora](#operator_eq_eq)|Sobrecargado. Determina si dos objetos `task` representan la misma tarea interna.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Paralelismo](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)de tareas .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

## <a name="get"></a><a name="get"></a>Obtener

Devuelve el resultado que esta tarea generó. Si la tarea no está en un estado terminal, una llamada a `get` esperará a que finalice la tarea. Este método no devuelve un valor cuando se llama en una tarea con un `result_type` de `void`.

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Valor devuelto

Resultado de la tarea.

### <a name="remarks"></a>Observaciones

Si se cancela la tarea, `get` una llamada a producirá una [task_canceled](task-canceled-class.md) excepción. Si la tarea encontró una excepción diferente o si se propagó una excepción desde una tarea anterior, una llamada a `get` iniciará esta excepción.

> [!IMPORTANT]
> En una aplicación para la Plataforma universal de Windows (UWP), no `wait` `get`llame a [concurrency::task::wait](#wait) o `get` ( llamadas ) en el código que se ejecuta en el subproceso de interfaz de usuario. De lo contrario, el tiempo de ejecución produce [concurrency::invalid_operation](invalid-operation-class.md) porque estos métodos bloquean el subproceso actual y pueden hacer que la aplicación no responda. Sin embargo, `get` puede llamar al método para recibir el resultado de la tarea anterior en una continuación basada en tareas porque el resultado está inmediatamente disponible.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Determina si la tarea desempaqueta una interfaz `IAsyncInfo` de Windows en tiempo de ejecución o si desciende de esta tarea.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si la tarea `IAsyncInfo` desenvuelve una interfaz o desciende de una tarea de este tipo, **false** en caso contrario.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>task::is_done (Método de ejecución de simultaneidad)

Determina si se completa la tarea.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Valor devuelto

True si la tarea se ha completado, false en caso contrario.

### <a name="remarks"></a>Observaciones

La función devuelve true si la tarea se completa o cancela (con o sin excepción de usuario).

## <a name="operator"></a><a name="operator_neq"></a>¡Operador!

Determina si dos objetos `task` representan diferentes tareas internas.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La tarea que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos hacen referencia a diferentes tareas subyacentes, y **false** en caso contrario.

## <a name="operator"></a><a name="operator_eq"></a>operador

Reemplaza el contenido de un objeto `task` con otro.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `task` de origen.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Dado que `task` se comporta como un puntero inteligente, después de una asignación de copia, este objeto `task` representa la misma tarea real que `_Other`.

## <a name="operator"></a><a name="operator_eq_eq"></a>operadora

Determina si dos objetos `task` representan la misma tarea interna.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La tarea que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos hacen referencia a la misma tarea subyacente y **false** en caso contrario.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>método task::scheduler (Runtime de simultaneidad)

Devuelve el programador para esta tarea

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al programador

## <a name="task"></a>Tarea <a name="ctor"></a>

Construye un objeto `task`.

```cpp
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del parámetro a partir del cual se va a construir la tarea.

*_Param*<br/>
Parámetro desde el que se va a construir la tarea. Esto podría ser una lambda, `task_completion_event<result_type>` un objeto de función, un objeto o Windows::Foundation::IAsyncInfo si usa tareas en la aplicación de Windows en tiempo de ejecución. El lambda o el objeto de `std::function<X(void)>`función debe ser un `result_type` `task<result_type>`tipo equivalente a , donde X puede ser una variable de tipo , , o un Windows::Foundation::IAsyncInfo en aplicaciones de Windows en tiempo de ejecución.

*_TaskOptions*<br/>
Entre las opciones de tareas se incluyen el token de cancelación, el programador, etc.

*_Other*<br/>
Objeto `task` de origen.

### <a name="remarks"></a>Observaciones

El constructor predeterminado de un objeto `task` solo está presente para permitir que las tareas se usen dentro de los contenedores. No se puede usar una tarea construida de forma predeterminada hasta que no se le asigne una tarea válida. Métodos `get`como `wait` `then` , o producirá una [excepción invalid_argument](../../../standard-library/invalid-argument-class.md) cuando se llama en una tarea construida predeterminada.

Las tareas que se creen a partir de un objeto `task_completion_event` se completarán (y sus continuaciones se programarán) cuando se establezca el evento de finalización de las tareas.

La versión del constructor que toma un token de cancelación crea una tarea que se puede cancelar mediante el token `cancellation_token_source` desde el que se obtuvo. Las tareas que se crean sin token de cancelación no se pueden cancelar.

Las tareas que se crean a partir de la interfaz `Windows::Foundation::IAsyncInfo` o de una expresión lambda que devuelve una interfaz `IAsyncInfo` alcanzan su estado de terminal cuando se completa la operación o acción asincrónica insertada en Windows Runtime. De forma similar, las tareas `task<result_type>` creadas a partir de una expresión lambda que devuelve un estado de terminal alcanzan su estado de terminal cuando la tarea interna alcanza su estado de terminal y no cuando vuelve la expresión lambda.

El objeto `task` se comporta como un puntero inteligente y se puede pasar con seguridad por valor. Varios subprocesos pueden tener acceso a este objeto sin necesidad de bloqueos.

Las sobrecargas del constructor que toman una interfaz Windows::Foundation::IAsyncInfo o una expresión lambda que devuelve dicha interfaz solo están disponibles para las aplicaciones de Windows en tiempo de ejecución.

Para obtener más información, consulte [Paralelismo](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)de tareas .

## <a name="then"></a><a name="then"></a>Entonces

Agrega una tarea de continuación a esta tarea.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que invocará esta tarea.

*_Func*<br/>
Función de continuación que se va a ejecutar cuando se complete esta tarea. Esta función de continuación debe tomar como entrada una variable o un objeto `result_type` o `task<result_type>`, donde `result_type` es el tipo del resultado que esta tarea produce.

*_TaskOptions*<br/>
Entre las opciones de tareas se incluyen el token de cancelación, el programador y el contexto de continuación. De forma predeterminada, las tres opciones anteriores se heredan de la tarea precedente

*_CancellationToken*<br/>
Token de cancelación que se va a asociar a la tarea de continuación. Las tareas de continuación que se creen sin un token de cancelación heredarán el token de la tarea que le precede.

*_ContinuationContext*<br/>
Variable que especifica dónde debe ejecutarse la continuación. Esta variable solo es útil cuando se usa en una aplicación para UWP. Para obtener más información, consulte [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Valor devuelto

Tarea de continuación creada recientemente. El tipo de resultado de la tarea devuelta está determinado por lo que `_Func` devuelve.

### <a name="remarks"></a>Observaciones

Las sobrecargas `then` de que toman un lambda o functor que devuelve un Windows::Foundation::IAsyncInfo interfaz, solo están disponibles para las aplicaciones de Windows en tiempo de ejecución.

Para obtener más información sobre cómo utilizar las continuaciones de tareas para componer trabajo asincrónico, vea [Paralelismo](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)de tareas .

## <a name="wait"></a><a name="wait"></a>Esperar

Espera que esta tarea alcance un estado terminal. Es posible que `wait` ejecute la tarea alineada, si se cumplen todas las dependencias de tareas, y todavía no se ha detectado para la ejecución de un trabajador en segundo plano.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de `task_status`, que podría ser `completed` o `canceled`. Si la tarea encontró una excepción durante la ejecución o se propagó una excepción desde una tarea anterior, `wait` producirá esta excepción.

### <a name="remarks"></a>Observaciones

> [!IMPORTANT]
> En una aplicación para la Plataforma universal `wait` de Windows (UWP), no llame al código que se ejecuta en el subproceso de interfaz de usuario. De lo contrario, el runtime produce [concurrency::invalid_operation](invalid-operation-class.md) porque este método bloquea el subproceso actual y pueden provocar que la aplicación no responda. Sin embargo, puede llamar al método [concurrency::task::get](#get) para recibir el resultado de la tarea anterior en una continuación basada en tareas.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
