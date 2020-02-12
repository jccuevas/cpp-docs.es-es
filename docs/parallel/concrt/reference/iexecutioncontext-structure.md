---
title: IExecutionContext (estructura)
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 45d65a5e16121d39233c3ceb801933aa1f5a5f8e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138911"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext (estructura)

Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.

## <a name="syntax"></a>Sintaxis

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IExecutionContext::D ispatch](#dispatch)|Método al que se llama cuando un proxy del subproceso empieza a ejecutar un contexto de ejecución determinado. Debe ser la rutina principal de trabajo del programador.|
|[IExecutionContext:: GetId](#getid)|Devuelve un identificador único para el contexto de ejecución.|
|[IExecutionContext:: Getproxy (](#getproxy)|Devuelve una interfaz al proxy del subproceso que está ejecutando este contexto.|
|[IExecutionContext:: Getscheduler (](#getscheduler)|Devuelve una interfaz al programador al que pertenece este contexto de ejecución.|
|[IExecutionContext:: SetProxy](#setproxy)|Asocia un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de empezar a ejecutar el método `Dispatch` del contexto.|

## <a name="remarks"></a>Observaciones

Si va a implementar un programador personalizado que interactúa con el Administrador de recursos del Runtime de simultaneidad, deberá implementar la interfaz de `IExecutionContext`. Los subprocesos creados por el Administrador de recursos realizar el trabajo en nombre del programador ejecutando el método `IExecutionContext::Dispatch`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionContext`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="dispatch"></a>IExecutionContext::D método ispatch

Método al que se llama cuando un proxy del subproceso empieza a ejecutar un contexto de ejecución determinado. Debe ser la rutina principal de trabajo del programador.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatchState*<br/>
Puntero al estado en el que se envía este contexto de ejecución. Para obtener más información sobre el estado de envío, vea [dispatchstate (](dispatchstate-structure.md).

## <a name="getid"></a>IExecutionContext:: GetId (método)

Devuelve un identificador único para el contexto de ejecución.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

### <a name="remarks"></a>Observaciones

Debe utilizar el método `GetExecutionContextId` para obtener un identificador único para el objeto que implementa la interfaz de `IExecutionContext`, antes de utilizar la interfaz como parámetro para los métodos proporcionados por la Administrador de recursos. Se espera que devuelva el mismo identificador cuando se invoca la función `GetId`.

Un identificador Obtenido de un origen diferente podría producir un comportamiento indefinido.

## <a name="getproxy"></a>IExecutionContext:: Getproxy ((método)

Devuelve una interfaz al proxy del subproceso que está ejecutando este contexto.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IThreadProxy`. Si el proxy del subproceso del contexto de ejecución no se ha inicializado con una llamada a `SetProxy`, la función debe devolver `NULL`.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invocará el método `SetProxy` en un contexto de ejecución, con una interfaz `IThreadProxy` como parámetro, antes de escribir el método `Dispatch` en en el contexto. Se espera que almacene este argumento y lo devuelva en las llamadas a `GetProxy()`.

## <a name="getscheduler"></a>IExecutionContext:: Getscheduler ((método)

Devuelve una interfaz al programador al que pertenece este contexto de ejecución.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IScheduler`.

### <a name="remarks"></a>Observaciones

Es necesario inicializar el contexto de ejecución con una interfaz de `IScheduler` válida antes de usarla como parámetro para los métodos proporcionados por la Administrador de recursos.

## <a name="setproxy"></a>IExecutionContext:: SetProxy (método)

Asocia un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de empezar a ejecutar el método `Dispatch` del contexto.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parámetros

*pThreadProxy*<br/>
Una interfaz al proxy del subproceso que está a punto de especificar el método de `Dispatch` en este contexto de ejecución.

### <a name="remarks"></a>Observaciones

Se espera que guarde el parámetro `pThreadProxy` y lo devuelva en una llamada al método `GetProxy`. La Administrador de recursos garantiza que el proxy del subproceso asociado al contexto de ejecución no cambiará mientras el proxy del subproceso esté ejecutando el método `Dispatch`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)
