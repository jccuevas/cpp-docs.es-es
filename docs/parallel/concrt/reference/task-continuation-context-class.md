---
title: task_continuation_context (Clase)
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: 5d7d92fcd1bb00513b9e05030afa56726e87183b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280297"
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context (Clase)

La clase `task_continuation_context` permite especificar dónde se desea que se ejecute una continuación. Sólo es útil utilizar esta clase desde una aplicación de Windows en tiempo de ejecución. Para las aplicaciones en tiempo de ejecución que no son de Windows, el contexto de ejecución de la continuación tarea es determinado por el tiempo de ejecución y no es configurable.

## <a name="syntax"></a>Sintaxis

```
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto actual del subproceso de winrt.|
|[use_arbitrary](#use_arbitrary)|Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el tiempo de ejecución.|
|[use_current](#use_current)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.|
|[use_default](#use_default)|Crea el contexto de continuación de tarea predeterminado.|
|[use_synchronous_execution](#use_synchronous_execution)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónica.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Requisitos

**Encabezado:** ppltasks.h

**Espacio de nombres:** simultaneidad

## <a name="get_current_winrt_context"></a> get_current_winrt_context

Devuelve un objeto de contexto de continuación de tarea que representa el contexto actual del subproceso de WinRT.

## <a name="syntax"></a>Sintaxis

```
static task_continuation_context get_current_winrt_context();
```

## <a name="return-value"></a>Valor devuelto

El contexto del subproceso actual en tiempo de ejecución de Windows. Devuelve un task_continuation_context vacío si se llama desde un contexto en tiempo de ejecución que no son de Windows.

## <a name="remarks"></a>Comentarios

El `get_current_winrt_context` método captura el contexto del subproceso del llamador en tiempo de ejecución de Windows. Devuelve un contexto vacío para los llamadores en tiempo de ejecución que no son de Windows.

El valor devuelto por `get_current_winrt_context` puede utilizarse para indicar al tiempo de ejecución que la continuación debe ejecutarse en el modelo de apartamento del contexto capturado (STA frente a STA), independientemente de si la tarea antecedente es el reconocimiento de apartamento. El reconocimiento de tarea es una tarea que desajusta un tiempo de ejecución de Windows de un apartamento `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea.

Este método es similar a la `use_current` método, pero también está disponible para código C++ nativo sin C++ / c++ / compatibilidad con las extensiones CX. Está destinado a usuarios avanzados usando escribir C + + / código de biblioteca independiente CX nativos y los autores de llamadas en tiempo de ejecución de Windows. A menos que necesite esta funcionalidad, se recomienda la `use_current` método, que solo está disponible para C + + / clientes CX.

##  <a name="use_arbitrary"></a> use_arbitrary

Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el tiempo de ejecución.

```
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Valor devuelto

Un contexto de continuación de tarea que representa una ubicación arbitraria.

### <a name="remarks"></a>Comentarios

Cuando se usa en este contexto de continuación de la continuación se ejecutará en un contexto que el runtime elige incluso si la tarea antecedente es el reconocimiento de apartamento.

`use_arbitrary` se puede usar para desactivar el comportamiento predeterminado para una continuación en una tarea que reconoce apartamento creada en un STA.

Este método solo está disponible para las aplicaciones de Windows en tiempo de ejecución.

##  <a name="use_current"></a> use_current

Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.

```
static task_continuation_context use_current();
```

### <a name="return-value"></a>Valor devuelto

Contexto de ejecución actual.

### <a name="remarks"></a>Comentarios

Este método captura el contexto del llamador en tiempo de ejecución de Windows para que las continuaciones se pueden ejecutar en el apartamento correcto.

El valor devuelto por `use_current` puede utilizarse para indicar al tiempo de ejecución que la continuación debe ejecutarse en el contexto capturado (STA frente a STA), independientemente de si es o no la tarea antecedente reconoce el apartamento. El reconocimiento de tarea es una tarea que desajusta un tiempo de ejecución de Windows de un apartamento `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea.

Este método solo está disponible para las aplicaciones de Windows en tiempo de ejecución.

##  <a name="use_default"></a> use_default

Crea el contexto de continuación de tarea predeterminado.

```
static task_continuation_context use_default();
```

### <a name="return-value"></a>Valor devuelto

El contexto de continuación de forma predeterminada.

### <a name="remarks"></a>Comentarios

Se usa el contexto predeterminado si no especifica un contexto de continuación cuando se llama a la `then` método. En las aplicaciones de Windows para Windows 7 y, a continuación, así como aplicaciones de escritorio en Windows 8 y versiones posteriores, el tiempo de ejecución determina dónde se ejecutarán las continuaciones de tareas. Sin embargo, en una aplicación de Windows en tiempo de ejecución, el contexto de continuación predeterminado para una continuación en una tarea que reconoce apartamento es el contenedor donde `then` se invoca.

El reconocimiento de tarea es una tarea que desajusta un tiempo de ejecución de Windows de un apartamento `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea. Por lo tanto, si programa una continuación en una tarea consciente de apartamento en un STA de Windows en tiempo de ejecución, la continuación se ejecutará en ese STA.

Una continuación en una tarea tenga en cuenta que no sean apartamento se ejecutará en un contexto que se elige el tiempo de ejecución.

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution

Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónica.

## <a name="syntax"></a>Sintaxis

```
static task_continuation_context use_synchronous_execution();
```

## <a name="return-value"></a>Valor devuelto

El contexto de ejecución sincrónica.

## <a name="remarks"></a>Comentarios

El `use_synchronous_execution` método obliga a la tarea de continuación para ejecutar de forma sincrónica en el contexto, provocando la finalización de su tarea antecedente.

Si ya se ha completado la tarea antecedente cuando se adjunta la continuación, la continuación se ejecuta de forma sincrónica en el contexto que se adjunta la continuación.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
