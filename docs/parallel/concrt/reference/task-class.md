---
title: tarea (Clase) (Motor Runtime de simultaneidad)
ms.date: 11/04/2016
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
ms.openlocfilehash: 99676ac0fff9584cd8453562f8918f6cadd66666
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385211"
---
# <a name="task-class-concurrency-runtime"></a>tarea (Clase) (Motor Runtime de simultaneidad)

La clase `task` de la biblioteca de patrones de procesamiento paralelo (PPL). Un objeto `task` representa el trabajo que se puede ejecutar de forma asincrónica y de forma simultánea con otras tareas y trabajos paralelos generados por los algoritmos paralelos en el runtime de simultaneidad. Genera un resultado de tipo `_ResultType` al finalizar correctamente. Las tareas de tipo `task<void>` no producen ningún resultado. Es posible esperar y cancelar una tarea de forma independiente al resto de tareas. También pueden combinarse con otras tareas mediante continuaciones ( `then`) y combinación ( `when_all`) y elección ( `when_any`) patrones.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto de tarea.

*_ReturnType*<br/>
Tipo de resultado de esta tarea.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`result_type`|El tipo del resultado que un objeto de esta clase produce.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[task](#ctor)|Sobrecargado. Construye un objeto `task`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get](#get)|Sobrecargado. Devuelve el resultado que esta tarea generó. Si la tarea no está en un estado terminal, una llamada a `get` esperará a que finalice la tarea. Este método no devuelve un valor cuando se llama en una tarea con un `result_type` de `void`.|
|[is_apartment_aware](#is_apartment_aware)|Determina si la tarea desempaqueta una interfaz `IAsyncInfo` de Windows en tiempo de ejecución o si desciende de esta tarea.|
|[is_done](#is_done)|Determina si se completa la tarea.|
|[scheduler](#scheduler)|Devuelve el programador para esta tarea|
|[then](#then)|Sobrecargado. Agrega una tarea de continuación a esta tarea.|
|[wait](#wait)|Espera que esta tarea alcance un estado terminal. Es posible que `wait` ejecute la tarea alineada, si se cumplen todas las dependencias de tareas, y todavía no se ha detectado para la ejecución de un trabajador en segundo plano.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Sobrecargado. Determina si dos objetos `task` representan diferentes tareas internas.|
|[operator=](#operator_eq)|Sobrecargado. Reemplaza el contenido de un objeto `task` con otro.|
|[operator==](#operator_eq_eq)|Sobrecargado. Determina si dos objetos `task` representan la misma tarea interna.|

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

##  <a name="get"></a> Obtener

Devuelve el resultado que esta tarea generó. Si la tarea no está en un estado terminal, una llamada a `get` esperará a que finalice la tarea. Este método no devuelve un valor cuando se llama en una tarea con un `result_type` de `void`.

```
_ReturnType get() const;

void get() const;
```

### <a name="return-value"></a>Valor devuelto

Resultado de la tarea.

### <a name="remarks"></a>Comentarios

Si se cancela la tarea, una llamada a `get` producirá un [task_canceled](task-canceled-class.md) excepción. Si la tarea encontró una excepción diferente o si se propagó una excepción desde una tarea anterior, una llamada a `get` iniciará esta excepción.

> [!IMPORTANT]
>  En una aplicación plataforma Universal de Windows (UWP), no llame a [concurrency::task::wait](#wait) o `get` ( `wait` llamadas `get`) en el código que se ejecuta en el subproceso de interfaz de usuario. En caso contrario, el runtime produce [Concurrency:: invalid_operation](invalid-operation-class.md) porque estos métodos se bloquea el subproceso actual y puede provocar que la aplicación deje de responder. Sin embargo, puede llamar a la `get` método para recibir el resultado de la tarea anterior en una continuación basada en tareas porque el resultado está disponible inmediatamente.

##  <a name="is_apartment_aware"></a> is_apartment_aware

Determina si la tarea desempaqueta una interfaz `IAsyncInfo` de Windows en tiempo de ejecución o si desciende de esta tarea.

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si la tarea desencapsula una `IAsyncInfo` interfaz o desciende de dicha tarea, **false** en caso contrario.

##  <a name="is_done"></a>  Task::is_done (método) (Runtime de simultaneidad)

Determina si se completa la tarea.

```
bool is_done() const;
```

### <a name="return-value"></a>Valor devuelto

True si la tarea se ha completado, false en caso contrario.

### <a name="remarks"></a>Comentarios

La función devuelve true si la tarea se completaban o cancelaban (con o sin la excepción de usuario).

##  <a name="operator_neq"></a> operator!=

Determina si dos objetos `task` representan diferentes tareas internas.

```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La tarea para comparar.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos que hacen referencia a distintas tareas subyacentes, y **false** en caso contrario.

##  <a name="operator_eq"></a> operator=

Reemplaza el contenido de un objeto `task` con otro.

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `task` de origen.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Dado que `task` se comporta como un puntero inteligente, después de una asignación de copia, este objeto `task` representa la misma tarea real que `_Other`.

##  <a name="operator_eq_eq"></a> operador ==

Determina si dos objetos `task` representan la misma tarea interna.

```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parámetros

*_Rhs*<br/>
La tarea para comparar.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos que hacen referencia a la misma tarea subyacente, y **false** en caso contrario.

##  <a name="scheduler"></a>  Task::Scheduler (método) (Runtime de simultaneidad)

Devuelve el programador para esta tarea

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al programador

##  <a name="ctor"></a> Tarea

Construye un objeto `task`.

```
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
Parámetro desde el que se va a construir la tarea. Esto podría ser una expresión lambda, un objeto de función, un `task_completion_event<result_type>` objeto o un Windows::Foundation::IAsyncInfo si se usan tareas en la aplicación en tiempo de ejecución de Windows. El objeto de función o expresión lambda debe ser un tipo equivalente a `std::function<X(void)>`, donde X puede ser una variable de tipo `result_type`, `task<result_type>`, o un Windows::Foundation::IAsyncInfo en aplicaciones de Windows en tiempo de ejecución.

*_TaskOptions*<br/>
Entre las opciones de tareas se incluyen el token de cancelación, el programador, etc.

*_Other*<br/>
Objeto `task` de origen.

### <a name="remarks"></a>Comentarios

El constructor predeterminado de un objeto `task` solo está presente para permitir que las tareas se usen dentro de los contenedores. No se puede usar una tarea construida de forma predeterminada hasta que no se le asigne una tarea válida. Los métodos como `get`, `wait` o `then` producirá una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción cuando se llama en una tarea construida predeterminada.

Las tareas que se creen a partir de un objeto `task_completion_event` se completarán (y sus continuaciones se programarán) cuando se establezca el evento de finalización de las tareas.

La versión del constructor que toma un token de cancelación crea una tarea que se puede cancelar mediante el token `cancellation_token_source` desde el que se obtuvo. Las tareas que se crean sin token de cancelación no se pueden cancelar.

Las tareas que se crean a partir de la interfaz `Windows::Foundation::IAsyncInfo` o de una expresión lambda que devuelve una interfaz `IAsyncInfo` alcanzan su estado de terminal cuando se completa la operación o acción asincrónica insertada en Windows Runtime. De manera similar, las tareas que se crean a partir de una expresión lamda que devuelve un objeto `task<result_type>` alcanzan su estado terminal cuando la tarea interna alcanza su estado terminal, y no cuando la expresión lamda devuelve un resultado.

El objeto `task` se comporta como un puntero inteligente y se puede pasar con seguridad por valor. Varios subprocesos pueden tener acceso a este objeto sin necesidad de bloqueos.

Las sobrecargas del constructor que toman una interfaz Windows::Foundation::IAsyncInfo o una expresión lambda que devuelve esta interfaz, solo están disponibles para las aplicaciones de Windows Runtime.

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="then"></a> A continuación

Agrega una tarea de continuación a esta tarea.

```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

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

### <a name="remarks"></a>Comentarios

Las sobrecargas de `then` que toman una expresión lambda o functor que devuelve una interfaz Windows::Foundation::IAsyncInfo, solo están disponibles para las aplicaciones de Windows Runtime.

Para obtener más información sobre cómo usar las continuaciones de tareas para crear trabajo asincrónico, vea [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="wait"></a> Espere

Espera que esta tarea alcance un estado terminal. Es posible que `wait` ejecute la tarea alineada, si se cumplen todas las dependencias de tareas, y todavía no se ha detectado para la ejecución de un trabajador en segundo plano.

```
task_status wait() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de `task_status`, que podría ser `completed` o `canceled`. Si la tarea encontró una excepción durante la ejecución o se propagó una excepción desde una tarea anterior, `wait` producirá esta excepción.

### <a name="remarks"></a>Comentarios

> [!IMPORTANT]
>  En una aplicación plataforma Universal de Windows (UWP), no llame a `wait` en el código que se ejecuta en el subproceso de interfaz de usuario. De lo contrario, el runtime produce [concurrency::invalid_operation](invalid-operation-class.md) porque este método bloquea el subproceso actual y pueden provocar que la aplicación no responda. Sin embargo, puede llamar al método [concurrency::task::get](#get) para recibir el resultado de la tarea anterior en una continuación basada en tareas.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
