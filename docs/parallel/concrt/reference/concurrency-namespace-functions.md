---
title: concurrency (Funciones del espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 4005ae888511ec987fe83ab3d616aa0fc3675a22
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424840"
---
# <a name="concurrency-namespace-functions"></a>concurrency (Funciones del espacio de nombres)

||||
|-|-|-|
|[Alloc](#alloc)|[CreateResourceManager (](#createresourcemanager)|[Disabletracing (](#disabletracing)|
|[Enabletracing (](#enabletracing)|[Gratis](#free)|[Getexecutioncontextid (](#getexecutioncontextid)|
|[GetOSVersion (](#getosversion)|[GetProcessorCount (](#getprocessorcount)|[Getprocessornodecount (](#getprocessornodecount)|
|[Getschedulerid (](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[Asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[aparecen](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[currir](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a>Alloc

Asigna un bloque de memoria del tamaño especificado del subasignador de almacenamiento en caché del runtime de simultaneidad.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parámetros

*_NumBytes*<br/>
El número de bytes de memoria que se va a asignar.

### <a name="return-value"></a>Valor devuelto

Puntero a la memoria recién asignada.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los escenarios de la aplicación que podrían beneficiarse del uso del Subasignador de almacenamiento en caché, consulte [programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a>Asend

Una operación de envío asincrónica, que programa una tarea para propagar los datos al bloque de destino.

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de los datos que se van a enviar.

*_Trg*<br/>
Puntero o referencia al destino al que se envían los datos.

*_Data*<br/>
Referencia a los datos que se van a enviar.

### <a name="return-value"></a>Valor devuelto

**true** si se aceptó el mensaje antes de que se devolviera el método, **false** en caso contrario.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [funciones de paso de mensajes](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a>cancel_current_task

Cancela la tarea que se está ejecutando actualmente. Se puede llamar a esta función desde el cuerpo de una tarea para anular la ejecución de la tarea y hacer que obtenga el estado `canceled`.

No está admitido que llame a esta función si no está dentro del cuerpo de un objeto `task`. Esto dará lugar a un comportamiento indefinido como, por ejemplo, un bloqueo en la aplicación.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a>claridad

Borra la cola simultánea, destruyendo todos los elementos actualmente puestos en cola. Este método no es seguro para la simultaneidad.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parámetros

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a>create_async

Crea una construcción asincrónica de Windows Runtime basada en un objeto o función lambda que se ha proporcionado. El tipo devuelto de `create_async` es `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` o `IAsyncOperationWithProgress<TResult, TProgress>^` en función de la signatura de la expresión lambda pasada al método.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Type (Tipo).

*_Func*<br/>
Objeto de función o expresión lambda donde se crea una construcción asincrónica de Windows Runtime.

### <a name="return-value"></a>Valor devuelto

Una construcción asincrónica representada por un IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^ o IAsyncOperationWithProgress\<TResult, TProgress > ^. La interfaz devuelta depende de la signatura de la expresión lambda pasada a la función.

### <a name="remarks"></a>Observaciones

El tipo devuelto de la expresión lambda determina si la construcción es una acción o una operación.

Las expresiones lambda que devuelven "void" provocan la creación de acciones. Las expresiones lambda que devuelven un resultado de tipo `TResult` provocan la creación de operaciones TResult.

La expresión lambda también puede devolver un `task<TResult>` que encapsule el trabajo asincrónico dentro de sí mismo o que sea la continuación de una cadena de tareas que representan el trabajo asincrónico. En este caso, la propia expresión lambda se ejecuta de forma alineada, ya que las tareas son las que se ejecutan de forma asincrónica y el tipo de valor devuelto de una expresión lambda se desempaqueta para generar la construcción asincrónica que devuelve `create_async`. Esto implica que una expresión lambda que devuelve una tarea\<void > producirá la creación de acciones, y una expresión lambda que devuelva una tarea\<TResult > producirá la creación de operaciones TResult.

La expresión lambda puede aceptar cero, uno o dos argumentos. Los argumentos válidos son `progress_reporter<TProgress>` y `cancellation_token`, en ese orden si se utilizan ambos. Una expresión lambda sin argumentos produce la creación de una construcción asincrónica sin la capacidad de informar del progreso. Una expresión lambda que toma un progress_reporter\<TProgress > hará que `create_async` devuelva una construcción asincrónica que informa del progreso de tipo TProgress cada vez que se llama al método `report` del objeto progress_reporter. Una expresión lambda que toma un objeto cancellation_token puede utilizar dicho token para comprobar posibles cancelaciones o pasarlo a las tareas que crea para que la cancelación de la construcción asincrónica dé lugar a la cancelación de dichas tareas.

Si el cuerpo de la expresión lambda o el objeto de función devuelve un resultado (y no una tarea\<TResult >), el expresión lamdba se ejecutará de forma asincrónica dentro del MTA del proceso en el contexto de una tarea que el Runtime crea implícitamente. El método `IAsyncInfo::Cancel` producirá la cancelación de la tarea implícita.

Si el cuerpo de una expresión lambda devuelve una tarea, la expresión lamba se ejecutará de forma alineada y, al declarar la expresión lambda para que tome un argumento del tipo `cancellation_token`, podrá desencadenar la cancelación de cualquier tarea que cree en la expresión lambda pasando dicho token en la creación. Puede utilizar el método `register_callback` del token para hacer que el runtime invoque una devolución de llamada cuando llame a `IAsyncInfo::Cancel` en la acción u operación asincrónica producida.

Esta función solo está disponible para Windows Runtime aplicaciones.

## <a name="createresourcemanager"></a>CreateResourceManager (

Devuelve una interfaz que representa la instancia singleton del Administrador de recursos del runtime de simultaneidad. El Administrador de recursos es el responsable de asignar recursos a los programadores que desean cooperar entre sí.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IResourceManager`.

### <a name="remarks"></a>Observaciones

Varias llamadas subsiguientes a este método devolverán la misma instancia del Administrador de recursos. Cada llamada al método incrementa un recuento de referencias en el Administrador de recursos y debe coincidir con una llamada al método [IResourceManager:: Release](iresourcemanager-structure.md) cuando el programador haya terminado de comunicarse con el administrador de recursos.

se produce [unsupported_os](unsupported-os-class.md) si el Runtime de simultaneidad no admite el sistema operativo.

## <a name="create_task"></a>create_task

Crea un objeto de [tarea](task-class.md) PPL. `create_task` se puede usar en cualquier lugar en el que se ha utilizado un constructor de tarea. Se proporciona principalmente por comodidad, porque permite el uso de la palabra clave `auto` cuando se crean tareas.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del parámetro a partir del cual se va a construir la tarea.

*_ReturnType*<br/>
Type (Tipo).

*_Param*<br/>
Parámetro desde el que se va a construir la tarea. Puede tratarse de un objeto de función o expresión lambda, un objeto de `task_completion_event`, un objeto de `task` diferente o una interfaz Windows:: Foundation:: IAsyncInfo si usa tareas en la aplicación de UWP.

*_TaskOptions*<br/>
Opciones de la tarea.

*_Task*<br/>
Tarea que se va a crear.

### <a name="return-value"></a>Valor devuelto

Nueva tarea de tipo `T`, que se deduce de `_Param`.

### <a name="remarks"></a>Observaciones

La primera sobrecarga se comporta como un constructor de tarea que toma un único parámetro.

La segunda sobrecarga asocia el token de cancelación proporcionado a la tarea recién creada. Si utiliza esta sobrecarga, no se le permite pasar un objeto de `task` diferente como primer parámetro.

El tipo de la tarea devuelta se deduce del primer parámetro de la función. Si `_Param` es un `task_completion_event<T>`, un `task<T>`o un functor que devuelve el tipo `T` o `task<T>`, el tipo de la tarea creada es `task<T>`.

En una aplicación de UWP, si `_Param` es de tipo Windows:: Foundation:: IAsyncOperation\<T > ^ o Windows:: Foundation:: IAsyncOperationWithProgress\<T, P > ^ o un functor que devuelve cualquiera de esos tipos, la tarea creada será de tipo `task<T>`. Si `_Param` es de tipo Windows:: Foundation:: IAsyncAction ^ o Windows:: Foundation:: IAsyncActionWithProgress\<P > ^ o un functor que devuelve cualquiera de esos tipos, la tarea creada tendrá el tipo `task<void>`.

## <a name="disabletracing"></a>Disabletracing (

Deshabilita la traza en el runtime de simultaneidad. Esta función está desusada porque la traza de ETW no está registrada de forma predeterminada.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Valor devuelto

Si el seguimiento se ha deshabilitado correctamente, se devuelve `S_OK`. Si el seguimiento no se inició previamente, se devuelve `E_NOT_STARTED`

## <a name="enabletracing"></a>Enabletracing (

Habilita la traza en el runtime de simultaneidad. Esta función está en desuso porque la traza de ETW ahora está registrada de forma predeterminada.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Valor devuelto

Si el seguimiento se inició correctamente, se devuelve `S_OK`; de lo contrario, se devuelve `E_NOT_STARTED`.

## <a name="free"></a>Ningún

Libera un bloque de memoria asignado previamente mediante el método `Alloc` al subasignador de almacenamiento en caché del runtime de simultaneidad.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parámetros

*_PAllocation*<br/>
Puntero a la memoria previamente asignada por el método `Alloc` que se liberará. Si el parámetro `_PAllocation` está establecido en el valor `NULL`, esté método lo ignorará y volverá inmediatamente.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre los escenarios de la aplicación que podrían beneficiarse del uso del Subasignador de almacenamiento en caché, consulte [programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Valor devuelto

## <a name="getexecutioncontextid"></a>Getexecutioncontextid (

Devuelve un identificador único que se puede asignar a un contexto de ejecución que implementa la interfaz `IExecutionContext`.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Valor devuelto

Identificador único para un contexto de ejecución.

### <a name="remarks"></a>Observaciones

Utilice este método para obtener un identificador para el contexto de ejecución antes de pasar una interfaz `IExecutionContext` como un parámetro a cualquiera de los métodos que ofrece el Administrador de recursos.

## <a name="getosversion"></a>GetOSVersion (

Devuelve la versión del sistema operativo.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Valor devuelto

Valor enumerado que representa el sistema operativo.

### <a name="remarks"></a>Observaciones

se produce [unsupported_os](unsupported-os-class.md) si el Runtime de simultaneidad no admite el sistema operativo.

## <a name="getprocessorcount"></a>GetProcessorCount (

Devuelve el número de subprocesos de hardware en el sistema subyacente.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Valor devuelto

El número de subprocesos de hardware.

### <a name="remarks"></a>Observaciones

se produce [unsupported_os](unsupported-os-class.md) si el Runtime de simultaneidad no admite el sistema operativo.

## <a name="getprocessornodecount"></a>Getprocessornodecount (

Devuelve el número de nodos NUMA o paquetes de procesador en el sistema subyacente.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Valor devuelto

El número de nodos NUMA o paquetes de procesador.

### <a name="remarks"></a>Observaciones

Si el sistema contiene más nodos NUMA que paquetes de procesador, se devuelve el número de nodos NUMA; de lo contrario, se devuelve el número de paquetes de procesador.

se produce [unsupported_os](unsupported-os-class.md) si el Runtime de simultaneidad no admite el sistema operativo.

## <a name="getschedulerid"></a>Getschedulerid (

Devuelve un identificador único que se puede asignar a un programador que implementa la interfaz `IScheduler`.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Valor devuelto

Identificador único de un programador.

### <a name="remarks"></a>Observaciones

Use este método para obtener un identificador para su programador antes de pasar una interfaz `IScheduler` como un parámetro a cualquiera de los métodos que ofrece el Administrador de recursos.

## <a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parámetros

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>

## <a name="interruption_point"></a>interruption_point

Crea un punto de interrupción para la cancelación. Si una cancelación está en curso en el contexto donde se llama a esta función, se producirá una excepción interna que anula la ejecución del trabajo paralelo que se está ejecutando actualmente. Si la cancelación no está en curso, la función no hace nada.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Observaciones

No debe detectar la excepción de cancelación interna producida por la función `interruption_point()`. El tiempo de ejecución detectará y controlará la excepción, y la captura puede hacer que el programa se comporte de forma anómala.

## <a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Devuelve una indicación de si el grupo de tareas que actualmente se está ejecutando alineado en el contexto actual se encuentra en medio de una cancelación activa (o lo estará pronto). Tenga en cuenta que si no hay ningún grupo de tareas que se ejecuta actualmente alineado en el contexto actual, se devolverá `false`.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Valor devuelto

**true** si el grupo de tareas que se está ejecutando actualmente se está cancelando; de lo contrario, **false** .

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [cancelación](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a>make_choice

Construye un bloque de mensajería `choice` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
El tipo de bloque de mensaje del primer origen.

*T2*<br/>
El tipo de bloque de mensaje del segundo origen.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` .

*_Item1*<br/>
El primer origen.

*_Item2*<br/>
El segundo origen.

*_Items*<br/>
Orígenes adicionales.

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="return-value"></a>Valor devuelto

Bloque de mensajes `choice` con dos o más orígenes de entrada.

## <a name="make_greedy_join"></a>make_greedy_join

Construye un bloque de mensajería `greedy multitype_join` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
El tipo de bloque de mensaje del primer origen.

*T2*<br/>
El tipo de bloque de mensaje del segundo origen.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` .

*_Item1*<br/>
El primer origen.

*_Item2*<br/>
El segundo origen.

*_Items*<br/>
Orígenes adicionales.

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="return-value"></a>Valor devuelto

Bloque de mensajes `greedy multitype_join` con dos o más orígenes de entrada.

## <a name="make_join"></a>make_join

Construye un bloque de mensajería `non_greedy multitype_join` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
El tipo de bloque de mensaje del primer origen.

*T2*<br/>
El tipo de bloque de mensaje del segundo origen.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` .

*_Item1*<br/>
El primer origen.

*_Item2*<br/>
El segundo origen.

*_Items*<br/>
Orígenes adicionales.

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="return-value"></a>Valor devuelto

Bloque de mensajes `non_greedy multitype_join` con dos o más orígenes de entrada.

## <a name="make_task"></a>make_task

Un método generador para crear un objeto `task_handle`.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se invocará para ejecutar el trabajo representado por el objeto `task_handle`.

*_Func*<br/>
Función que se invocará para ejecutar el trabajo representado por el objeto `task_handle`. Puede ser un functor lambda, un puntero a una función o cualquier objeto que admita una versión del operador de llamada de función con la firma `void operator()()`.

### <a name="return-value"></a>Valor devuelto

Objeto `task_handle` .

### <a name="remarks"></a>Observaciones

Esta función es útil cuando se necesita crear un objeto de `task_handle` con una expresión lambda, ya que permite crear el objeto sin conocer el tipo true del functor lambda.

## <a name="parallel_buffered_sort"></a>parallel_buffered_sort

Organiza los elementos de un intervalo especificado en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario, en paralelo. Esta función es semánticamente similar a `std::sort` que se trata de una ordenación basada en comparación, inestable, en contexto salvo que necesita espacio adicional `O(n)` y requiere una inicialización predeterminada para los elementos que se ordenan.

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parámetros

*_Random_iterator*<br/>
Tipo de iterador del intervalo de entrada.

*_Allocator*<br/>
El tipo de un C++ asignador de memoria compatible con la biblioteca estándar.

*_Function*<br/>
Tipo del comparador binario.

*_Begin*<br/>
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*_End*<br/>
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar.

*_Alloc*<br/>
Instancia de un asignador de memoria compatible con la C++ biblioteca estándar.

*_Func*<br/>
Objeto de función de predicado definido por el usuario que define el criterio de comparación que debe cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen. Esta función de comparador debe imponer una ordenación débil estricta en los pares de elementos de la secuencia.

*_Chunk_size*<br/>
El tamaño mínimo de un fragmento que se dividirá en dos para la ejecución en paralelo.

### <a name="remarks"></a>Observaciones

Todas las sobrecargas requieren `n * sizeof(T)` espacio adicional, donde `n` es el número de elementos que se van a ordenar y `T` es el tipo de elemento. En la mayoría de los casos, parallel_buffered_sort mostrará una mejora en el rendimiento respecto a [parallel_sort](concurrency-namespace-functions.md)y debe usarlo en parallel_sort si tiene la memoria disponible.

Si no proporciona un comparador binario `std::less` se utiliza como valor predeterminado, lo que requiere que el tipo de elemento proporcione el operador `operator<()`.

Si no proporciona un tipo de asignador o una instancia, se utiliza C++ el asignador de memoria de la biblioteca estándar `std::allocator<T>` para asignar el búfer.

El algoritmo divide el intervalo de entrada en dos fragmentos y divide sucesivamente cada fragmento en dos subfragmentos para su ejecución en paralelo. El argumento opcional `_Chunk_size` se puede usar para indicar al algoritmo que debe administrar fragmentos de tamaño < `_Chunk_size` en serie.

## <a name="parallel_for"></a>parallel_for

`parallel_for` itera sobre un intervalo de índices y ejecuta una función proporcionada por el usuario en cada iteración, en paralelo.

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Parámetros

*_Index_type*<br/>
Tipo del índice que se usa para la iteración.

*_Function*<br/>
El tipo de la función que se ejecutará en cada iteración.

*_Partitioner*<br/>
Tipo del particionador que se usa para particionar el intervalo proporcionado.

*first*<br/>
Primer índice que se va a incluir en la iteración.

*last*<br/>
Índice situado una posición después del último índice que se va a incluir en la iteración.

*_Step*<br/>
Valor por el que se va a pasar al recorrer en iteración `first` a `last`. El paso debe ser positivo. se produce [invalid_argument](../../../standard-library/invalid-argument-class.md) si el paso es menor que 1.

*_Func*<br/>
Función que se va a ejecutar en cada iteración. Puede ser una expresión lambda, un puntero de función o cualquier objeto que admita una versión del operador de llamada de función con la firma `void operator()(_Index_type)`.

*_Part*<br/>
Referencia al objeto de particionador. El argumento puede ser uno de `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`[, `const`Simple_partitioner](simple-partitioner-class.md) [`&` o affinity_partitioner`&` si](affinity-partitioner-class.md) se utiliza un objeto [affinity_partitioner](affinity-partitioner-class.md) , la referencia debe ser una referencia de valor l no const, de modo que el algoritmo pueda almacenar el estado de los bucles futuros que se van a volver a usar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [algoritmos paralelos](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each` aplica una función especificada para cada elemento dentro de un intervalo, en paralelo. Es semánticamente equivalente a la función `for_each` en el espacio de nombres `std`, salvo que la iteración sobre los elementos se realiza en paralelo, y el orden de iteración no está especificado. El argumento `_Func` debe admitir un operador de llamada de función del formulario `operator()(T)` donde el parámetro `T` es el tipo de elemento del contenedor que se recorre en iteración.

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Parámetros

*_Iterator*<br/>
Tipo del iterador que se usa para iterar por el contenedor.

*_Function*<br/>
Tipo de la función que se va a aplicar a cada elemento del intervalo.

*_Partitioner*<br/>
*first*<br/>
Iterador que direcciona la posición del primer elemento que se va a incluir en la iteración paralela.

*last*<br/>
Iterador que direcciona la posición situada una posición después del último elemento que se va a incluir en la iteración paralela.

*_Func*<br/>
Objeto de función definida por el usuario que se aplica a cada elemento del intervalo.

*_Part*<br/>
Referencia al objeto de particionador. El argumento puede ser uno de `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`[, `const`Simple_partitioner](simple-partitioner-class.md) [`&` o affinity_partitioner`&` si](affinity-partitioner-class.md) se utiliza un objeto [affinity_partitioner](affinity-partitioner-class.md) , la referencia debe ser una referencia de valor l no const, de modo que el algoritmo pueda almacenar el estado de los bucles futuros que se van a volver a usar.

### <a name="remarks"></a>Observaciones

[auto_partitioner](auto-partitioner-class.md) se usará para la sobrecarga sin un particionador explícito.

En el caso de los iteradores que no admiten el acceso aleatorio, solo se admite [auto_partitioner](auto-partitioner-class.md) .

Para obtener más información, vea [algoritmos paralelos](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a>parallel_invoke

Ejecuta los objetos de función proporcionados como parámetros en paralelo y se bloquea hasta que han terminado de ejecutarse. Cada objeto de función puede ser una expresión lambda, un puntero a una función o cualquier otro objeto que admite el operador de llamada de función con la signatura `void operator()()`.

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Parámetros

*_Function1*<br/>
Tipo del primer objeto de función que se va a ejecutar en paralelo.

*_Function2*<br/>
Tipo del segundo objeto de función que se va a ejecutar en paralelo.

*_Function3*<br/>
Tipo del tercer objeto de función que se va a ejecutar en paralelo.

*_Function4*<br/>
Tipo del cuarto objeto de función que se va a ejecutar en paralelo.

*_Function5*<br/>
Tipo del quinto objeto de función que se va a ejecutar en paralelo.

*_Function6*<br/>
Tipo del sexto objeto de función que se va a ejecutar en paralelo.

*_Function7*<br/>
Tipo del séptimo objeto de función que se va a ejecutar en paralelo.

*_Function8*<br/>
Tipo del octavo objeto de función que se va a ejecutar en paralelo.

*_Function9*<br/>
Tipo del noveno objeto de función que se va a ejecutar en paralelo.

*_Function10*<br/>
Tipo del décimo objeto de función que se va a ejecutar en paralelo.

*_Func1*<br/>
Primer objeto de función que se va a ejecutar en paralelo.

*_Func2*<br/>
Segundo objeto de función que se va a ejecutar en paralelo.

*_Func3*<br/>
El tercer objeto de función que se va a ejecutar en paralelo.

*_Func4*<br/>
Cuarto objeto de función que se va a ejecutar en paralelo.

*_Func5*<br/>
Quinto objeto de función que se va a ejecutar en paralelo.

*_Func6*<br/>
Sexto objeto de función que se va a ejecutar en paralelo.

*_Func7*<br/>
Séptimo objeto de función que se va a ejecutar en paralelo.

*_Func8*<br/>
Octavo objeto de función que se va a ejecutar en paralelo.

*_Func9*<br/>
Noveno objeto de función que se va a ejecutar en paralelo.

*_Func10*<br/>
Décimo objeto de función que se va a ejecutar en paralelo.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que uno o varios objetos de función proporcionados como parámetros pueden ejecutarse en línea en el contexto de llamada.

Si uno o varios de los objetos de función pasados como parámetros a esta función produce una excepción, el tiempo de ejecución seleccionará una de estas excepciones de su elección y la propagará fuera de la llamada a `parallel_invoke`.

Para obtener más información, vea [algoritmos paralelos](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a>parallel_radixsort

Organiza los elementos en un intervalo especificado en un orden no descendente utilizando un algoritmo de ordenación de base. Esta es una función estable de ordenación que requiere una función de proyección que pueda proyectar elementos que se puedan ordenar en claves como enteros sin signo. Se requiere una inicialización predeterminada para que se ordenen los elementos.

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Parámetros

*_Random_iterator*<br/>
Tipo de iterador del intervalo de entrada.

*_Allocator*<br/>
El tipo de un C++ asignador de memoria compatible con la biblioteca estándar.

*_Function*<br/>
Tipo de la función de proyección.

*_Begin*<br/>
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*_End*<br/>
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar.

*_Alloc*<br/>
Instancia de un asignador de memoria compatible con la C++ biblioteca estándar.

*_Proj_func*<br/>
Objeto de función de proyección definido por el usuario que convierte un elemento en un valor entero.

*_Chunk_size*<br/>
El tamaño mínimo de un fragmento que se dividirá en dos para la ejecución en paralelo.

### <a name="remarks"></a>Observaciones

Todas las sobrecargas requieren `n * sizeof(T)` espacio adicional, donde `n` es el número de elementos que se van a ordenar y `T` es el tipo de elemento. Se requiere un functor de proyección unario con la firma `I _Proj_func(T)` para devolver una clave cuando se proporciona un elemento, donde `T` es el tipo de elemento y `I` es un tipo de entero sin signo.

Si no se proporciona una función de proyección, se usa una función de proyección predeterminada que simplemente devuelve el elemento para los tipos enteros. La función no se compilará si el elemento no es un tipo entero en ausencia de una función de proyección.

Si no proporciona un tipo de asignador o una instancia, se utiliza C++ el asignador de memoria de la biblioteca estándar `std::allocator<T>` para asignar el búfer.

El algoritmo divide el intervalo de entrada en dos fragmentos y divide sucesivamente cada fragmento en dos subfragmentos para su ejecución en paralelo. El argumento opcional `_Chunk_size` se puede usar para indicar al algoritmo que debe administrar fragmentos de tamaño < `_Chunk_size` en serie.

## <a name="parallel_reduce"></a>parallel_reduce

Calcula la suma de todos los elementos en un intervalo especificado mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos de manera similar mediante el uso de una operación binaria determinada distinta de la suma, en paralelo. `parallel_reduce` es semánticamente similar a `std::accumulate`, salvo que requiere que la operación binaria sea asociativa, y requiere un valor de identidad en lugar de un valor inicial.

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Parámetros

*_Forward_iterator*<br/>
Tipo de iterador del intervalo de entrada.

*_Sym_reduce_fun*<br/>
El tipo de la función de reducción simétrica. Debe ser un tipo de función con la firma `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, donde _Reduce_type es igual que el tipo de identidad y el tipo de resultado de la reducción. En el caso de la tercera sobrecarga, debe ser coherente con el tipo de salida de `_Range_reduce_fun`.

*_Reduce_type*<br/>
Tipo al que se reducirá la entrada, que puede ser diferente del tipo de elemento de entrada. El valor devuelto y el valor de identidad tendrán este tipo.

*_Range_reduce_fun*<br/>
El tipo de la función de reducción del intervalo. Debe ser un tipo de función con la firma `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type es igual que el tipo de identidad y el tipo de resultado de la reducción.

*_Begin*<br/>
Iterador de entrada que direcciona el primer elemento del intervalo que se va a reducir.

*_End*<br/>
Iterador de entrada que direcciona el elemento que está una posición más allá del último elemento del intervalo que se va a reducir.

*_Identity*<br/>
El valor de identidad `_Identity` es del mismo tipo que el tipo de resultado de la reducción y también el `value_type` del iterador para la primera y la segunda sobrecarga. En el caso de la tercera sobrecarga, el valor de identidad debe tener el mismo tipo que el tipo de resultado de la reducción, pero puede ser diferente del `value_type` del iterador. Debe tener un valor adecuado para que el operador de reducción de intervalo `_Range_fun`, cuando se aplica a un intervalo de un solo elemento de tipo `value_type` y el valor de identidad, se comporta como una conversión de tipo del valor de tipo `value_type` al tipo de identidad.

*_Sym_fun*<br/>
Función simétrica que se utilizará en el segundo de la reducción. Consulte la sección Comentarios para obtener más información.

*_Range_fun*<br/>
Función que se usará en la primera fase de la reducción. Consulte la sección Comentarios para obtener más información.

### <a name="return-value"></a>Valor devuelto

Resultado de la reducción.

### <a name="remarks"></a>Observaciones

Para realizar una reducción paralela, la función divide el intervalo en fragmentos en función del número de trabajadores disponibles para el programador subyacente. La reducción se produce en dos fases, la primera fase realiza una reducción dentro de cada fragmento y la segunda fase realiza una reducción entre los resultados parciales de cada fragmento.

La primera sobrecarga requiere que el `value_type`del iterador, `T`, sea el mismo que el tipo de valor de identidad, así como el tipo de resultado de reducción. El tipo de elemento T debe proporcionar al operador `T T::operator + (T)` para reducir los elementos de cada fragmento. También se usa el mismo operador en la segunda fase.

La segunda sobrecarga también requiere que el `value_type` del iterador sea el mismo que el tipo de valor de identidad, así como el tipo de resultado de reducción. El operador binario proporcionado `_Sym_fun` se usa en ambas fases de reducción, con el valor de identidad como el valor inicial de la primera fase.

En el caso de la tercera sobrecarga, el tipo de valor de identidad debe ser el mismo que el tipo de resultado de reducción, pero el `value_type` del iterador puede ser diferente de ambos. La función de reducción de intervalo `_Range_fun` se usa en la primera fase con el valor de identidad como el valor inicial, y la función binaria `_Sym_reduce_fun` se aplica a los subprocesos secundarios en la segunda fase.

## <a name="parallel_sort"></a>parallel_sort

Organiza los elementos de un intervalo especificado en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario, en paralelo. Esta función es semánticamente similar a `std::sort` que se trata una ordenación basada en comparación, inestable, en contexto.

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parámetros

*_Random_iterator*<br/>
Tipo de iterador del intervalo de entrada.

*_Function*<br/>
Tipo del functor de comparación binaria.

*_Begin*<br/>
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*_End*<br/>
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar.

*_Func*<br/>
Objeto de función de predicado definido por el usuario que define el criterio de comparación que debe cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen. Esta función de comparador debe imponer una ordenación débil estricta en los pares de elementos de la secuencia.

*_Chunk_size*<br/>
El tamaño mínimo de un fragmento que se dividirá en dos para la ejecución en paralelo.

### <a name="remarks"></a>Observaciones

La primera sobrecarga utiliza el comparador binario `std::less`.

La segunda sobrecarga utiliza el comparador binario proporcionado que debe tener la firma `bool _Func(T, T)` donde `T` es el tipo de los elementos del intervalo de entrada.

El algoritmo divide el intervalo de entrada en dos fragmentos y divide sucesivamente cada fragmento en dos subfragmentos para su ejecución en paralelo. El argumento opcional `_Chunk_size` se puede usar para indicar al algoritmo que debe administrar fragmentos de tamaño < `_Chunk_size` en serie.

## <a name="parallel_transform"></a>parallel_transform

Aplica un objeto especificado de función a cada elemento de un intervalo de origen, o a un par de elementos de dos intervalos de origen, y copia los valores devueltos del objeto de función en un intervalo de destino, en paralelo. Esta función es semánticamente equivalente a `std::transform`.

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Parámetros

*_Input_iterator1*<br/>
Tipo del primer o único iterador de entrada.

*_Output_iterator*<br/>
Tipo del iterador de salida.

*_Unary_operator*<br/>
Tipo del funcr unario que se va a ejecutar en cada elemento del intervalo de entrada.

*_Input_iterator2*<br/>
Tipo del segundo iterador de entrada.

*_Binary_operator*<br/>
El tipo del funcnte binario ejecutado en pares en los elementos de los dos intervalos de origen.

*_Partitioner*<br/>
*first1*<br/>
Iterador de entrada que dirige a la posición del primer elemento del primer o único intervalo de origen en el que se va a operar.

*last1*<br/>
Iterador de entrada que dirige a la posición situada una posición después del último elemento del primer intervalo de origen en el que se va a operar.

*_Result*<br/>
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino.

*_Unary_op*<br/>
Objeto de función unario definido por el usuario que se aplica a cada elemento del intervalo de origen.

*_Part*<br/>
Referencia al objeto de particionador. El argumento puede ser uno de `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`[, `const`Simple_partitioner](simple-partitioner-class.md) [`&` o affinity_partitioner`&` si](affinity-partitioner-class.md) se utiliza un objeto [affinity_partitioner](affinity-partitioner-class.md) , la referencia debe ser una referencia de valor l no const, de modo que el algoritmo pueda almacenar el estado de los bucles futuros que se van a volver a usar.

*first2*<br/>
Iterador de entrada que dirige a la posición del primer elemento del segundo intervalo de origen en el que se va a operar.

*_Binary_op*<br/>
Objeto de función binario definido por el usuario que se aplica en pares, en un orden hacia delante, a los dos intervalos de origen.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino que va a recibir los elementos de salida transformados por el objeto de función.

### <a name="remarks"></a>Observaciones

[auto_partitioner](auto-partitioner-class.md) se usará para las sobrecargas sin un argumento de particionador explícito.

En el caso de los iteradores que no admiten el acceso aleatorio, solo se admite [auto_partitioner](auto-partitioner-class.md) .

Las sobrecargas que toman el argumento `_Unary_op` transforman el intervalo de entrada en el intervalo de salida aplicando el funcr unario a cada elemento del intervalo de entrada. `_Unary_op` debe admitir el operador de llamada de función con la `operator()(T)` de firma, donde `T` es el tipo de valor del intervalo en el que se recorre en iteración.

Las sobrecargas que toman el argumento `_Binary_op` transformar dos intervalos de entrada en el intervalo de salida aplicando el funcnte binario a un elemento del primer intervalo de entrada y un elemento del segundo intervalo de entrada. `_Binary_op` debe admitir el operador de llamada de función con `operator()(T, U)` de firma, donde `T``U` son tipos de valor de los dos iteradores de entrada.

Para obtener más información, vea [algoritmos paralelos](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a>aparecen

Una implementación receive general, que permite a un contexto esperar datos exactamente de un origen y filtrar los valores que se aceptan.

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga.

*_Src*<br/>
Puntero o referencia al origen desde el que se esperan los datos.

*_Timeout*<br/>
Tiempo máximo que el método debe tener para los datos, en milisegundos.

*_Filter_proc*<br/>
Función de filtro que determina si se deben aceptar los mensajes.

### <a name="return-value"></a>Valor devuelto

Un valor del origen del tipo de carga.

### <a name="remarks"></a>Observaciones

Si el parámetro `_Timeout` tiene un valor distinto del `COOPERATIVE_TIMEOUT_INFINITE`constante, se produce la excepción [operation_timed_out](operation-timed-out-class.md) si la cantidad de tiempo especificada expira antes de que se reciba un mensaje. Si desea un tiempo de espera de longitud cero, debe usar la función [try_receive](concurrency-namespace-functions.md) , en lugar de llamar a `receive` con un tiempo de espera de `0` (cero), ya que es más eficaz y no inicia excepciones en los tiempos de espera.

Para obtener más información, vea [funciones de paso de mensajes](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a>run_with_cancellation_token

Ejecuta un objeto de función de forma inmediata y sincrónicamente en el contexto de un token de cancelación dado.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parámetros

*_Function*<br/>
Tipo del objeto de función que se va a invocar.

*_Func*<br/>
Objeto de función que se ejecutará. Este objeto debe admitir el operador de llamada de función con una firma de void (void).

*_Ct*<br/>
Token de cancelación que controlará la cancelación implícita del objeto de función. Use `cancellation_token::none()` si desea que la función se ejecute sin la posibilidad de que se cancele la cancelación implícita de un grupo de tareas primario.

### <a name="remarks"></a>Observaciones

Cualquier punto de interrupción en el objeto de función se desencadenará cuando se cancele el `cancellation_token`. El token explícito `_Ct` aislará este `_Func` de la cancelación primaria si el elemento primario tiene un token diferente o ningún token.

## <a name="send"></a>Enviar

Una operación de envío sincrónica, que espera hasta que el destino acepte o rechace el mensaje.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga.

*_Trg*<br/>
Puntero o referencia al destino al que se envían los datos.

*_Data*<br/>
Referencia a los datos que se van a enviar.

### <a name="return-value"></a>Valor devuelto

**true** si se aceptó el mensaje; en caso contrario, **false** .

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [funciones de paso de mensajes](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parámetros

*_Scheduler*<br/>
Programador de ambiente que se va a establecer.

## <a name="set_task_execution_resources"></a>set_task_execution_resources

Limita los recursos de ejecución que usan los subprocesos de trabajo internos del runtime de simultaneidad para el conjunto de afinidad especificado.

Se puede llamar a este método solamente antes de que el Administrador de recursos se haya creado o entre dos duraciones del Administrador de recursos. Se puede invocar varias veces siempre que el Administrador de recursos no exista en el momento de la invocación. Después de que se haya establecido un límite de afinidad, permanece en vigor hasta la siguiente llamada válida al método `set_task_execution_resources`.

La máscara de afinidad proporcionada no necesita ser un subconjunto de la máscara de afinidad en proceso. La afinidad en proceso se actualizará en caso necesario.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parámetros

*_ProcessAffinityMask*<br/>
Máscara de afinidad a la que se van a restringir los subprocesos de trabajo Runtime de simultaneidad. Use este método en un sistema con más de 64 subprocesos de hardware solo si desea limitar el Runtime de simultaneidad a un subconjunto del grupo de procesadores actual. En general, debe usar la versión del método que acepta una matriz de afinidades de grupo como parámetro, para restringir la afinidad en máquinas con más de 64 subprocesos de hardware.

*count*<br/>
Número de entradas de `GROUP_AFFINITY` en la matriz especificada por el parámetro `_PGroupAffinity`.

*_PGroupAffinity*<br/>
Matriz de entradas de `GROUP_AFFINITY`.

### <a name="remarks"></a>Observaciones

El método producirá una excepción [invalid_operation](invalid-operation-class.md) si un administrador de recursos está presente en el momento en que se invoca y una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si la afinidad especificada da como resultado un conjunto vacío de recursos.

La versión del método que toma una matriz de afinidades de grupo como parámetro solo debe usarse en sistemas operativos con Windows 7 o una versión posterior. De lo contrario, se produce una excepción [invalid_operation](invalid-operation-class.md) .

La modificación mediante programación de la afinidad del proceso después de invocar este método no hará que el Administrador de recursos vuelva a evaluar la afinidad a la que está restringida. Por lo tanto, se deben realizar todos los cambios en la afinidad del proceso antes de llamar a este método.

## <a name="swap"></a> swap

Intercambia los elementos de dos objetos `concurrent_vector`.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de los elementos almacenados en los vectores simultáneos.

*_Ax*<br/>
Tipo de asignador de los vectores simultáneos.

*_A*<br/>
Vector simultáneo cuyos elementos se van a intercambiar con los de los vectores simultáneos `_B`.

*_B*<br/>
Vector simultáneo que proporciona los elementos que se van a intercambiar o el vector cuyos elementos se van a intercambiar con los del vector simultáneo `_A`.

### <a name="remarks"></a>Observaciones

La función de plantilla es un algoritmo especializado en la clase contenedora `concurrent_vector` para ejecutar la función miembro `_A`. [concurrent_vector:: swap](concurrent-vector-class.md#swap)(`_B`). Se trata de instancias de la ordenación parcial de plantillas de función por el compilador. Cuando las funciones de plantilla se sobrecargan de manera que la coincidencia de la plantilla con la llamada de la función no es única, entonces el compilador selecciona la versión más especializada de la función de plantilla. La versión general de la función de plantilla, `template <class T> void swap(T&, T&)`, en la clase de algoritmo funciona mediante asignación y es una operación lenta. La versión especializada de cada contenedor es mucho más rápida, dado que puede funcionar con la representación interna de la clase contenedora.

Este método no es seguro para la simultaneidad. Debe asegurarse de que ningún otro subproceso está realizando operaciones en ninguno de los vectores simultáneos al llamar a este método.

## <a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parámetros

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valor devuelto

## <a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parámetros

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valor devuelto

## <a name="trace_agents_register_name"></a>Trace_agents_register_name

Asocia el nombre dado al bloque o agente de mensajes en el seguimiento ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del objeto. Suele ser un bloque de mensajes o un agente.

*_PObject*<br/>
Puntero al bloque de mensajes o agente al que se llama en el seguimiento.

*_Name*<br/>
Nombre del objeto especificado.

## <a name="try_receive"></a>try_receive

Una implementación try-receive general, que permite a un contexto buscar datos exactamente de un origen y filtrar los valores que se aceptan. Si los datos no están listos, el método devolverá **false**.

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga

*_Src*<br/>
Puntero o referencia al origen desde el que se esperan los datos.

*_value*<br/>
Referencia a una ubicación donde se colocará el resultado.

*_Filter_proc*<br/>
Función de filtro que determina si se deben aceptar los mensajes.

### <a name="return-value"></a>Valor devuelto

Un valor de `bool` que indica si se colocó o no una carga en `_value`.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [funciones de paso de mensajes](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a>currir

Hace una pausa en el contexto actual para un periodo de tiempo indicado.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parámetros

*_Milliseconds*<br/>
Número de milisegundos durante los que se debe pausar el contexto actual. Si el parámetro `_Milliseconds` se establece en el valor `0`, el contexto actual debe producir la ejecución en otros contextos ejecutables antes de continuar.

### <a name="remarks"></a>Observaciones

Si se llama a este método en un contexto de Runtime de simultaneidad Scheduler, el programador encontrará un contexto diferente para ejecutarse en el recurso subyacente. Dado que Scheduler es cooperativo por naturaleza, este contexto no se puede reanudar exactamente después del número de milisegundos especificado. Si el programador está ocupado ejecutando otras tareas que no ceden de forma cooperativa al programador, el período de espera puede ser indefinido.

## <a name="when_all"></a>when_all

Crea una tarea que se completará correctamente cuando todas las tareas proporcionadas como argumentos se completen correctamente.

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Parámetros

*_Iterator*<br/>
El tipo de iterador de entrada.

*_Begin*<br/>
Posición del primer elemento del intervalo de elementos que se va a combinar en la tarea resultante.

*_End*<br/>
Posición del primer elemento que supera el intervalo de elementos que se va a combinar en la tarea resultante.

*_TaskOptions*<br/>
Objeto `task_options`.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando todas las tareas de entrada se han completado correctamente. Si las tareas de entrada son de tipo `T`, el resultado de esta función será `task<std::vector<T>>`. Si las tareas de entrada son del tipo `void`, la tarea de salida también será `task<void>`.

### <a name="remarks"></a>Observaciones

`when_all` es una función sin bloqueo que genera `task` como resultado. A diferencia de [Task:: wait](task-class.md#wait), es seguro llamar a esta función en una aplicación de UWP en el subproceso asta (Application STA).

Si una de las tareas se cancela o produce una excepción, la tarea devuelta finalizará pronto, con el estado cancelado, y la excepción, si se produce, se producirá si llama a [Task:: get](task-class.md#get) o `task::wait` en esa tarea.

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a>when_any

Crea una tarea que se completará correctamente cuando cualquiera de las tareas proporcionadas como argumentos se complete correctamente.

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Parámetros

*_Iterator*<br/>
El tipo de iterador de entrada.

*_Begin*<br/>
Posición del primer elemento del intervalo de elementos que se va a combinar en la tarea resultante.

*_End*<br/>
Posición del primer elemento que supera el intervalo de elementos que se va a combinar en la tarea resultante.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token de cancelación que controla la cancelación de la tarea devuelta. Si no proporciona un token de cancelación, la tarea resultante recibe el token de cancelación de la tarea que hace que se complete.

### <a name="return-value"></a>Valor devuelto

Tarea que se completa correctamente cuando cualquiera de las tareas de entrada se completa correctamente. Si las tareas de entrada son del tipo `T`, el resultado de esta función será un `task<std::pair<T, size_t>>>`, donde el primer elemento del par es el resultado de la tarea que se está completando y el segundo elemento es el índice de la tarea que ha finalizado. Si las tareas de entrada son del tipo `void`, el resultado es un `task<size_t>`, donde el resultado es el índice de la tarea que se está completando.

### <a name="remarks"></a>Observaciones

`when_any` es una función sin bloqueo que genera `task` como resultado. A diferencia de [Task:: wait](task-class.md#wait), es seguro llamar a esta función en una aplicación de UWP en el subproceso asta (Application STA).

Para obtener más información, consulte [paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
