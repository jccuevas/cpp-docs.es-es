---
title: IScheduler (Estructura)
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368169"
---
# <a name="ischeduler-structure"></a>IScheduler (Estructura)

Una interfaz a una abstracción de un programador de trabajo. El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.

## <a name="syntax"></a>Sintaxis

```cpp
struct IScheduler;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Proporciona un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho a ejecutar un único subproceso que puede realizar el trabajo en nombre del programador.|
|[IScheduler::GetId](#getid)|Devuelve un identificador único para el programador.|
|[IScheduler::GetPolicy](#getpolicy)|Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas del programador, vea [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Inicia la eliminación de las raíces del procesador virtual que se asignaron previamente a este programador.|
|[IScheduler::Estadísticas](#statistics)|Proporciona información relacionada con las tasas de llegada y finalización de tareas, y cambio en la longitud de la cola para un programador.|

## <a name="remarks"></a>Observaciones

Si va a implementar un programador personalizado que se comunica con `IScheduler` Resource Manager, debe proporcionar una implementación de la interfaz. Esta interfaz es un extremo de un canal bidireccional de comunicación entre un programador y Resource Manager. El otro extremo está `IResourceManager` representado `ISchedulerProxy` por las interfaces y que implementa Resource Manager.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler::AddVirtualProcessors Método

Proporciona un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho a ejecutar un único subproceso que puede realizar el trabajo en nombre del programador.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de `IVirtualProcessorRoot` interfaces que representan las raíces del procesador virtual que se agregan al programador.

*count*<br/>
El número `IVirtualProcessorRoot` de interfaces en la matriz.

### <a name="remarks"></a>Observaciones

Resource Manager invoca `AddVirtualProcessor` el método para conceder un conjunto inicial de raíces de procesador virtual a un programador. También podría invocar el método para agregar raíces de procesador virtual al programador cuando reequilibra los recursos entre programadores.

## <a name="ischedulergetid-method"></a><a name="getid"></a>IScheduler::GetId Método

Devuelve un identificador único para el programador.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

### <a name="remarks"></a>Observaciones

Debe usar la función [GetSchedulerId](concurrency-namespace-functions.md) para obtener un identificador `IScheduler` único para el objeto que implementa la interfaz, antes de usar la interfaz como parámetro para los métodos proporcionados por el Administrador de recursos. Se espera que devuelva el `GetId` mismo identificador cuando se invoca la función.

Un identificador obtenido de un origen diferente podría dar lugar a un comportamiento indefinido.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler::GetPolicy Método

Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas del programador, vea [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una copia de la directiva del programador.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler::NotifyResourcesExternallyBusy Método

Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de `IVirtualProcessorRoot` interfaces asociadas a los subprocesos de hardware en los que otros programadores han ocupado.

*count*<br/>
El número `IVirtualProcessorRoot` de interfaces en la matriz.

### <a name="remarks"></a>Observaciones

Es posible que un subproceso de hardware determinado se asigne a varios programadores al mismo tiempo. Una razón para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima para todos los programadores, sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no los está utilizando, a través de todas sus raíces de procesador virtual en ese subproceso de hardware que se está desactivando.

El nivel de suscripción de un subproceso de hardware se indica por el número de subprocesos suscritos y las raíces de procesador virtual activadas asociadas a ese subproceso de hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción a la que contribuyen otros programadores. Las notificaciones de que los recursos están ocupados externamente se envían a un programador cuando el nivel de suscripción externa de un subproceso de hardware se mueve de cero a territorio positivo.

Las notificaciones a través de este método solo se `MinConcurrency` envían a programadores que `MaxConcurrency` tienen una directiva donde el valor de la clave de directiva es igual al valor de la clave de directiva. Para obtener más información sobre las directivas del programador, vea [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica para las notificaciones obtiene un conjunto de notificaciones iniciales cuando se crea, informándolo si los recursos que se le acaban de asignar están ocupados externamente o inactivos.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>IScheduler::NotifyResourcesExternallyIdle Método

Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de `IVirtualProcessorRoot` interfaces asociadas a subprocesos de hardware en los que otros programadores se han quedado inactivos.

*count*<br/>
El número `IVirtualProcessorRoot` de interfaces en la matriz.

### <a name="remarks"></a>Observaciones

Es posible que un subproceso de hardware determinado se asigne a varios programadores al mismo tiempo. Una razón para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima para todos los programadores, sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no los está utilizando, a través de todas sus raíces de procesador virtual en ese subproceso de hardware que se está desactivando.

El nivel de suscripción de un subproceso de hardware se indica por el número de subprocesos suscritos y las raíces de procesador virtual activadas asociadas a ese subproceso de hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción a la que contribuyen otros programadores. Las notificaciones de que los recursos están ocupados externamente se envían a un programador cuando el nivel de suscripción externa de un subproceso de hardware cae a cero desde un valor positivo anterior.

Las notificaciones a través de este método solo se `MinConcurrency` envían a programadores que `MaxConcurrency` tienen una directiva donde el valor de la clave de directiva es igual al valor de la clave de directiva. Para obtener más información sobre las directivas del programador, vea [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica para las notificaciones obtiene un conjunto de notificaciones iniciales cuando se crea, informándolo si los recursos que se le acaban de asignar están ocupados externamente o inactivos.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler::RemoveVirtualProcessors Método

Inicia la eliminación de las raíces del procesador virtual que se asignaron previamente a este programador.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de `IVirtualProcessorRoot` interfaces que representan las raíces del procesador virtual que se van a quitar.

*count*<br/>
El número `IVirtualProcessorRoot` de interfaces en la matriz.

### <a name="remarks"></a>Observaciones

Resource Manager invoca `RemoveVirtualProcessors` el método para recuperar un conjunto de raíces de procesador virtual de un programador. Se espera que el programador invoque el método [Remove](iexecutionresource-structure.md#remove) en cada interfaz cuando se realiza con las raíces del procesador virtual. No utilice `IVirtualProcessorRoot` una interfaz una `Remove` vez que haya invocado el método en ella.

El `ppVirtualProcessorRoots` parámetro apunta a una matriz de interfaces. Entre el conjunto de raíces de procesador virtual que se va a `Remove` eliminar, las raíces nunca se han activado se pueden devolver inmediatamente utilizando el método. Las raíces que se han activado y están ejecutando el trabajo, o se han desactivado y están esperando a que llegue el trabajo, deben devolverse de forma asincrónica. El programador debe realizar todos los intentos para quitar la raíz del procesador virtual lo antes posible. Retrasar la eliminación de las raíces del procesador virtual puede dar lugar a una sobresuscripción involuntaria dentro del programador.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler::Método de estadísticas

Proporciona información relacionada con las tasas de llegada y finalización de tareas, y cambio en la longitud de la cola para un programador.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parámetros

*pTaskCompletionRate*<br/>
El número de tareas que ha completado el programador desde la última llamada a este método.

*pTaskArrivalRate*<br/>
El número de tareas que han llegado al programador desde la última llamada a este método.

*pNumberOfTasksEnqueued*<br/>
El número total de tareas en todas las colas del programador.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invoca este método para recopilar estadísticas para un programador. Las estadísticas recopiladas aquí se utilizarán para generar algoritmos de retroalimentación dinámica para determinar cuándo es apropiado asignar más recursos al programador y cuándo quitar recursos. Los valores proporcionados por el programador pueden ser optimistas y no necesariamente tienen que reflejar el recuento actual con precisión.

Debe implementar este método si desea que Resource Manager use comentarios sobre aspectos como la llegada de tareas para determinar cómo equilibrar el recurso entre el programador y otros programadores registrados con Resource Manager. Si decide no recopilar estadísticas, puede establecer `DynamicProgressFeedback` la `DynamicProgressFeedbackDisabled` clave de directiva en el valor de la directiva del programador y Resource Manager no invocará este método en el programador.

En ausencia de información estadística, Resource Manager usará niveles de suscripción de subprocesos de hardware para tomar decisiones de migración y asignación de recursos. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy (Clase)](schedulerpolicy-class.md)<br/>
[IExecutionContext (estructura)](iexecutioncontext-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager (Estructura)](iresourcemanager-structure.md)
