---
title: ISchedulerProxy (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 3dd95150022ad94f50b456c84f7dacd2d3cef7c5
ms.lasthandoff: 03/17/2017

---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy (Estructura)
La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ISchedulerProxy:: BindContext](#bindcontext)|Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.|  
|[ISchedulerProxy:: CreateOversubscriber](#createoversubscriber)|Crea una nueva raíz del procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.|  
|[ISchedulerProxy:: RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad para ejecutar un subproceso que puede realizar el trabajo para el programador.|  
|[ISchedulerProxy:: Shutdown](#shutdown)|Notifica al administrador de recursos que se está cerrando el programador. Esto hará que el Administrador de recursos reclame inmediatamente todos los recursos concedidos al programador.|  
|[ISchedulerProxy:: SubscribeCurrentThread](#subscribecurrentthread)|El subproceso actual se registra con el Administrador de recursos, asociarla a este programador.|  
|[ISchedulerProxy:: UnbindContext](#unbindcontext)|Desasocia un proxy del subproceso del contexto de ejecución especificado por el `pContext` parámetro y lo devuelve al grupo libre del generador de proxy de subproceso. Sólo se llama a este método en un contexto de ejecución que se enlazó a través de la [BindContext](#bindcontext) método y aún no se ha iniciado en el que se va a la `pContext` parámetro de un [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) llamada al método.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de recursos pasa una `ISchedulerProxy` interfaz a cada programador que se registra con él mediante el [IResourceManager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) método.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="bindcontext"></a>ISchedulerProxy:: BindContext (método)  
 Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 Una interfaz al contexto de ejecución para asociar a un proxy del subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, el [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) método enlazará un proxy del subproceso a un contexto de ejecución a petición. Sin embargo, hay circunstancias donde es necesario enlazar un contexto de antemano para asegurarse de que el `SwitchTo` método activa en un contexto ya enlazado. Este es el caso en un contexto de programación, no puede llamar a métodos que asignan memoria UMS y enlace a un proxy del subproceso puede implicar la asignación de memoria si un proxy del subproceso no está disponible en el grupo libre del generador de proxy de subproceso.  
  
 `invalid_argument`se produce si el parámetro `pContext` tiene el valor `NULL`.  
  
##  <a name="createoversubscriber"></a>ISchedulerProxy:: CreateOversubscriber (método)  
 Crea una nueva raíz del procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pExecutionResource`  
 Un `IExecutionResource` interfaz que representa el subproceso del hardware que desea suscribir en exceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Interfaz `IVirtualProcessorRoot`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método cuando su programador desee realizar suscripciones excesivas de un subproceso de hardware determinado durante un período limitado de tiempo. Una vez que haya terminado con la raíz del procesador virtual, debe devolverlo al administrador de recursos mediante una llamada a la [quitar](iexecutionresource-structure.md#remove) método en el `IVirtualProcessorRoot` interfaz.  
  
 Incluso puede saturar una raíz del procesador virtual existente, porque la `IVirtualProcessorRoot` interfaz se hereda de la `IExecutionResource` interfaz.  
  
##  <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: RequestInitialVirtualProcessors (método)  
 Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad para ejecutar un subproceso que puede realizar el trabajo para el programador.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `doSubscribeCurrentThread`  
 Si desea suscribirse el subproceso actual y cuenta para ello durante la asignación de recursos.  
  
### <a name="return-value"></a>Valor devuelto  
 El `IExecutionResource` de interfaz para el subproceso actual, si el parámetro `doSubscribeCurrentThread` tiene el valor `true`. Si el valor es `false`, el método devuelve `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Antes de que un programador ejecute cualquier trabajo, debe utilizar este método para solicitar raíces de procesador virtual del Administrador de recursos. El Administrador de recursos tendrá acceso a la directiva del programador mediante [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) y utilizar los valores de las claves de directiva `MinConcurrency`, `MaxConcurrency` y `TargetOversubscriptionFactor` para determinar cuántos subprocesos de hardware que se asigna inicialmente al programador y cuántas raíces del procesador virtual para crear para cada subproceso de hardware. Para obtener más información sobre cómo se usan las directivas del programador para determinar la asignación inicial de un programador, consulte [PolicyElementKey](concurrency-namespace-enums.md).  
  
 El Administrador de recursos concede recursos a un programador llamando al método [IScheduler:: AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) con una lista de raíces de procesador virtual. El método se invoca como una devolución de llamada en el programador antes de que este método devuelve.  
  
 Si el programador solicitado la suscripción para el subproceso actual estableciendo el parámetro `doSubscribeCurrentThread` a `true`, el método devuelve un `IExecutionResource` interfaz. La suscripción se debe finalizar en un momento posterior utilizando la [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) método.  
  
 Al determinar qué subprocesos de hardware están seleccionados, el Administrador de recursos intentará optimizar la afinidad de nodo del procesador. Si la suscripción se solicita para el subproceso actual, es una indicación de que el subproceso actual piensa participar en el trabajo asignado a este programador. En tal caso, las raíces de procesadores virtuales asignados se encuentran en el nodo de procesador que se está ejecutando el subproceso actual, si es posible.  
  
 La acción de suscribir un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente por uno. El nivel de suscripción se reduce en uno cuando finaliza la suscripción. Para obtener más información sobre niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>ISchedulerProxy:: Shutdown (método)  
 Notifica al administrador de recursos que se está cerrando el programador. Esto hará que el Administrador de recursos reclame inmediatamente todos los recursos concedidos al programador.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Todos los `IExecutionContext` el programador recibido como resultado de suscribir un subproceso externo mediante los métodos de interfaces `ISchedulerProxy::RequestInitialVirtualProcessors` o `ISchedulerProxy::SubscribeCurrentThread` debe devolverse al administrador de recursos mediante `IExecutionResource::Remove` antes de que un programador se apaga.  
  
 Si su programador tuviera alguna desactivado raíces de procesador virtual, debe activarlos mediante [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)y tiene los proxy de subprocesos que se ejecutan en estos deje el `Dispatch` método de los contextos de ejecución que están enviando antes de invocar `Shutdown` en un proxy del programador.  
  
 No es necesario que el programador individualmente devolver todas las raíces de procesador virtual en el Administrador de recursos concede a él a través de llamadas a la `Remove` método porque se devolverá todas las raíces de procesadores virtuales para el Administrador de recursos durante el apagado.  
  
##  <a name="subscribecurrentthread"></a>ISchedulerProxy:: SubscribeCurrentThread (método)  
 El subproceso actual se registra con el Administrador de recursos, asociarla a este programador.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `IExecutionResource` interfaz que representa el subproceso actual en el tiempo de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método si desea que el Administrador de recursos para tener en cuenta el subproceso actual mientras se asignan recursos a su programador y otros programadores. Es especialmente útil cuando el subproceso piensa participar en el trabajo en la cola del programador, junto con las raíces de procesador virtual que el programador recibe del Administrador de recursos. El Administrador de recursos usa información para evitar innecesarias suscripciones excesivas de subprocesos de hardware en el sistema.  
  
 El recurso de ejecución recibido a través de este método debe devolverse al administrador de recursos mediante la [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) método. El subproceso que llama el `Remove` método debe ser el mismo subproceso que llamó anteriormente el `SubscribeCurrentThread` método.  
  
 La acción de suscribir un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente por uno. El nivel de suscripción se reduce en uno cuando finaliza la suscripción. Para obtener más información sobre niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>ISchedulerProxy:: UnbindContext (método)  
 Desasocia un proxy del subproceso del contexto de ejecución especificado por el `pContext` parámetro y lo devuelve al grupo libre del generador de proxy de subproceso. Sólo se llama a este método en un contexto de ejecución que se enlazó a través de la [BindContext](#bindcontext) método y aún no se ha iniciado en el que se va a la `pContext` parámetro de un [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) llamada al método.  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 El contexto de ejecución para desasociarlo de su proxy del subproceso.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IScheduler (estructura)](ischeduler-structure.md)   
 [IThreadProxy (estructura)](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)   
 [IResourceManager (estructura)](iresourcemanager-structure.md)

