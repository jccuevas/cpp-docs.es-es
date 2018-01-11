---
title: IExecutionResource (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs: C++
helpviewer_keywords: IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd22fdb38b1828e1fa86ca79b9967a546ccb9456
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[IExecutionResource:: CurrentSubscriptionLevel](#currentsubscriptionlevel)|Devuelve el número de procesador virtual activadas raíces y suscrito subprocesos externos actualmente asociados a este recurso de ejecución representa el subproceso del hardware subyacente.|  
|[IExecutionResource:: GetExecutionResourceId](#getexecutionresourceid)|Devuelve un identificador único para el subproceso del hardware que representa este recurso de ejecución.|  
|[IExecutionResource:: GetNodeId](#getnodeid)|Devuelve un identificador único para el nodo del procesador que pertenece este recurso de ejecución.|  
|[IExecutionResource:: Remove](#remove)|Devuelve este recurso de ejecución para el Administrador de recursos.|  
  
## <a name="remarks"></a>Comentarios  
 Recursos de ejecución pueden ser independientes o asociados a raíces del procesador virtual. Se crea un recurso de ejecución independiente cuando un subproceso en la aplicación crea una suscripción del subproceso. Los métodos [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) y [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) crean suscripciones del subproceso y devuelven un `IExecutionResource` interfaz que representa la suscripción. Crear una suscripción del subproceso es una manera de informar al administrador de recursos que un subproceso determinado participará en el trabajo en cola a un programador, junto con las raíces de procesador virtual en el Administrador de recursos asigna al programador. El Administrador de recursos usa la información para evitar la sobresuscripción de subprocesos de hardware siempre sea posible.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IExecutionResource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="currentsubscriptionlevel"></a>IExecutionResource:: CurrentSubscriptionLevel (método)  
 Devuelve el número de procesador virtual activadas raíces y suscrito subprocesos externos actualmente asociados a este recurso de ejecución representa el subproceso del hardware subyacente.  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nivel de suscripción actual.  
  
### <a name="remarks"></a>Comentarios  
 El nivel de suscripción le indica cuántos subprocesos en ejecución están asociados con el subproceso de hardware. Esto incluye solo el Administrador de recursos es consciente de en el formulario de subprocesos subscritos y raíces de procesador virtual que están ejecutando activamente los proxy del subproceso de subprocesos.  
  
 Llamar al método [ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), o el método [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) con el parámetro `doSubscribeCurrentThread` establecido en el valor `true`incrementa el nivel de suscripción de un subproceso de hardware en uno. Asimismo, devuelven un `IExecutionResource` interfaz que representa la suscripción. Una llamada correspondiente a la [IExecutionResource:: Remove](#remove) disminuye nivel de suscripción del subproceso de hardware por uno.  
  
 El hecho de activar una raíz del procesador virtual mediante el método [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) incrementa el nivel de suscripción de un subproceso de hardware en uno. Los métodos [IVirtualProcessorRoot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate), o [IExecutionResource:: Remove](#remove) disminuir el nivel de suscripción en uno cuando se invoca en una raíz de procesador virtual activada.  
  
 El Administrador de recursos usa información de nivel de suscripción como una de las maneras en que se va a determinar cuándo se debe mover recursos entre los programadores.  
  
##  <a name="getexecutionresourceid"></a>IExecutionResource:: GetExecutionResourceId (método)  
 Devuelve un identificador único para el subproceso del hardware que representa este recurso de ejecución.  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador único para el subproceso del hardware subyacente de este recurso de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Cada subproceso del hardware tiene asignado un identificador único por el Runtime de simultaneidad. Si varios recursos de ejecución están asociado hardware subproceso, todos tendrán el mismo identificador de recurso de ejecución.  
  
##  <a name="getnodeid"></a>IExecutionResource:: GetNodeId (método)  
 Devuelve un identificador único para el nodo del procesador que pertenece este recurso de ejecución.  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador único para un nodo del procesador.  
  
### <a name="remarks"></a>Comentarios  
 El Runtime de simultaneidad representa subprocesos de hardware en el sistema en grupos de nodos de procesador. Nodos normalmente se derivan de la topología del hardware del sistema. Por ejemplo, todos los procesadores en un socket concreto o un nodo NUMA concreto pueden pertenecer al mismo nodo de procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluyendo `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador en el sistema.  
  
 Se puede obtener el recuento de nodos de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).  
  
##  <a name="remove"></a>IExecutionResource:: Remove (método)  
 Devuelve este recurso de ejecución para el Administrador de recursos.  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pScheduler`  
 Una interfaz al programador que realiza la solicitud para quitar este recurso de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para devolver los recursos de ejecución independientes, así como recursos de ejecución asociados a raíces del procesador virtual para el Administrador de recursos.  
  
 Si se trata de un recurso de ejecución independiente que recibió de cualquiera de los métodos [ISchedulerProxy:: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) o [ISchedulerProxy:: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), la llamada a la método `Remove` finalizará la suscripción del subproceso que el recurso se creó para representar. Se deben finalizar todas las suscripciones de subproceso antes de cerrar un proxy del programador y debe llamar a `Remove` desde el subproceso que creó la suscripción.  
  
 Raíces de procesador virtual, también, pueden devolverse al administrador de recursos invocando el `Remove` método, porque la interfaz `IVirtualProcessorRoot` hereda de la `IExecutionResource` interfaz. Puede que necesite devolver una raíz del procesador virtual en respuesta a una llamada a la [IScheduler:: RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) método, o cuando haya terminado con una raíz de la suscripción excesiva de procesador virtual que obtuvo en el [ ISchedulerProxy:: CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber) método. Para las raíces de procesador virtual, no hay ninguna restricción en el subproceso puede invocar el `Remove` método.  
  
 `invalid_argument`se produce si el parámetro `pScheduler` está establecido en `NULL`.  
  
 `invalid_operation`se produce si el parámetro `pScheduler` es distinta del programador que se creó este recurso de ejecución para, o bien, con un recurso de ejecución independiente, si el subproceso actual es diferente del subproceso que creó la suscripción del subproceso.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)
