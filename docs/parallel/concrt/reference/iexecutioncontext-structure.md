---
title: IExecutionContext (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecb07238fbe3648c857520cce5658b8d2897ee2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384278"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext (Estructura)

Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.

## <a name="syntax"></a>Sintaxis

```
struct IExecutionContext;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IExecutionContext:: Dispatch](#dispatch)|El método que se llama cuando un proxy del subproceso comienza a ejecutarse un contexto de ejecución determinado. Debe tratarse de la rutina de trabajo principal para el programador.|
|[IExecutionContext::GetId](#getid)|Devuelve un identificador único para el contexto de ejecución.|
|[IExecutionContext::GetProxy](#getproxy)|Devuelve una interfaz para el proxy del subproceso que se está ejecutando en este contexto.|
|[IExecutionContext::GetScheduler](#getscheduler)|Devuelve una interfaz para el programador al que pertenece este contexto de ejecución.|
|[IExecutionContext::SetProxy](#setproxy)|Asocia a un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de que comienza a ejecutarse el contexto `Dispatch` método.|

## <a name="remarks"></a>Comentarios

Si está implementando un programador personalizado que interactúa con el Administrador de recursos del Runtime de simultaneidad, deberá implementar la `IExecutionContext` interfaz. Los subprocesos creados por el Administrador de recursos realizan trabajo en el nombre de su programador ejecutando el `IExecutionContext::Dispatch` método.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionContext`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="dispatch"></a>  IExecutionContext:: Dispatch (método)

El método que se llama cuando un proxy del subproceso comienza a ejecutarse un contexto de ejecución determinado. Debe tratarse de la rutina de trabajo principal para el programador.

```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>Parámetros

*pDispatchState*<br/>
Un puntero al estado en el que está siendo enviado este contexto de ejecución. Para obtener más información sobre el estado de envío, consulte [DispatchState](dispatchstate-structure.md).

##  <a name="getid"></a>  IExecutionContext:: GetId (método)

Devuelve un identificador único para el contexto de ejecución.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador entero único.

### <a name="remarks"></a>Comentarios

Debe usar el método `GetExecutionContextId` para obtener un identificador único para el objeto que implementa el `IExecutionContext` interfaz antes de usar la interfaz como un parámetro a los métodos proporcionados por el Administrador de recursos. Se espera que devuelva el mismo identificador cuando el `GetId` se invoca la función.

Un identificador obtenido de un origen diferente podría provocar un comportamiento indefinido.

##  <a name="getproxy"></a>  GetProxy (método)

Devuelve una interfaz para el proxy del subproceso que se está ejecutando en este contexto.

```
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IThreadProxy`. Si no se ha inicializado el proxy del subproceso del contexto de ejecución con una llamada a `SetProxy`, la función debe devolver `NULL`.

### <a name="remarks"></a>Comentarios

Invocará el Administrador de recursos el `SetProxy` método en un contexto de ejecución, con un `IThreadProxy` interfaz como un parámetro, antes de escribir el `Dispatch` método en la en el contexto. Se espera que almacene este argumento y devolverlo en las llamadas a `GetProxy()`.

##  <a name="getscheduler"></a>  GetScheduler (método)

Devuelve una interfaz para el programador al que pertenece este contexto de ejecución.

```
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz `IScheduler`.

### <a name="remarks"></a>Comentarios

Son necesarios para inicializar el contexto de ejecución con válido `IScheduler` interfaz antes de usarlo como un parámetro a los métodos proporcionados por el Administrador de recursos.

##  <a name="setproxy"></a>  SetProxy (método)

Asocia a un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de que comienza a ejecutarse el contexto `Dispatch` método.

```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>Parámetros

*pThreadProxy*<br/>
Una interfaz para el proxy del subproceso que se va a escribir el `Dispatch` método en este contexto de ejecución.

### <a name="remarks"></a>Comentarios

Se espera que guarde el parámetro `pThreadProxy` y devolverlo en una llamada a la `GetProxy` método. El Administrador de recursos garantiza que el proxy del subproceso asociado al contexto de ejecución no cambiará mientras se está ejecutando el proxy del subproceso del `Dispatch` método.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)
