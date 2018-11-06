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
ms.openlocfilehash: 56042c799f22b0e35bbd0d03d96d649e508f6e51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578950"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource (Estructura)

Una abstracción para un subproceso del hardware.

## <a name="syntax"></a>Sintaxis

```
struct IExecutionResource;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IExecutionResource:: CurrentSubscriptionLevel](#currentsubscriptionlevel)|Devuelve el número de procesador virtual activada raíces y suscrito actualmente asociados con el subproceso de hardware subyacente que representa este recurso de ejecución de subprocesos externos.|
|[IExecutionResource:: GetExecutionResourceId](#getexecutionresourceid)|Devuelve un identificador único para el subproceso de hardware que representa este recurso de ejecución.|
|[IExecutionResource:: GetNodeId](#getnodeid)|Devuelve un identificador único para el nodo del procesador que pertenece este recurso de ejecución.|
|[IExecutionResource:: Remove](#remove)|Devuelve este recurso de ejecución para el Administrador de recursos.|

## <a name="remarks"></a>Comentarios

Recursos de ejecución pueden ser independiente o asociados con raíces de procesador virtual. Cuando un subproceso de la aplicación crea una suscripción de subproceso, se crea un recurso de ejecución independiente. Los métodos [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) y [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) crear suscripciones de subproceso y devuelven un `IExecutionResource` interfaz que representa el suscripción. Crear una suscripción de subproceso es una manera de informar al administrador de recursos que un subproceso determinado participará en el trabajo en cola a un programador, junto con las raíces de procesador virtual asigna el Administrador de recursos para el programador. El Administrador de recursos usa la información para evitar la sobresuscripción de subprocesos de hardware que sea posible.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="currentsubscriptionlevel"></a>  IExecutionResource:: CurrentSubscriptionLevel (método)

Devuelve el número de procesador virtual activada raíces y suscrito actualmente asociados con el subproceso de hardware subyacente que representa este recurso de ejecución de subprocesos externos.

```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El nivel de suscripción actual.

### <a name="remarks"></a>Comentarios

El nivel de suscripción indica cuántos subprocesos en ejecución están asociados con el subproceso de hardware. Esto incluye solo el Administrador de recursos es tener en cuenta en el formulario de subprocesos está suscritos y raíces de procesador virtual que están ejecutando activamente el proxy del subproceso de subprocesos.

Una llamada al método [ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), o el método [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) con el parámetro `doSubscribeCurrentThread` establecido en el valor **true** aumenta el nivel de suscripción de un subproceso de hardware en uno. Asimismo, devuelven un `IExecutionResource` interfaz que representa la suscripción. Una llamada correspondiente a la [IExecutionResource](#remove) disminuye nivel de suscripción del subproceso de hardware en uno.

La acción de activar una raíz del procesador virtual mediante el método [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) aumenta el nivel de suscripción de un subproceso de hardware en uno. Los métodos [IVirtualProcessorRoot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate), o [IExecutionResource](#remove) disminuir el nivel de suscripción en uno cuando se invoca en una raíz del procesador virtual activada.

El Administrador de recursos usa la información de nivel de suscripción como una de las maneras en que se va a determinar cuándo se deben mover recursos entre los programadores.

##  <a name="getexecutionresourceid"></a>  IExecutionResource:: GetExecutionResourceId (método)

Devuelve un identificador único para el subproceso de hardware que representa este recurso de ejecución.

```
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador único para el subproceso del hardware subyacente de este recurso de ejecución.

### <a name="remarks"></a>Comentarios

Cada subproceso de hardware se asigna un identificador único por el Runtime de simultaneidad. Si varios recursos de ejecución están asociado hardware subproceso, todos tendrán el mismo identificador de recurso de ejecución.

##  <a name="getnodeid"></a>  IExecutionResource:: GetNodeId (método)

Devuelve un identificador único para el nodo del procesador que pertenece este recurso de ejecución.

```
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador único para un nodo del procesador.

### <a name="remarks"></a>Comentarios

El Runtime de simultaneidad representa los subprocesos de hardware en el sistema en grupos de nodos de procesador. Nodos normalmente se derivan de la topología del hardware del sistema. Por ejemplo, todos los procesadores en un socket específico o un nodo NUMA determinado pueden pertenecer al mismo nodo de procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluyendo `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador en el sistema.

Se puede obtener el recuento de nodos de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).

##  <a name="remove"></a>  IExecutionResource:: Remove (método)

Devuelve este recurso de ejecución para el Administrador de recursos.

```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parámetros

*pScheduler*<br/>
Interfaz para el programador que realiza la solicitud para quitar este recurso de ejecución.

### <a name="remarks"></a>Comentarios

Utilice este método para devolver los recursos de ejecución independientes, así como recursos de ejecución asociados con raíces de procesador virtual a Resource Manager.

Si se trata de un recurso de ejecución independiente que recibió de cualquiera de los métodos [ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) o [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), al llamar a la método `Remove` finalizará la suscripción del subproceso que el recurso se creó para representar. Deben terminar todas las suscripciones del subproceso antes de cerrar un proxy del programador y debe llamar a `Remove` desde el subproceso que creó la suscripción.

Raíces de procesador virtual, también pueden devolverse a Resource Manager mediante la invocación de la `Remove` método, porque la interfaz `IVirtualProcessorRoot` hereda el `IExecutionResource` interfaz. Es posible que deba devolver una raíz del procesador virtual en respuesta a una llamada a la [RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) método, o cuando haya terminado con una raíz de la suscripción excesiva de procesador virtual que obtuvo en el [ ISchedulerProxy:: CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber) método. Para las raíces de procesador virtual, no hay ninguna restricción en qué subproceso se puede invocar el `Remove` método.

`invalid_argument` se produce si el parámetro `pScheduler` está establecido en `NULL`.

`invalid_operation` se produce si el parámetro `pScheduler` es distinta del programador que se creó este recurso de ejecución para, o bien, con un recurso de ejecución independiente, si el subproceso actual es diferente del subproceso que creó la suscripción del subproceso.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
