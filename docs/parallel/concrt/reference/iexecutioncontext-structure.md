---
title: IExecutionContext (Estructura)
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
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358804"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext (Estructura)

Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.

## <a name="syntax"></a>Sintaxis

```cpp
struct IExecutionContext;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IExecutionContext::Dispatch](#dispatch)|Método al que se llama cuando un proxy de subproceso comienza a ejecutar un contexto de ejecución determinado. Esta debe ser la rutina de trabajo principal para el programador.|
|[IExecutionContext::GetId](#getid)|Devuelve un identificador único para el contexto de ejecución.|
|[IExecutionContext::GetProxy](#getproxy)|Devuelve una interfaz al proxy de subproceso que está ejecutando este contexto.|
|[IExecutionContext::GetScheduler](#getscheduler)|Devuelve una interfaz al programador al que pertenece este contexto de ejecución.|
|[IExecutionContext::SetProxy](#setproxy)|Asocia un proxy de subproceso con este contexto de ejecución. El proxy de subproceso asociado invoca este método justo `Dispatch` antes de que comience a ejecutar el método del contexto.|

## <a name="remarks"></a>Observaciones

Si va a implementar un programador personalizado que interactúa con el Administrador de `IExecutionContext` recursos del Runtime de simultaneidad, deberá implementar la interfaz. Los subprocesos creados por Resource Manager realizan el `IExecutionContext::Dispatch` trabajo en nombre del programador ejecutando el método.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionContext`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>IExecutionContext::Dispatch Método

Método al que se llama cuando un proxy de subproceso comienza a ejecutar un contexto de ejecución determinado. Esta debe ser la rutina de trabajo principal para el programador.

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatchState*<br/>
Puntero al estado en el que se distribuye este contexto de ejecución. Para obtener más información sobre el estado de envío, vea [DispatchState](dispatchstate-structure.md).

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>IExecutionContext::GetId Método

Devuelve un identificador único para el contexto de ejecución.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

### <a name="remarks"></a>Observaciones

Debe usar el `GetExecutionContextId` método para obtener un identificador único `IExecutionContext` para el objeto que implementa la interfaz, antes de usar la interfaz como parámetro para los métodos proporcionados por Resource Manager. Se espera que devuelva el `GetId` mismo identificador cuando se invoca la función.

Un identificador obtenido de un origen diferente podría dar lugar a un comportamiento indefinido.

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>IExecutionContext::GetProxy Método

Devuelve una interfaz al proxy de subproceso que está ejecutando este contexto.

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IThreadProxy`. Si el proxy de subproceso del contexto de ejecución `SetProxy`no se `NULL`ha inicializado con una llamada a , la función debe devolver .

### <a name="remarks"></a>Observaciones

Resource Manager invocará `SetProxy` el método en un `IThreadProxy` contexto de ejecución, con `Dispatch` una interfaz como parámetro, antes de escribir el método en el contexto. Se espera que almacene este argumento y `GetProxy()`lo devuelva en llamadas a .

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>IExecutionContext::GetScheduler Método

Devuelve una interfaz al programador al que pertenece este contexto de ejecución.

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IScheduler`.

### <a name="remarks"></a>Observaciones

Debe inicializar el contexto de ejecución `IScheduler` con una interfaz válida antes de utilizarlo como parámetro para los métodos proporcionados por Resource Manager.

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>IExecutionContext::SetProxy Método

Asocia un proxy de subproceso con este contexto de ejecución. El proxy de subproceso asociado invoca este método justo `Dispatch` antes de que comience a ejecutar el método del contexto.

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parámetros

*pThreadProxy*<br/>
Interfaz para el proxy de subproceso `Dispatch` que está a punto de escribir el método en este contexto de ejecución.

### <a name="remarks"></a>Observaciones

Se espera que guarde `pThreadProxy` el parámetro y lo `GetProxy` devuelva en una llamada al método. Resource Manager garantiza que el proxy de subproceso asociado al contexto de ejecución `Dispatch` no cambiará mientras el proxy de subproceso está ejecutando el método.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)
