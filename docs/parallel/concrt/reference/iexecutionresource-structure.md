---
title: IExecutionResource (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377311"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource (Estructura)

Una abstracción para un subproceso del hardware.

## <a name="syntax"></a>Sintaxis

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Devuelve el número de raíces de procesador virtual activadas y subprocesos externos suscritos actualmente asociados con el subproceso de hardware subyacente que representa este recurso de ejecución.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Devuelve un identificador único para el subproceso de hardware que representa este recurso de ejecución.|
|[IExecutionResource::GetNodeId](#getnodeid)|Devuelve un identificador único para el nodo de procesador al que pertenece este recurso de ejecución.|
|[IExecutionResource::Remove](#remove)|Devuelve este recurso de ejecución al Administrador de recursos.|

## <a name="remarks"></a>Observaciones

Los recursos de ejecución pueden ser independientes o asociados con las raíces del procesador virtual. Se crea un recurso de ejecución independiente cuando un subproceso de la aplicación crea una suscripción de subproceso. Los métodos [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) e [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) crean `IExecutionResource` suscripciones de subprocesos y devuelven una interfaz que representa la suscripción. La creación de una suscripción de subproceso es una forma de informar al Administrador de recursos de que un subproceso determinado participará en el trabajo en cola en un programador, junto con las raíces del procesador virtual que Resource Manager asigna al programador. Resource Manager usa la información para evitar sobresuscribir subprocesos de hardware donde pueda.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>Método IExecutionResource::CurrentSubscriptionLevel

Devuelve el número de raíces de procesador virtual activadas y subprocesos externos suscritos actualmente asociados con el subproceso de hardware subyacente que representa este recurso de ejecución.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El nivel de suscripción actual.

### <a name="remarks"></a>Observaciones

El nivel de suscripción indica cuántos subprocesos en ejecución están asociados con el subproceso de hardware. Esto solo incluye subprocesos que el Administrador de recursos de recursos conoce en forma de subprocesos suscritos y raíces de procesador virtual que ejecutan activamente proxies de subprocesos.

Llamar al método [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), o el método [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) con el parámetro `doSubscribeCurrentThread` establecido en el valor **true** incrementa el nivel de suscripción de un subproceso de hardware en uno. También devuelven `IExecutionResource` una interfaz que representa la suscripción. Una llamada correspondiente a la [IExecutionResource::Remove](#remove) disminuye el nivel de suscripción del subproceso de hardware por uno.

El acto de activar una raíz de procesador virtual mediante el método [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) incrementa el nivel de suscripción de un subproceso de hardware en uno. Los métodos [IVirtualProcessorRoot::Deactivate](ivirtualprocessorroot-structure.md#deactivate)o [IExecutionResource::Remove](#remove) disminuyen el nivel de suscripción por uno cuando se invoca en una raíz de procesador virtual activada.

Resource Manager usa la información de nivel de suscripción como una de las formas de determinar cuándo mover recursos entre programadores.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>IExecutionResource::GetExecutionResourceId (método)

Devuelve un identificador único para el subproceso de hardware que representa este recurso de ejecución.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único para el subproceso de hardware subyacente a este recurso de ejecución.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad asigna un identificador único a cada subproceso de hardware. Si varios recursos de ejecución están asociados con subprocesode hardware, todos tendrán el mismo identificador de recurso de ejecución.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>IExecutionResource::GetNodeId Método

Devuelve un identificador único para el nodo de procesador al que pertenece este recurso de ejecución.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único para un nodo de procesador.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad representa subprocesos de hardware en el sistema en grupos de nodos de procesador. Los nodos se derivan generalmente de la topología de hardware del sistema. Por ejemplo, todos los procesadores de un socket específico o un nodo NUMA específico pueden pertenecer al mismo nodo de procesador. Resource Manager asigna identificadores únicos a `0` estos nodos `nodeCount - 1`empezando por , donde `nodeCount` representa el número total de nodos de procesador en el sistema.

El recuento de nodos se puede obtener de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>IExecutionResource::Remove Método

Devuelve este recurso de ejecución al Administrador de recursos.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parámetros

*pScheduler*<br/>
Interfaz para el programador que realiza la solicitud para quitar este recurso de ejecución.

### <a name="remarks"></a>Observaciones

Utilice este método para devolver recursos de ejecución independientes, así como recursos de ejecución asociados con las raíces del procesador virtual al Administrador de recursos.

Si se trata de un recurso de ejecución independiente que recibió de cualquiera de los métodos [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) o [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), al llamar al método `Remove` finalizará la suscripción de subproceso que se creó para representar el recurso. Debe finalizar todas las suscripciones de subprocesos antes de `Remove` cerrar un proxy del programador y debe llamar desde el subproceso que creó la suscripción.

Las raíces del procesador virtual también se pueden devolver `Remove` al Administrador `IVirtualProcessorRoot` de recursos `IExecutionResource` invocando el método, porque la interfaz hereda de la interfaz. Es posible que deba devolver una raíz de procesador virtual en respuesta a una llamada al método [IScheduler::RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) o cuando haya terminado con una raíz de procesador virtual sobresuscrita que obtuvo del método [ISchedulerProxy::CreateOversubscriber.](ischedulerproxy-structure.md#createoversubscriber) Para las raíces del procesador virtual, no hay `Remove` restricciones sobre qué subproceso puede invocar el método.

`invalid_argument`se produce si `pScheduler` el parámetro `NULL`se establece en .

`invalid_operation`se produce si `pScheduler` el parámetro es diferente del programador para el que se creó este recurso de ejecución o, con un recurso de ejecución independiente, si el subproceso actual es diferente del subproceso que creó la suscripción de subproceso.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
