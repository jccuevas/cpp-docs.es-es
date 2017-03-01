---
title: IScheduler (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IScheduler
dev_langs:
- C++
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: fd8733bdcf113497b82cb2559eaba5a6a4a15165
ms.lasthandoff: 02/24/2017

---
# <a name="ischeduler-structure"></a>IScheduler (Estructura)
Una interfaz a una abstracción de un programador de trabajo. El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IScheduler:: AddVirtualProcessors (método)](#addvirtualprocessors)|Proporciona a un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho para ejecutar un subproceso único que puede realizar el trabajo en nombre del programador.|  
|[IScheduler:: GetId (método)](#getid)|Devuelve un identificador único para el programador.|  
|[IScheduler:: GetPolicy (método)](#getpolicy)|Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas de programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).|  
|[IScheduler:: NotifyResourcesExternallyBusy (método)](#notifyresourcesexternallybusy)|Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.|  
|[IScheduler:: NotifyResourcesExternallyIdle (método)](#notifyresourcesexternallyidle)|Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.|  
|[IScheduler:: RemoveVirtualProcessors (método)](#removevirtualprocessors)|Inicia la eliminación de raíces de procesador virtual que se asignaron previamente a este programador.|  
|[IScheduler:: Statistics (método)](#statistics)|Proporciona información relacionada con tasas de llegada y finalización de la tarea y el cambio de longitud de cola para un programador.|  
  
## <a name="remarks"></a>Comentarios  
 Si está implementando un programador personalizado que comunica con el Administrador de recursos, debe proporcionar una implementación de la `IScheduler` interfaz. Esta interfaz es uno de los extremos de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo está representado por la `IResourceManager` y `ISchedulerProxy` interfaces implementadas por el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IScheduler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameaddvirtualprocessorsa--ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler:: AddVirtualProcessors (método)  
 Proporciona a un programador con un conjunto de raíces de procesador virtual para su uso. Cada `IVirtualProcessorRoot` interfaz representa el derecho para ejecutar un subproceso único que puede realizar el trabajo en nombre del programador.  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `ppVirtualProcessorRoots`  
 Una matriz de `IVirtualProcessorRoot` raíces de interfaces que representan el procesador virtual que se agrega al programador.  
  
 `count`  
 El número de `IVirtualProcessorRoot` interfaces de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 El Administrador de recursos invoca el `AddVirtualProcessor` método conceder un conjunto inicial de raíces de procesador virtual a un programador. También puede invocar el método para agregar raíces de procesador virtual al programador cuando vuelve a equilibrar los recursos entre los programadores.  
  
##  <a name="a-namegetida--ischedulergetid-method"></a><a name="getid"></a>IScheduler:: GetId (método)  
 Devuelve un identificador único para el programador.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador entero único.  
  
### <a name="remarks"></a>Comentarios  
 Debe utilizar el [GetSchedulerId](concurrency-namespace-functions.md) function para obtener un identificador único para el objeto que implementa el `IScheduler` interfaz antes de utilizar la interfaz como un parámetro a los métodos proporcionados por el Administrador de recursos. Se espera que devuelva el mismo identificador cuando el `GetId` se invoca la función.  
  
 Un identificador obtenido de un origen diferente podría provocar un comportamiento indefinido.  
  
##  <a name="a-namegetpolicya--ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler:: GetPolicy (método)  
 Devuelve una copia de la directiva del programador. Para obtener más información sobre las directivas de programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la directiva del programador.  
  
##  <a name="a-namenotifyresourcesexternallybusya--ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler:: NotifyResourcesExternallyBusy (método)  
 Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` ahora están siendo utilizados por otros programadores.  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `ppVirtualProcessorRoots`  
 Una matriz de `IVirtualProcessorRoot` interfaces asociadas con los subprocesos de hardware en el que otros programadores se han vuelto ocupados.  
  
 `count`  
 El número de `IVirtualProcessorRoot` interfaces de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Es posible que un subproceso de hardware determinado que se asignará a los programadores varios al mismo tiempo. Un motivo para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima para todos los programadores sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no está utilizando, por medio de todas sus raíces de procesador virtual en ese subproceso del hardware que se está desactivando.  
  
 El nivel de suscripción de un subproceso de hardware se indica mediante el número de subprocesos subscritos y activado raíces de procesador virtual asociadas a ese subproceso del hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso del hardware es la parte de la suscripción que otros programadores contribuyen. Las notificaciones de que los recursos están externamente no disponibles se envían a un programador cuando el nivel de suscripción externo para un subproceso del hardware se mueve desde cero en territorio positivo.  
  
 Notificaciones a través de este método sólo se envían a los programadores que tienen una directiva donde el valor de la `MinConcurrency` clave de directiva es igual que el valor de la `MaxConcurrency` clave de directiva. Para obtener más información sobre las directivas de programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Un programador que califica las notificaciones Obtiene un conjunto de notificaciones iniciales cuando se crea, para informar de si los recursos sólo se asignó son externamente ocupado o inactivo.  
  
##  <a name="a-namenotifyresourcesexternallyidlea--ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>IScheduler:: NotifyResourcesExternallyIdle (método)  
 Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces de procesador virtual en la matriz `ppVirtualProcessorRoots` no están siendo utilizados por otros programadores.  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `ppVirtualProcessorRoots`  
 Una matriz de `IVirtualProcessorRoot` interfaces asociadas con los subprocesos de hardware en el que otros programadores se han vuelto inactivas.  
  
 `count`  
 El número de `IVirtualProcessorRoot` interfaces de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Es posible que un subproceso de hardware determinado que se asignará a los programadores varios al mismo tiempo. Un motivo para esto podría ser que no hay suficientes subprocesos de hardware en el sistema para satisfacer la simultaneidad mínima para todos los programadores sin compartir recursos. Otra posibilidad es que los recursos se asignen temporalmente a otros programadores cuando el programador propietario no está utilizando, por medio de todas sus raíces de procesador virtual en ese subproceso del hardware que se está desactivando.  
  
 El nivel de suscripción de un subproceso de hardware se indica mediante el número de subprocesos subscritos y activado raíces de procesador virtual asociadas a ese subproceso del hardware. Desde el punto de vista de un programador determinado, el nivel de suscripción externo de un subproceso del hardware es la parte de la suscripción que otros programadores contribuyen. Las notificaciones de que los recursos están externamente no disponibles se envían a un programador cuando el nivel de suscripción externo para un subproceso del hardware llega hasta cero desde un valor positivo anterior.  
  
 Notificaciones a través de este método sólo se envían a los programadores que tienen una directiva donde el valor de la `MinConcurrency` clave de directiva es igual que el valor de la `MaxConcurrency` clave de directiva. Para obtener más información sobre las directivas de programador, consulte [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Un programador que califica las notificaciones Obtiene un conjunto de notificaciones iniciales cuando se crea, para informar de si los recursos sólo se asignó son externamente ocupado o inactivo.  
  
##  <a name="a-nameremovevirtualprocessorsa--ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler:: RemoveVirtualProcessors (método)  
 Inicia la eliminación de raíces de procesador virtual que se asignaron previamente a este programador.  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `ppVirtualProcessorRoots`  
 Una matriz de `IVirtualProcessorRoot` interfaces que representan las raíces de procesador virtual va a quitar.  
  
 `count`  
 El número de `IVirtualProcessorRoot` interfaces de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 El Administrador de recursos invoca el `RemoveVirtualProcessors` método para recuperar un conjunto de raíces de procesador virtual de un programador. El programador debe invocar el [quitar](iexecutionresource-structure.md#remove) método en cada interfaz cuando se hace con las raíces de procesador virtual. No use un `IVirtualProcessorRoot` interfaz una vez que ha invocado la `Remove` método en él.  
  
 El parámetro `ppVirtualProcessorRoots` apunta a una matriz de interfaces. Entre el conjunto de raíces de procesador virtual que se va a quitar, las raíces no se han activado nunca se pueden devolver inmediatamente mediante el `Remove` (método). Las raíces que se han activado y son ejecutar el trabajo o se hayan desactivado y están esperando a que llegue trabajo, se deben devolver de forma asincrónica. El programador debe hacer todo lo posible para quitar la raíz del procesador virtual tan pronto como sea posible. Retraso en la eliminación de las raíces de procesador virtual puede producir la suscripción excesiva involuntaria dentro del programador.  
  
##  <a name="a-namestatisticsa--ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler:: Statistics (método)  
 Proporciona información relacionada con tasas de llegada y finalización de la tarea y el cambio de longitud de cola para un programador.  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pTaskCompletionRate`  
 El número de tareas que se han completado el programador desde la última llamada a este método.  
  
 `pTaskArrivalRate`  
 El número de tareas que han llegado al programador desde la última llamada a este método.  
  
 `pNumberOfTasksEnqueued`  
 El número total de tareas en todas las colas del programador.  
  
### <a name="remarks"></a>Comentarios  
 Este método se invoca el Administrador de recursos para recopilar las estadísticas para un programador. Las estadísticas que se recopilan aquí se usará para los algoritmos de comentario dinámicos para determinar cuándo es adecuado asignar más recursos al programador y cuándo se deben quitar recursos de la unidad. Los valores proporcionados por el programador pueden ser optimistas y no tienen necesariamente que refleja el recuento actual de forma precisa.  
  
 Debe implementar este método si desea que el Administrador de recursos Utilice comentarios sobre aspectos tales como la llegada de la tarea para determinar cómo equilibrar los recursos entre su programador y otros programadores registrados con el Administrador de recursos. Si decide no recopilar las estadísticas, puede establecer la clave de directiva `DynamicProgressFeedback` en el valor `DynamicProgressFeedbackDisabled` en la directiva de su programador y el recurso, el administrador no invocará este método en su programador.  
  
 En ausencia de información estadística, el Administrador de recursos usará los niveles de suscripción de subproceso de hardware para tomar decisiones de migración y asignación de recursos. Para obtener más información sobre niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [PolicyElementKey (enumeración)](concurrency-namespace-enums.md)   
 [SchedulerPolicy (clase)](schedulerpolicy-class.md)   
 [IExecutionContext (estructura)](iexecutioncontext-structure.md)   
 [IThreadProxy (estructura)](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)   
 [IResourceManager (estructura)](iresourcemanager-structure.md)

