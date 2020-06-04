---
title: ISchedulerProxy (Estructura)
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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368156"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy (Estructura)

La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Asocia un contexto de ejecución con un proxy de subproceso, si aún no está asociado a uno.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Crea una nueva raíz de procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad de ejecutar un subproceso que puede realizar el trabajo para el programador.|
|[ISchedulerProxy::Shutdown](#shutdown)|Notifica al Administrador de recursos que el programador se está cerrando. Esto hará que Resource Manager reclame inmediatamente todos los recursos concedidos al programador.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Registra el subproceso actual con Resource Manager, asociándolo a este programador.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Desasocia un proxy de subproceso del `pContext` contexto de ejecución especificado por el parámetro y lo devuelve al grupo libre del generador de proxy de subprocesos. Este método solo se puede llamar en un contexto de ejecución que se enlaza a través `pContext` de la [ISchedulerProxy::BindContext](#bindcontext) método y aún no se ha iniciado a través de ser el parámetro de un [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) llamada al método.|

## <a name="remarks"></a>Observaciones

Resource Manager entrega `ISchedulerProxy` una interfaz a cada programador que se registra con ella mediante el [método IResourceManager::RegisterScheduler.](iresourcemanager-structure.md#registerscheduler)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISchedulerProxy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy::BindContext Método

Asocia un contexto de ejecución con un proxy de subproceso, si aún no está asociado a uno.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Interfaz al contexto de ejecución que se va a asociar a un proxy de subproceso.

### <a name="remarks"></a>Observaciones

Normalmente, el [método IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) enlazará un proxy de subproceso a un contexto de ejecución a petición. Sin embargo, existen circunstancias en las que es necesario `SwitchTo` enlazar un contexto de antemano para asegurarse de que el método cambia a un contexto ya enlazado. Este es el caso en un contexto de programación de UMS, ya que no puede llamar a métodos que asignan memoria y el enlace de un proxy de subproceso puede implicar la asignación de memoria si un proxy de subproceso no está disponible fácilmente en el grupo libre del generador de proxy de subprocesos.

`invalid_argument`se produce si `pContext` el parámetro `NULL`tiene el valor .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>Método ISchedulerProxy::CreateOversubscriber

Crea una nueva raíz de procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parámetros

*pExecutionResource*<br/>
Interfaz `IExecutionResource` que representa el subproceso de hardware que desea sobresuscribir.

### <a name="return-value"></a>Valor devuelto

Interfaz `IVirtualProcessorRoot`.

### <a name="remarks"></a>Observaciones

Utilice este método cuando el programador desee sobresuscribir un subproceso de hardware determinado durante un período de tiempo limitado. Una vez que haya terminado con la raíz del procesador virtual, debe `IVirtualProcessorRoot` devolverla al administrador de recursos llamando al método [Remove](iexecutionresource-structure.md#remove) en la interfaz.

Incluso puede sobresuscribir una raíz de `IVirtualProcessorRoot` procesador virtual existente, porque la interfaz hereda de la `IExecutionResource` interfaz.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>Método ISchedulerProxy::RequestInitialVirtualProcessors

Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad de ejecutar un subproceso que puede realizar el trabajo para el programador.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parámetros

*doSubscribeCurrentThread*<br/>
Si desea suscribirse al subproceso actual y tener en cuenta durante la asignación de recursos.

### <a name="return-value"></a>Valor devuelto

La `IExecutionResource` interfaz para el subproceso `doSubscribeCurrentThread` actual, si el parámetro tiene el valor **true**. Si el valor es **false**, el método devuelve NULL.

### <a name="remarks"></a>Observaciones

Antes de que un programador ejecute cualquier trabajo, debe usar este método para solicitar raíces de procesador virtual desde Resource Manager. Resource Manager tendrá acceso a la directiva del programador mediante [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) y usará los valores de las claves `MinConcurrency`de directiva `MaxConcurrency` y `TargetOversubscriptionFactor` para determinar cuántos subprocesos de hardware se asignarán al programador inicialmente y cuántas raíces de procesador virtual se crearán para cada subproceso de hardware. Para obtener más información sobre cómo se usan las directivas del programador para determinar la asignación inicial de un programador, vea [PolicyElementKey](concurrency-namespace-enums.md).

Resource Manager concede recursos a un programador llamando al método [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) con una lista de raíces de procesador virtual. El método se invoca como una devolución de llamada en el programador antes de que se devuelva este método.

Si el programador solicitó la suscripción `doSubscribeCurrentThread` para el subproceso `IExecutionResource` actual estableciendo el parámetro en **true**, el método devuelve una interfaz. La suscripción debe terminarse en un momento posterior mediante el método [IExecutionResource::Remove.](iexecutionresource-structure.md#remove)

Al determinar qué subprocesos de hardware se seleccionan, Resource Manager intentará optimizar la afinidad de nodos de procesador. Si se solicita una suscripción para el subproceso actual, es una indicación de que el subproceso actual tiene la intención de participar en el trabajo asignado a este programador. En tal caso, las raíces de procesadores virtuales asignados se encuentran en el nodo de procesador en el que se ejecuta el subproceso actual, si es posible.

El acto de suscribirse a un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente en uno. El nivel de suscripción se reduce en uno cuando se termina la suscripción. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy::Shutdown Método

Notifica al Administrador de recursos que el programador se está cerrando. Esto hará que Resource Manager reclame inmediatamente todos los recursos concedidos al programador.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Observaciones

Todas `IExecutionContext` las interfaces que el programador recibió como resultado `ISchedulerProxy::RequestInitialVirtualProcessors` de `ISchedulerProxy::SubscribeCurrentThread` la suscripción de `IExecutionResource::Remove` un subproceso externo mediante los métodos o deben devolverse al Administrador de recursos mediante antes de que un programador se cierre.

Si el programador tenía alguna raíz de procesador virtual desactivada, debe activarlas mediante [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) `Dispatch` y hacer que los servidores proxy de `Shutdown` subprocesos que se ejecutan en ellos dejen el método de los contextos de ejecución que están distribuyendo antes de invocar en un proxy del programador.

No es necesario que el programador devuelva individualmente todas las raíces del procesador `Remove` virtual que Resource Manager le concedió a través de llamadas al método porque todas las raíces de procesadores virtuales se devolverán al Administrador de recursos al apagarse.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy::SubscribeCurrentThread Método

Registra el subproceso actual con Resource Manager, asociándolo a este programador.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Valor devuelto

La `IExecutionResource` interfaz que representa el subproceso actual en el tiempo de ejecución.

### <a name="remarks"></a>Observaciones

Utilice este método si desea que Resource Manager tenga en cuenta el subproceso actual mientras asigna recursos al programador y a otros programadores. Es especialmente útil cuando el subproceso planea participar en el trabajo en cola en el programador, junto con las raíces del procesador virtual que el programador recibe del Administrador de recursos. Resource Manager usa información para evitar la sobresuscripción innecesaria de subprocesos de hardware en el sistema.

El recurso de ejecución recibido a través de este método debe devolverse al Administrador de recursos mediante el [método IExecutionResource::Remove.](iexecutionresource-structure.md#remove) El subproceso que `Remove` llama al método debe ser `SubscribeCurrentThread` el mismo subproceso que llamó anteriormente al método.

El acto de suscribirse a un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente en uno. El nivel de suscripción se reduce en uno cuando se termina la suscripción. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>Método ISchedulerProxy::UnbindContext

Desasocia un proxy de subproceso del `pContext` contexto de ejecución especificado por el parámetro y lo devuelve al grupo libre del generador de proxy de subprocesos. Este método solo se puede llamar en un contexto de ejecución que se enlaza a través `pContext` de la [ISchedulerProxy::BindContext](#bindcontext) método y aún no se ha iniciado a través de ser el parámetro de un [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) llamada al método.

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
El contexto de ejecución que se va a desasociar de su proxy de subproceso.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IScheduler (estructura)](ischeduler-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager (Estructura)](iresourcemanager-structure.md)
