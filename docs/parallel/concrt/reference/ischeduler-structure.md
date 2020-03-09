---
title: IScheduler (estructura)
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
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854205"
---
# <a name="ischeduler-structure"></a>IScheduler (estructura)

Una interfaz a una abstracción de un programador de trabajo. El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.

## <a name="syntax"></a>Sintaxis

```cpp
struct IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IScheduler:: Addvirtualprocessors (](#addvirtualprocessors)|Proporciona un programador con un conjunto de raíces de procesador virtual para su uso. Cada interfaz de `IVirtualProcessorRoot` representa el derecho para ejecutar un único subproceso que puede realizar el trabajo en nombre del programador.|
|[IScheduler:: GetId](#getid)|Devuelve un identificador único para el programador.|
|[IScheduler:: GetPolicy](#getpolicy)|Devuelve una copia de la Directiva del programador. Para obtener más información sobre las directivas de Scheduler, consulte [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler:: Notifyresourcesexternallybusy (](#notifyresourcesexternallybusy)|Notifica a este programador que los subprocesos de hardware que representa el conjunto de raíces del procesador virtual de la matriz `ppVirtualProcessorRoots` están siendo utilizados por otros programadores.|
|[IScheduler:: Notifyresourcesexternallyidle (](#notifyresourcesexternallyidle)|Notifica a este programador que los subprocesos de hardware que representa el conjunto de raíces del procesador virtual de la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.|
|[IScheduler:: Removevirtualprocessors (](#removevirtualprocessors)|Inicia la eliminación de las raíces del procesador virtual que se asignaron previamente a este programador.|
|[IScheduler:: Statistics](#statistics)|Proporciona información relacionada con las tasas de llegada y finalización de las tareas, así como el cambio en la longitud de la cola de un programador.|

## <a name="remarks"></a>Observaciones

Si está implementando un programador personalizado que se comunica con el Administrador de recursos, debe proporcionar una implementación de la interfaz de `IScheduler`. Esta interfaz es un extremo de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo se representa mediante las interfaces `IResourceManager` y `ISchedulerProxy` implementadas por el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="addvirtualprocessors"></a>IScheduler:: Addvirtualprocessors ((método)

Proporciona un programador con un conjunto de raíces de procesador virtual para su uso. Cada interfaz de `IVirtualProcessorRoot` representa el derecho para ejecutar un único subproceso que puede realizar el trabajo en nombre del programador.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de interfaces `IVirtualProcessorRoot` que representan las raíces del procesador virtual que se agregan al programador.

*count*<br/>
Número de interfaces `IVirtualProcessorRoot` de la matriz.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invoca el método `AddVirtualProcessor` para conceder un conjunto inicial de raíces del procesador virtual a un programador. También puede invocar el método para agregar raíces del procesador virtual al programador cuando reequilibra los recursos entre los programadores.

## <a name="getid"></a>IScheduler:: GetId (método)

Devuelve un identificador único para el programador.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador entero único.

### <a name="remarks"></a>Observaciones

Debe usar la función [getschedulerid (](concurrency-namespace-functions.md) para obtener un identificador único para el objeto que implementa la interfaz `IScheduler`, antes de utilizar la interfaz como parámetro para los métodos proporcionados por la administrador de recursos. Se espera que devuelva el mismo identificador cuando se invoca la función `GetId`.

Un identificador Obtenido de un origen diferente podría producir un comportamiento indefinido.

## <a name="getpolicy"></a>IScheduler:: GetPolicy (método)

Devuelve una copia de la Directiva del programador. Para obtener más información sobre las directivas de Scheduler, consulte [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una copia de la Directiva del programador.

## <a name="notifyresourcesexternallybusy"></a>IScheduler:: Notifyresourcesexternallybusy ((método)

Notifica a este programador que los subprocesos de hardware que representa el conjunto de raíces del procesador virtual de la matriz `ppVirtualProcessorRoots` están siendo utilizados por otros programadores.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de interfaces `IVirtualProcessorRoot` asociadas a los subprocesos de hardware en los que otros programadores han dejado de estar ocupados.

*count*<br/>
Número de interfaces `IVirtualProcessorRoot` de la matriz.

### <a name="remarks"></a>Observaciones

Es posible que un subproceso de hardware determinado se asigne a varios programadores al mismo tiempo. Una razón para ello puede ser que no haya suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima de todos los programadores, sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no los esté usando, por medio de todas sus raíces del procesador virtual en ese subproceso de hardware desactivado.

El nivel de suscripción de un subproceso de hardware está indicado por el número de subprocesos suscritos y las raíces del procesador virtual activadas asociadas a ese subproceso de hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción a la que contribuyen otros programadores. Las notificaciones de que los recursos están ocupados externamente se envían a un programador cuando el nivel de suscripción externo de un subproceso de hardware pasa de cero al territorio positivo.

Las notificaciones a través de este método solo se envían a los programadores que tienen una directiva en la que el valor de la clave de directiva de `MinConcurrency` es igual al valor de la clave de directiva de `MaxConcurrency`. Para obtener más información sobre las directivas de Scheduler, consulte [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica para notificaciones obtiene un conjunto de notificaciones iniciales cuando se crea, lo que informa de si los recursos que se acaban de asignar están ocupados externamente o inactivos.

## <a name="notifyresourcesexternallyidle"></a>IScheduler:: Notifyresourcesexternallyidle ((método)

Notifica a este programador que los subprocesos de hardware que representa el conjunto de raíces del procesador virtual de la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de interfaces `IVirtualProcessorRoot` asociadas a los subprocesos de hardware en los que otros programadores han dejado de estar inactivos.

*count*<br/>
Número de interfaces `IVirtualProcessorRoot` de la matriz.

### <a name="remarks"></a>Observaciones

Es posible que un subproceso de hardware determinado se asigne a varios programadores al mismo tiempo. Una razón para ello puede ser que no haya suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima de todos los programadores, sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no los esté usando, por medio de todas sus raíces del procesador virtual en ese subproceso de hardware desactivado.

El nivel de suscripción de un subproceso de hardware está indicado por el número de subprocesos suscritos y las raíces del procesador virtual activadas asociadas a ese subproceso de hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso de hardware es la parte de la suscripción a la que contribuyen otros programadores. Las notificaciones de que los recursos están ocupados externamente se envían a un programador cuando el nivel de suscripción externo de un subproceso de hardware cae a cero de un valor positivo anterior.

Las notificaciones a través de este método solo se envían a los programadores que tienen una directiva en la que el valor de la clave de directiva de `MinConcurrency` es igual al valor de la clave de directiva de `MaxConcurrency`. Para obtener más información sobre las directivas de Scheduler, consulte [SchedulerPolicy](schedulerpolicy-class.md).

Un programador que califica para notificaciones obtiene un conjunto de notificaciones iniciales cuando se crea, lo que informa de si los recursos que se acaban de asignar están ocupados externamente o inactivos.

## <a name="removevirtualprocessors"></a>IScheduler:: Removevirtualprocessors ((método)

Inicia la eliminación de las raíces del procesador virtual que se asignaron previamente a este programador.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Parámetros

*ppVirtualProcessorRoots*<br/>
Matriz de interfaces `IVirtualProcessorRoot` que representan las raíces del procesador virtual que se van a quitar.

*count*<br/>
Número de interfaces `IVirtualProcessorRoot` de la matriz.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invoca el método `RemoveVirtualProcessors` para recuperar un conjunto de raíces del procesador virtual de un programador. Se espera que el programador invoque el método [Remove](iexecutionresource-structure.md#remove) en cada interfaz cuando se realiza con las raíces del procesador virtual. No utilice una interfaz `IVirtualProcessorRoot` una vez que se haya invocado el método `Remove` en ella.

El parámetro `ppVirtualProcessorRoots` apunta a una matriz de interfaces. Entre el conjunto de raíces del procesador virtual que se van a quitar, las raíces nunca se han activado se pueden devolver inmediatamente mediante el método `Remove`. Las raíces que se han activado y que se ejecutan en el trabajo, o que se han desactivado y están esperando a que llegue el trabajo, se deben devolver de forma asincrónica. El programador debe realizar todos los intentos de quitar la raíz del procesador virtual lo más rápido posible. Al retrasar la eliminación de las raíces del procesador virtual, se puede producir una sobresuscripción involuntaria en el programador.

## <a name="statistics"></a>IScheduler:: Statistics (método)

Proporciona información relacionada con las tasas de llegada y finalización de las tareas, así como el cambio en la longitud de la cola de un programador.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Parámetros

*pTaskCompletionRate*<br/>
El número de tareas que el programador ha completado desde la última llamada a este método.

*pTaskArrivalRate*<br/>
El número de tareas que han llegado al programador desde la última llamada a este método.

*pNumberOfTasksEnqueued*<br/>
El número total de tareas en todas las colas del programador.

### <a name="remarks"></a>Observaciones

El Administrador de recursos invoca este método para recopilar las estadísticas de un programador. Las estadísticas recopiladas aquí se usarán para impulsar algoritmos de comentarios dinámicos con el fin de determinar cuándo es adecuado asignar más recursos al programador y cuándo quitar recursos. Los valores proporcionados por Scheduler pueden ser optimistas y no tienen por qué reflejar el recuento actual con precisión.

Debe implementar este método si desea que el Administrador de recursos use comentarios sobre cosas como la llegada de la tarea para determinar cómo equilibrar el recurso entre el programador y otros programadores registrados con el Administrador de recursos. Si decide no recopilar estadísticas, puede establecer la clave de la Directiva `DynamicProgressFeedback` en el valor `DynamicProgressFeedbackDisabled` en la Directiva del programador y el Administrador de recursos no invocará este método en el programador.

En ausencia de información estadística, el Administrador de recursos utilizará los niveles de suscripción de subprocesos de hardware para tomar decisiones de asignación de recursos y migración. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Policyelementkey (](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy (clase)](schedulerpolicy-class.md)<br/>
[IExecutionContext (estructura)](iexecutioncontext-structure.md)<br/>
[IThreadProxy (estructura)](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager (estructura)](iresourcemanager-structure.md)
