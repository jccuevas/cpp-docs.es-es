---
title: task_options (Clase) (Runtime de simultaneidad)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: e79dd7979b587ae807c8984a04b79be362b03758
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368606"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options (Clase) (Runtime de simultaneidad)

Representa las opciones permitidas para crear una tarea

## <a name="syntax"></a>Sintaxis

```cpp
class task_options;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_options::task_options (Constructor) (Runtime de simultaneidad)](#ctor)|Sobrecargado. Lista predeterminada de opciones de creación de tareas|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[task_options::get_cancellation_token (Método) (Runtime de simultaneidad)](#get_cancellation_token)|Devuelve el token de cancelación|
|[task_options::get_continuation_context (Método) (Runtime de simultaneidad)](#get_continuation_context)|Devuelve el contexto de continuación|
|[task_options::get_scheduler (Método) (Runtime de simultaneidad)](#get_scheduler)|Devuelve el programador|
|[task_options::has_cancellation_token (Método) (Runtime de simultaneidad)](#has_cancellation_token)|Indica si el usuario especificó un token de cancelación|
|[task_options::has_scheduler (Método) (Runtime de simultaneidad)](#has_scheduler)|Indica si el usuario especificó un programador n|
|[task_options::set_cancellation_token (Método) (Runtime de simultaneidad)](#set_cancellation_token)|Establece el token determinado en las opciones|
|[task_options::set_continuation_context (Método) (Runtime de simultaneidad)](#set_continuation_context)|Establece el contexto de continuación determinado en las opciones|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_options`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

## <a name="task_optionsget_cancellation_token-method-concurrency-runtime"></a><a name="get_cancellation_token"></a>método task_options::get_cancellation_token (Runtime de simultaneidad)

Devuelve el token de cancelación

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="task_optionsget_continuation_context-method-concurrency-runtime"></a><a name="get_continuation_context"></a>método task_options::get_continuation_context (Runtime de simultaneidad)

Devuelve el contexto de continuación

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="task_optionsget_scheduler-method-concurrency-runtime"></a><a name="get_scheduler"></a>método task_options::get_scheduler (Runtime de simultaneidad)

Devuelve el programador

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="task_optionshas_cancellation_token-method-concurrency-runtime"></a><a name="has_cancellation_token"></a>método task_options::has_cancellation_token (Runtime de simultaneidad)

Indica si el usuario especificó un token de cancelación

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="task_optionshas_scheduler-method-concurrency-runtime"></a><a name="has_scheduler"></a>método task_options::has_scheduler (Runtime de simultaneidad)

Indica si el usuario especificó un programador n

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

## <a name="task_optionsset_cancellation_token-method-concurrency-runtime"></a><a name="set_cancellation_token"></a>Método task_options::set_cancellation_token (Runtime de simultaneidad)

Establece el token determinado en las opciones

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parámetros

`_Token`

## <a name="task_optionsset_continuation_context-method-concurrency-runtime"></a><a name="set_continuation_context"></a>task_options::set_continuation_context (Método) (Runtime de simultaneidad)

Establece el contexto de continuación determinado en las opciones

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parámetros

`_ContinuationContext`

## <a name="task_optionstask_options-constructor-concurrency-runtime"></a><a name="ctor"></a>Constructor task_options::task_options (runtime de simultaneidad)

Lista predeterminada de opciones de creación de tareas

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Parámetros

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
