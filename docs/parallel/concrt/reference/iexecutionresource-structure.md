---
title: IExecutionResource (estructura)
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
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424264"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource (estructura)

Una abstracción para un subproceso del hardware.

## <a name="syntax"></a>Sintaxis

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IExecutionResource:: Currentsubscriptionlevel (](#currentsubscriptionlevel)|Devuelve el número de raíces del procesador virtual activadas y los subprocesos externos suscritos asociados actualmente al subproceso de hardware subyacente que este recurso de ejecución representa.|
|[IExecutionResource:: GetExecutionResourceId (](#getexecutionresourceid)|Devuelve un identificador único para el subproceso de hardware que este recurso de ejecución representa.|
|[IExecutionResource:: GetNodeID (](#getnodeid)|Devuelve un identificador único para el nodo de procesador al que pertenece este recurso de ejecución.|
|[IExecutionResource:: Remove](#remove)|Devuelve este recurso de ejecución al Administrador de recursos.|

## <a name="remarks"></a>Observaciones

Los recursos de ejecución pueden ser independientes o asociarse a las raíces del procesador virtual. Se crea un recurso de ejecución independiente cuando un subproceso de la aplicación crea una suscripción de subproceso. Los métodos [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) y [ISchedulerProxy:: requestinitialvirtualprocessors (](ischedulerproxy-structure.md#requestinitialvirtualprocessors) crean suscripciones de subproceso y devuelven una interfaz `IExecutionResource` que representa la suscripción. Crear una suscripción de subproceso es una manera de informar al Administrador de recursos de que un subproceso determinado participará en el trabajo en cola en un programador, junto con las raíces del procesador virtual Administrador de recursos asigna al programador. En el Administrador de recursos se usa la información para evitar los subprocesos de hardware de sobresuscripción en los que puede.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="currentsubscriptionlevel"></a>IExecutionResource:: Currentsubscriptionlevel ((método)

Devuelve el número de raíces del procesador virtual activadas y los subprocesos externos suscritos asociados actualmente al subproceso de hardware subyacente que este recurso de ejecución representa.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Nivel de suscripción actual.

### <a name="remarks"></a>Observaciones

El nivel de suscripción le indica cuántos subprocesos en ejecución están asociados con el subproceso de hardware. Esto solo incluye los subprocesos que reconoce el Administrador de recursos en forma de subprocesos suscritos y las raíces del procesador virtual que ejecutan activamente los proxies de subprocesos.

Al llamar al método [ischedulerproxy:: subscribecurrentthread (](ischedulerproxy-structure.md#subscribecurrentthread)o al método [Ischedulerproxy:: requestinitialvirtualprocessors (](ischedulerproxy-structure.md#requestinitialvirtualprocessors) con el parámetro `doSubscribeCurrentThread` establecido en el valor **true** , se incrementa el nivel de suscripción de un subproceso de hardware en uno. También devuelven una interfaz `IExecutionResource` que representa la suscripción. Una llamada correspondiente a [IExecutionResource:: Remove](#remove) disminuye en uno el nivel de suscripción del subproceso de hardware.

El hecho de activar una raíz del procesador virtual mediante el método [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) incrementa el nivel de suscripción de un subproceso de hardware en uno. Los métodos [IVirtualProcessorRoot::D eactivate](ivirtualprocessorroot-structure.md#deactivate)o [IExecutionResource:: Remove](#remove) disminuyen el nivel de suscripción en uno cuando se invoca en una raíz del procesador virtual activada.

El Administrador de recursos usa la información de nivel de suscripción como una de las formas en que se debe determinar cuándo se deben trasladar los recursos entre los programadores.

## <a name="getexecutionresourceid"></a>IExecutionResource:: GetExecutionResourceId ((método)

Devuelve un identificador único para el subproceso de hardware que este recurso de ejecución representa.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único para el subproceso de hardware subyacente a este recurso de ejecución.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad asigna a cada subproceso de hardware un identificador único. Si hay varios recursos de ejecución asociados a un subproceso de hardware, todos tendrán el mismo identificador de recurso de ejecución.

## <a name="getnodeid"></a>IExecutionResource:: GetNodeID ((método)

Devuelve un identificador único para el nodo de procesador al que pertenece este recurso de ejecución.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único para un nodo de procesador.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad representa los subprocesos de hardware en el sistema en grupos de nodos de procesador. Normalmente, los nodos se derivan de la topología de hardware del sistema. Por ejemplo, todos los procesadores de un socket específico o un nodo NUMA específico pueden pertenecer al mismo nodo del procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluye `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador del sistema.

El recuento de nodos puede obtenerse a partir de la función [getprocessornodecount (](concurrency-namespace-functions.md).

## <a name="remove"></a>IExecutionResource:: Remove (método)

Devuelve este recurso de ejecución al Administrador de recursos.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parámetros

*pScheduler*<br/>
Una interfaz al programador que realiza la solicitud para quitar este recurso de ejecución.

### <a name="remarks"></a>Observaciones

Utilice este método para devolver los recursos de ejecución independientes, así como los recursos de ejecución asociados a las raíces del procesador virtual al Administrador de recursos.

Si se trata de un recurso de ejecución independiente que recibió de cualquiera de los métodos [ISchedulerProxy:: subscribecurrentthread (](ischedulerproxy-structure.md#subscribecurrentthread) o [ISchedulerProxy:: requestinitialvirtualprocessors (](ischedulerproxy-structure.md#requestinitialvirtualprocessors), al llamar al método `Remove` finalizará la suscripción de subproceso que el recurso se creó para representar. Debe finalizar todas las suscripciones de subproceso antes de cerrar un proxy del programador y debe llamar a `Remove` desde el subproceso que creó la suscripción.

También se pueden devolver raíces del procesador virtual al Administrador de recursos invocando el método `Remove`, porque la interfaz `IVirtualProcessorRoot` hereda de la interfaz `IExecutionResource`. Es posible que necesite devolver una raíz del procesador virtual en respuesta a una llamada al método [IScheduler:: removevirtualprocessors (](ischeduler-structure.md#removevirtualprocessors) , o bien cuando haya terminado con una raíz del procesador virtual sobresuscrita obtenida del método [ISchedulerProxy:: createoversubscriber (](ischedulerproxy-structure.md#createoversubscriber) . En el caso de las raíces del procesador virtual, no hay restricciones en las que el subproceso puede invocar el método `Remove`.

`invalid_argument` se produce si el parámetro `pScheduler` está establecido en `NULL`.

`invalid_operation` se produce si el parámetro `pScheduler` es diferente del programador para el que se creó este recurso de ejecución, o con un recurso de ejecución independiente, si el subproceso actual es diferente del subproceso que creó la suscripción de subproceso.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
