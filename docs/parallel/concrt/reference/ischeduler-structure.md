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
ms.openlocfilehash: 54db5d664a48f95a952eb1b409839d8ac3421e30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337510"
---
# <a name="ischeduler-structure"></a>IScheduler (Estructura)

Una interfaz a una abstracción de un programador de trabajo. El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.

## <a name="syntax"></a>Sintaxis

```
struct IScheduler;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Proporciona a un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho para ejecutar un subproceso único que puede realizar el trabajo en nombre del programador.|
|[IScheduler::GetId](#getid)|Devuelve un identificador único para el programador.|
|[IScheduler::GetPolicy](#getpolicy)|Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas del programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no se usan por otros programadores.|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Inicia la eliminación de raíces de procesador virtual que se asignaron previamente a este programador.|
|[IScheduler::Statistics](#statistics)|Proporciona información relacionada con las tasas de llegada y finalización de tarea y cambio de longitud de cola para un programador.|

## <a name="remarks"></a>Comentarios

Si está implementando un programador personalizado que se comunica con el Administrador de recursos, debe proporcionar una implementación de la `IScheduler` interfaz. Esta interfaz es un extremo de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo es representado por la `IResourceManager` y `ISchedulerProxy` interfaces implementadas por Resource Manager.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="addvirtualprocessors"></a>  AddVirtualProcessors (método)

Proporciona a un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho para ejecutar un subproceso único que puede realizar el trabajo en nombre del programador.

```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Una matriz de `IVirtualProcessorRoot` raíces de las interfaces que representa el procesador virtual que se agrega al programador.

*count*<br/>
El número de `IVirtualProcessorRoot` interfaces de la matriz.

### <a name="remarks"></a>Comentarios

El Administrador de recursos invoca el `AddVirtualProcessor` método conceder un conjunto inicial de raíces de procesador virtual a un programador. También puede invocar el método para agregar raíces de procesador virtual al programador cuando vuelve a equilibrar los recursos entre los programadores.

##  <a name="getid"></a>  IScheduler:: GetId (método)

Devuelve un identificador único para el programador.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador entero único.

### <a name="remarks"></a>Comentarios

Debe usar el [GetSchedulerId](concurrency-namespace-functions.md) función para obtener un identificador único para el objeto que implementa el `IScheduler` interfaz antes de usar la interfaz como un parámetro a los métodos proporcionados por el Administrador de recursos. Se espera que devuelva el mismo identificador cuando el `GetId` se invoca la función.

Un identificador obtenido de un origen diferente podría provocar un comportamiento indefinido.

##  <a name="getpolicy"></a>  IScheduler:: GetPolicy (método)

Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas del programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una copia de la directiva del programador.

##  <a name="notifyresourcesexternallybusy"></a>  NotifyResourcesExternallyBusy (método)

Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.

```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Una matriz de `IVirtualProcessorRoot` interfaces asociadas con los subprocesos de hardware en el que otros programadores han ocupado.

*count*<br/>
El número de `IVirtualProcessorRoot` interfaces de la matriz.

### <a name="remarks"></a>Comentarios

Es posible que un subproceso de hardware determinado que se asignará a los programadores varias al mismo tiempo. Un motivo para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para cumplir el mínimo de simultaneidad para todos los programadores, sin uso compartido de recursos. Otra posibilidad es que los recursos se asignan temporalmente a otros programadores cuando el programador propietario no las usa, por medio de todas sus raíces de procesador virtual en ese subproceso de hardware que se está desactivando.

El nivel de suscripción de un subproceso de hardware se indica mediante el número de subprocesos está suscritos y activa las raíces de procesador virtual asociadas a ese subproceso del hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción que otros programadores contribuyen. Cuando el nivel de suscripción externo para un subproceso de hardware se mueve desde cero en el territorio positivo, se envían notificaciones que los recursos están ocupados externamente a un programador.

Las notificaciones a través de este método solo se envían a los programadores que tienen una directiva donde el valor de la `MinConcurrency` es igual al valor de clave de la directiva el `MaxConcurrency` clave de la directiva. Para obtener más información sobre las directivas del programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica las notificaciones Obtiene un conjunto de notificaciones iniciales cuando se crea, para informar de si los recursos que se asignó solo son externamente ocupado o inactivo.

##  <a name="notifyresourcesexternallyidle"></a>  NotifyResourcesExternallyIdle (método)

Notifica a este programador que los subprocesos de hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no se usan por otros programadores.

```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Una matriz de `IVirtualProcessorRoot` interfaces asociadas con los subprocesos de hardware en el que otros programadores se han vuelto inactivas.

