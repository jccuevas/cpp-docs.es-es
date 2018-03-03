---
title: Clase CNonStatelessWorker | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs:
- C++
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 565324b4853880f8dcfafd83f9ba03439b4a7efa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cnonstatelessworker-class"></a>Clase CNonStatelessWorker
Recibe solicitudes de un grupo de subprocesos y los pasa a un objeto de trabajo que se crea y se destruye en cada solicitud.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>Parámetros  
 *Trabajo*  
 Una clase de subproceso de trabajo que cumplen la [Arquetipo trabajo](../../atl/reference/worker-archetype.md) adecuado para controlar las solicitudes en cola en [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).|  
|[CNonStatelessWorker::Initialize](#initialize)|Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).|  
|[CNonStatelessWorker::Terminate](#terminate)|Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es un subproceso de trabajo simple para su uso con [CThreadPool](../../atl/reference/cthreadpool-class.md). Esta clase no proporciona las capacidades de control de la solicitud de su propio. En su lugar, crea una instancia de una instancia de *trabajo* por solicitud y delega la implementación de sus métodos para esa instancia.  
  
 La ventaja de esta clase es que proporciona una manera cómoda de cambiar el modelo de estado para las clases de subprocesos de trabajo existentes. `CThreadPool`se creará un solo proceso de trabajo para la duración del subproceso, por lo que si la clase de trabajo contiene el estado, mantenga en varias solicitudes. Ajustando simplemente dicha clase en el `CNonStatelessWorker` plantilla antes de usarlo con `CThreadPool`, la duración del trabajador y el estado contiene se limita a una única solicitud.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="execute"></a>CNonStatelessWorker::Execute  
 Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una instancia de la *trabajo* clase en la pila y la llama [inicializar](worker-archetype.md#initialize) en ese objeto. Si la inicialización se realiza correctamente, este método también llama [Execute](worker-archetype.md#execute) y [Terminate](worker-archetype.md#terminate) en el mismo objeto.  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no lleva a cabo cualquier tarea de inicialización `Initialize`.  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase administra el mismo tipo de elemento de trabajo que la clase utilizada para la *trabajo* parámetro de plantilla. Vea [CNonStatelessWorker Introducción](../../atl/reference/cnonstatelessworker-class.md) para obtener más información.  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no las operaciones de limpieza en `Terminate`.  
  
## <a name="see-also"></a>Vea también  
 [CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)   
 [Arquetipo de trabajo](../../atl/reference/worker-archetype.md)   
 [Clases](../../atl/reference/atl-classes.md)
