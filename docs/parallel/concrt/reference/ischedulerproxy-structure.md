---
title: ISchedulerProxy (estructura)
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 776f70f9b93eb2e38151ceb5e84b4664420cf954
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424846"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy (estructura)

La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ISchedulerProxy:: Bindcontext (](#bindcontext)|Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.|
|[ISchedulerProxy:: Createoversubscriber (](#createoversubscriber)|Crea una nueva raíz del procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.|
|[ISchedulerProxy:: Requestinitialvirtualprocessors (](#requestinitialvirtualprocessors)|Solicita una asignación inicial de raíces del procesador virtual. Cada raíz del procesador virtual representa la capacidad de ejecutar un subproceso que puede realizar el trabajo para el programador.|
|[ISchedulerProxy:: Shutdown](#shutdown)|Notifica a la Administrador de recursos que el programador se está cerrando. Esto hará que el Administrador de recursos recupere inmediatamente todos los recursos concedidos al programador.|
|[ISchedulerProxy:: Subscribecurrentthread (](#subscribecurrentthread)|Registra el subproceso actual con el Administrador de recursos, asociándolo a este programador.|
|[ISchedulerProxy:: Unbindcontext (](#unbindcontext)|Desasocia un proxy del subproceso del contexto de ejecución especificado por el parámetro `pContext` y lo devuelve al grupo libre del generador de proxy del subproceso. Solo se puede llamar a este método en un contexto de ejecución que se ha enlazado a través del método [ISchedulerProxy:: bindcontext (](#bindcontext) y que aún no se ha iniciado a través de la `pContext` parámetro de una llamada al método [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) .|

## <a name="remarks"></a>Observaciones

El Administrador de recursos una interfaz de `ISchedulerProxy` a todos los programadors que se registran con él mediante el método [IResourceManager:: RegisterScheduler (](iresourcemanager-structure.md#registerscheduler) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISchedulerProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="bindcontext"></a>ISchedulerProxy:: Bindcontext ((método)

Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Interfaz al contexto de ejecución que se va a asociar a un proxy del subproceso.

### <a name="remarks"></a>Observaciones

Normalmente, el método [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) enlazará un proxy del subproceso a un contexto de ejecución a petición. Sin embargo, hay circunstancias en las que es necesario enlazar un contexto de antemano para asegurarse de que el método de `SwitchTo` cambie a un contexto ya enlazado. Este es el caso en un contexto de programación UMS, ya que no puede llamar a métodos que asignan memoria, y el enlace de un proxy del subproceso puede implicar la asignación de memoria si un proxy del subproceso no está disponible en el grupo gratuito del generador de proxy del subproceso.

`invalid_argument` se produce si el parámetro `pContext` tiene el valor `NULL`.

## <a name="createoversubscriber"></a>ISchedulerProxy:: Createoversubscriber ((método)

Crea una nueva raíz del procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parámetros

*pExecutionResource*<br/>
Interfaz `IExecutionResource` que representa el subproceso de hardware al que se desea suscribir.

### <a name="return-value"></a>Valor devuelto

Interfaz `IVirtualProcessorRoot`.

### <a name="remarks"></a>Observaciones

Use este método cuando el programador desee sobrescribir un subproceso de hardware determinado durante un período de tiempo limitado. Una vez que haya terminado con la raíz del procesador virtual, debe devolverla al administrador de recursos mediante una llamada al método [Remove](iexecutionresource-structure.md#remove) en la interfaz `IVirtualProcessorRoot`.

Incluso puede sobrescribir una raíz del procesador virtual existente, porque la interfaz de `IVirtualProcessorRoot` hereda de la interfaz `IExecutionResource`.

## <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: Requestinitialvirtualprocessors ((método)

Solicita una asignación inicial de raíces del procesador virtual. Cada raíz del procesador virtual representa la capacidad de ejecutar un subproceso que puede realizar el trabajo para el programador.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parámetros

*doSubscribeCurrentThread*<br/>
Si se va a suscribir el subproceso y la cuenta actuales durante la asignación de recursos.

### <a name="return-value"></a>Valor devuelto

La interfaz de `IExecutionResource` para el subproceso actual, si el parámetro `doSubscribeCurrentThread` tiene el valor **true**. Si el valor es **false**, el método devuelve NULL.

### <a name="remarks"></a>Observaciones

Antes de que un programador ejecute cualquier trabajo, debe utilizar este método para solicitar las raíces del procesador virtual desde el Administrador de recursos. El Administrador de recursos tendrá acceso a la Directiva del programador mediante [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) y usará los valores de las claves de directiva `MinConcurrency`, `MaxConcurrency` y `TargetOversubscriptionFactor` para determinar cuántos subprocesos de hardware asignar al programador inicialmente y el número de raíces del procesador virtual que se van a crear para cada subproceso de hardware. Para obtener más información sobre cómo se usan las directivas de Scheduler para determinar la asignación inicial de un programador, vea [policyelementkey (](concurrency-namespace-enums.md).

El Administrador de recursos concede recursos a un programador llamando al método [IScheduler:: addvirtualprocessors (](ischeduler-structure.md#addvirtualprocessors) con una lista de raíces del procesador virtual. El método se invoca como una devolución de llamada en el programador antes de que este método devuelva.

Si el programador solicitó la suscripción para el subproceso actual estableciendo el parámetro `doSubscribeCurrentThread` en **true**, el método devuelve una interfaz de `IExecutionResource`. La suscripción debe finalizar en un punto posterior mediante el método [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) .

Al determinar qué subprocesos de hardware están seleccionados, el Administrador de recursos intentará optimizar la afinidad del nodo de procesador. Si se solicita una suscripción para el subproceso actual, es una indicación de que el subproceso actual intenta participar en el trabajo asignado a este programador. En tal caso, las raíces de los procesadores virtuales asignados se encuentran en el nodo del procesador en el que se está ejecutando el subproceso actual, si es posible.

La acción de suscribir un subproceso aumenta en uno el nivel de suscripción del subproceso de hardware subyacente. El nivel de suscripción se reduce en uno cuando se termina la suscripción. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="shutdown"></a>ISchedulerProxy:: Shutdown (método)

Notifica a la Administrador de recursos que el programador se está cerrando. Esto hará que el Administrador de recursos recupere inmediatamente todos los recursos concedidos al programador.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Observaciones

Todas las interfaces `IExecutionContext` el programador recibido como resultado de la suscripción de un subproceso externo mediante los métodos `ISchedulerProxy::RequestInitialVirtualProcessors` o `ISchedulerProxy::SubscribeCurrentThread` deben devolverse al Administrador de recursos usando `IExecutionResource::Remove` antes de que un programador se cierre.

Si el programador tuviera alguna raíz de procesador virtual desactivada, debe activarla mediante [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)y hacer que los proxies del subproceso que se ejecutan en ellas dejen el método `Dispatch` de los contextos de ejecución que se envían antes de invocar `Shutdown` en un proxy del programador.

No es necesario que el programador devuelva individualmente todas las raíces del procesador virtual que Administrador de recursos le concedan a través de llamadas al método de `Remove` porque todas las raíces de los procesadores virtuales se devolverán al Administrador de recursos al cerrarse.

## <a name="subscribecurrentthread"></a>ISchedulerProxy:: Subscribecurrentthread ((método)

Registra el subproceso actual con el Administrador de recursos, asociándolo a este programador.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Valor devuelto

La interfaz de `IExecutionResource` que representa el subproceso actual en tiempo de ejecución.

### <a name="remarks"></a>Observaciones

Use este método si desea que la Administrador de recursos tenga en cuenta el subproceso actual mientras asigna recursos al programador y a otros programadores. Es especialmente útil cuando el subproceso planea participar en el trabajo en cola en el programador, junto con las raíces del procesador virtual que el programador recibe del Administrador de recursos. El Administrador de recursos usa información para evitar la sobresuscripción innecesaria de subprocesos de hardware en el sistema.

El recurso de ejecución recibido a través de este método debe devolverse al Administrador de recursos mediante el método [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) . El subproceso que llama al método `Remove` debe ser el mismo subproceso que anteriormente llamó al método `SubscribeCurrentThread`.

La acción de suscribir un subproceso aumenta en uno el nivel de suscripción del subproceso de hardware subyacente. El nivel de suscripción se reduce en uno cuando se termina la suscripción. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="unbindcontext"></a>ISchedulerProxy:: Unbindcontext ((método)

Desasocia un proxy del subproceso del contexto de ejecución especificado por el parámetro `pContext` y lo devuelve al grupo libre del generador de proxy del subproceso. Solo se puede llamar a este método en un contexto de ejecución que se ha enlazado a través del método [ISchedulerProxy:: bindcontext (](#bindcontext) y que aún no se ha iniciado a través de la `pContext` parámetro de una llamada al método [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) .

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Contexto de ejecución que se va a desasociar del proxy del subproceso.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager (estructura)](iresourcemanager-structure.md)