*count*<br/>
El número de `IVirtualProcessorRoot` interfaces de la matriz.

### <a name="remarks"></a>Comentarios

Es posible que un subproceso de hardware determinado que se asignará a los programadores varias al mismo tiempo. Un motivo para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para cumplir el mínimo de simultaneidad para todos los programadores, sin uso compartido de recursos. Otra posibilidad es que los recursos se asignan temporalmente a otros programadores cuando el programador propietario no las usa, por medio de todas sus raíces de procesador virtual en ese subproceso de hardware que se está desactivando.

El nivel de suscripción de un subproceso de hardware se indica mediante el número de subprocesos está suscritos y activa las raíces de procesador virtual asociadas a ese subproceso del hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción que otros programadores contribuyen. Cuando el nivel de suscripción externo para un subproceso de hardware llega a cero de un valor positivo anterior, se envían notificaciones que los recursos están ocupados externamente a un programador.

Las notificaciones a través de este método solo se envían a los programadores que tienen una directiva donde el valor de la `MinConcurrency` es igual al valor de clave de la directiva el `MaxConcurrency` clave de la directiva. Para obtener más información sobre las directivas del programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica las notificaciones Obtiene un conjunto de notificaciones iniciales cuando se crea, para informar de si los recursos que se asignó solo son externamente ocupado o inactivo.

##  <a name="removevirtualprocessors"></a>  RemoveVirtualProcessors (método)

Inicia la eliminación de raíces de procesador virtual que se asignaron previamente a este programador.

```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Una matriz de `IVirtualProcessorRoot` interfaces que representan las raíces de procesador virtual que va a quitar.

*count*<br/>
El número de `IVirtualProcessorRoot` interfaces de la matriz.

### <a name="remarks"></a>Comentarios

El Administrador de recursos invoca el `RemoveVirtualProcessors` método para volver a tomar un conjunto de raíces de procesador virtual de un programador. Se espera que el programador de invocar el [quitar](iexecutionresource-structure.md#remove) método en cada interfaz cuando se hace con las raíces de procesador virtual. No use un `IVirtualProcessorRoot` interfaz una vez que se han invocado el `Remove` método en él.

El parámetro `ppVirtualProcessorRoots` apunta a una matriz de interfaces. Entre el conjunto de raíces de procesador virtual va a quitar, nunca se han activado las raíces pueden devolverse inmediatamente mediante el `Remove` método. Las raíces que se han activado y son ejecutar el trabajo, o se han desactivado y están esperando a que llegue trabajo, se deben devolver de forma asincrónica. El programador debe hacer todo lo posible para quitar la raíz del procesador virtual tan pronto como sea posible. Retraso en la eliminación de las raíces de procesador virtual puede provocar la sobresuscripción involuntaria dentro del programador.

##  <a name="statistics"></a>  IScheduler:: Statistics (método)

Proporciona información relacionada con las tasas de llegada y finalización de tarea y cambio de longitud de cola para un programador.

```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parámetros

*pTaskCompletionRate*<br/>
El número de tareas que se han completado por el programador desde la última llamada a este método.

*pTaskArrivalRate*<br/>
El número de tareas que se recibieron en el programador desde la última llamada a este método.

*pNumberOfTasksEnqueued*<br/>
El número total de tareas en todas las colas del programador.

### <a name="remarks"></a>Comentarios

Este método se invoca el Administrador de recursos con el fin de recopilar las estadísticas para un programador. Las estadísticas que se recopilan aquí se usará para controlar los algoritmos de comentarios dinámicos para determinar cuándo es adecuado asignar más recursos al programador y cuándo se debe quitar recursos. Los valores proporcionados por el programador pueden ser optimistas y no necesariamente deben reflejar con precisión el recuento actual.

Debe implementar este método si desea que el Administrador de recursos para usar comentarios sobre aspectos tales como la llegada de la tarea para determinar cómo equilibrar los recursos entre su programador y otros programadores registrados con el Administrador de recursos. Si decide no recopilar las estadísticas, puede establecer la clave de directiva `DynamicProgressFeedback` al valor `DynamicProgressFeedbackDisabled` en la directiva de su programador y el recurso administrador no invocará este método en su programador.

En ausencia de información estadística, el Administrador de recursos usará los niveles de suscripción del subproceso de hardware para tomar decisiones de migración y asignación de recursos. Para obtener más información sobre los niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy (clase)](schedulerpolicy-class.md)<br/>
[IExecutionContext (estructura)](iexecutioncontext-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager (estructura)](iresourcemanager-structure.md)
