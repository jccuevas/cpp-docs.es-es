---
title: ISchedulerProxy (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65198998666391763ef32a55cd12e86529e619ed
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693928"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy (Estructura)
La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.|  
|[ISchedulerProxy:: CreateOversubscriber](#createoversubscriber)|Crea una nueva raíz del procesador virtual en el subproceso de hardware asociado a un recurso de ejecución existente.|  
|[ISchedulerProxy:: RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad para ejecutar un subproceso que puede realizar el trabajo para el programador.|  
|[ISchedulerProxy:: Shutdown](#shutdown)|Notifica al administrador de recursos que el programador está cerrando. Esto hará que el Administrador de recursos del que recuperar inmediatamente todos los recursos concedidos al programador.|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Registra el subproceso actual con el Administrador de recursos, asociar a este programador.|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Desasocia un proxy del subproceso del contexto de ejecución especificado por el `pContext` parámetro y se devuelve al grupo de medios libres del generador de proxy de subproceso. Solo se puede llamar al método en un contexto de ejecución que se enlazó a través de la [ISchedulerProxy:: BindContext](#bindcontext) método y aún no se ha iniciado a través de que se va a la `pContext` parámetro de un [IThreadProxy:: SwitchTo ](ithreadproxy-structure.md#switchto) llamada al método.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de recursos entrega una `ISchedulerProxy` interfaz para cada programador que se registra con él mediante el [IResourceManager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) método.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="bindcontext"></a>  BindContext (método)  
 Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 Una interfaz al contexto de ejecución para asociar a un proxy del subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, el [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto) método enlazará un proxy del subproceso a un contexto de ejecución a petición. Sin embargo, hay circunstancias donde es necesario enlazar un contexto de antemano para asegurarse de que el `SwitchTo` método activa en un contexto ya enlazado. Este es el caso en un contexto de programación como que no puede llamar a métodos que asignan memoria UMS y enlace a un proxy del subproceso puede implicar la asignación de memoria si un proxy del subproceso no está disponible en el grupo libre del generador de proxy de subproceso.  
  
 `invalid_argument` se produce si el parámetro `pContext` tiene el valor `NULL`.  
  
##  <a name="createoversubscriber"></a>  ISchedulerProxy:: CreateOversubscriber (método)  
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
 Utilice este método cuando el programador desea suscribir en exceso un subproceso de hardware determinado durante un período limitado de tiempo. Cuando haya terminado con la raíz del procesador virtual, debe devolver al administrador de recursos mediante una llamada a la [quitar](iexecutionresource-structure.md#remove) método en el `IVirtualProcessorRoot` interfaz.  
  
 Incluso puede saturar una raíz del procesador virtual existente, porque la `IVirtualProcessorRoot` interfaz hereda de la `IExecutionResource` interfaz.  
  
##  <a name="requestinitialvirtualprocessors"></a>  ISchedulerProxy:: RequestInitialVirtualProcessors (método)  
 Solicita una asignación inicial de raíces de procesador virtual. Cada raíz del procesador virtual representa la capacidad para ejecutar un subproceso que puede realizar el trabajo para el programador.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `doSubscribeCurrentThread`  
 Si desea suscribirse el subproceso actual y tenerlo en cuenta durante la asignación de recursos.  
  
### <a name="return-value"></a>Valor devuelto  
 El `IExecutionResource` interfaz para el subproceso actual, si el parámetro `doSubscribeCurrentThread` tiene el valor `true`. Si el valor es `false`, el método devuelve `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Antes de que un programador ejecute cualquier trabajo, debe utilizar este método para solicitar raíces del procesador virtual desde el Administrador de recursos. El Administrador de recursos tendrá acceso a la directiva del programador mediante [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) y usar los valores de las claves de directiva `MinConcurrency`, `MaxConcurrency` y `TargetOversubscriptionFactor` para determinar cuántos subprocesos de hardware para asignar a la programador inicialmente y cuántas raíces de procesador virtual para crear para cada subproceso del hardware. Para obtener más información sobre cómo se usan las directivas del programador para determinar la asignación inicial del programador, consulte [PolicyElementKey](concurrency-namespace-enums.md).  
  
 El Administrador de recursos concede recursos a un programador llamando al método [IScheduler:: AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) con una lista de raíces de procesador virtual. Se invoca el método como una devolución de llamada en el programador antes de que este método devuelve.  
  
 Si el programador solicita suscripción para el subproceso actual, establezca el parámetro `doSubscribeCurrentThread` a `true`, el método devuelve un `IExecutionResource` interfaz. La suscripción se debe terminar en un momento posterior usando el [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) método.  
  
 Al determinar qué subprocesos de hardware están seleccionados, el Administrador de recursos intentará optimizar para afinidad de nodo del procesador. Si se solicita la suscripción para el subproceso actual, es una indicación de que el subproceso actual tiene intención de participar en el trabajo asignado a este programador. En tal caso, las raíces de procesadores virtuales asignados se encuentran en el nodo de procesador que se está ejecutando el subproceso actual, si es posible.  
  
 El hecho de suscribirse a un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente por uno. El nivel de suscripción se reduce en uno cuando finaliza la suscripción. Para obtener más información sobre los niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>  ISchedulerProxy:: Shutdown (método)  
 Notifica al administrador de recursos que el programador está cerrando. Esto hará que el Administrador de recursos del que recuperar inmediatamente todos los recursos concedidos al programador.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Todos los `IExecutionContext` interfaces el programador recibido como resultado de suscribir un subproceso externo mediante los métodos `ISchedulerProxy::RequestInitialVirtualProcessors` o `ISchedulerProxy::SubscribeCurrentThread` debe devolverse al administrador de recursos mediante `IExecutionResource::Remove` antes de que un programador apaga.  
  
 Si su programador tuviera alguna desactivado raíces del procesador virtual, debe activarlos mediante [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)y tiene el proxy del subproceso se ejecuta en ellos deje el `Dispatch` método de la ejecución contextos que están enviando antes de invocar a `Shutdown` en un proxy del programador.  
  
 No es necesario para el programador para individualmente devolver todas las raíces de procesador virtual en el Administrador de recursos que se conceden a él a través de llamadas a la `Remove` método porque se devolverá todas las raíces de procesadores virtuales para el Administrador de recursos al apagar el equipo.  
  
##  <a name="subscribecurrentthread"></a>  ISchedulerProxy:: SubscribeCurrentThread (método)  
 Registra el subproceso actual con el Administrador de recursos, asociar a este programador.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `IExecutionResource` crea una interfaz que representa el subproceso actual en el tiempo de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método si desea que el Administrador de recursos para tener en cuenta el subproceso actual mientras se asignan recursos a su programador y otros programadores. Es especialmente útil cuando el subproceso piensa participar en el trabajo en cola para su programador, junto con las raíces de procesador virtual que el programador recibe desde el Administrador de recursos. El Administrador de recursos usa información para evitar innecesarias suscripciones excesivas de subprocesos de hardware en el sistema.  
  
 El recurso de ejecución recibido a través de este método se debe devolver al administrador de recursos mediante el [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) método. El subproceso que llama el `Remove` método debe ser el mismo subproceso que llamó previamente el `SubscribeCurrentThread` método.  
  
 El hecho de suscribirse a un subproceso aumenta el nivel de suscripción del subproceso de hardware subyacente por uno. El nivel de suscripción se reduce en uno cuando finaliza la suscripción. Para obtener más información sobre los niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>  ISchedulerProxy:: UnbindContext (método)  
 Desasocia un proxy del subproceso del contexto de ejecución especificado por el `pContext` parámetro y se devuelve al grupo de medios libres del generador de proxy de subproceso. Solo se puede llamar al método en un contexto de ejecución que se enlazó a través de la [ISchedulerProxy:: BindContext](#bindcontext) método y aún no se ha iniciado a través de que se va a la `pContext` parámetro de un [IThreadProxy:: SwitchTo ](ithreadproxy-structure.md#switchto) llamada al método.  
  
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
