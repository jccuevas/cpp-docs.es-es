---
title: task_options (Clase) (Runtime de simultaneidad)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: c832ce759c556765fa412b2ef77333bc6612b8c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407879"
---
# <a name="taskoptions-class-concurrency-runtime"></a>task_options (Clase) (Runtime de simultaneidad)

Representa las opciones permitidas para crear una tarea

## <a name="syntax"></a>Sintaxis

```
class task_options;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[task_options::task_options Constructor (Runtime de simultaneidad)](#ctor)|Sobrecargado. Lista predeterminada de opciones de creación de tareas|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[task_options::get_cancellation_token (método) (Runtime de simultaneidad)](#get_cancellation_token)|Devuelve el token de cancelación|
|[task_options::get_continuation_context (método) (Runtime de simultaneidad)](#get_continuation_context)|Devuelve el contexto de continuación|
|[task_options::get_scheduler (método) (Runtime de simultaneidad)](#get_scheduler)|Devuelve el programador|
|[task_options::has_cancellation_token (método) (Runtime de simultaneidad)](#has_cancellation_token)|Indica si el usuario especificó un token de cancelación|
|[task_options::has_scheduler (método) (Runtime de simultaneidad)](#has_scheduler)|Indica si el usuario especificó un programador n|
|[task_options::set_cancellation_token (método) (Runtime de simultaneidad)](#set_cancellation_token)|Establece el token determinado en las opciones|
|[task_options::set_continuation_context (método) (Runtime de simultaneidad)](#set_continuation_context)|Establece el contexto de continuación determinado en las opciones|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`task_options`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

##  <a name="get_cancellation_token"></a>  task_options::get_cancellation_token (método) (Runtime de simultaneidad)

Devuelve el token de cancelación

```
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="get_continuation_context"></a>  task_options::get_continuation_context (método) (Runtime de simultaneidad)

Devuelve el contexto de continuación

```
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="get_scheduler"></a>  task_options::get_scheduler (método) (Runtime de simultaneidad)

Devuelve el programador

```
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="has_cancellation_token"></a>  task_options::has_cancellation_token (método) (Runtime de simultaneidad)

Indica si el usuario especificó un token de cancelación

```
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="has_scheduler"></a>  task_options::has_scheduler (método) (Runtime de simultaneidad)

Indica si el usuario especificó un programador n

```
bool has_scheduler() const;
```

### <a name="return-value"></a>Valor devuelto

##  <a name="set_cancellation_token"></a>  task_options::set_cancellation_token (método) (Runtime de simultaneidad)

Establece el token determinado en las opciones

```
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parámetros

`_Token`

##  <a name="set_continuation_context"></a>  task_options::set_continuation_context (método) (Runtime de simultaneidad)

Establece el contexto de continuación determinado en las opciones

```
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parámetros

`_ContinuationContext`

##  <a name="ctor"></a>  task_options::task_options Constructor (Runtime de simultaneidad)

Lista predeterminada de opciones de creación de tareas

```
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

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
