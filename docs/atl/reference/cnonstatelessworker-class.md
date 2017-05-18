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
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 804b87bf752aac5cecf64cb61b4d53d6269963f2
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cnonstatelessworker-class"></a>Clase CNonStatelessWorker
Recibe solicitudes de un grupo de subprocesos y pasa un objeto de trabajo que se crea y se destruye en cada solicitud.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>Parámetros  
 *Trabajo*  
 Una clase de subproceso de trabajo que se ajuste a la [Arquetipo de trabajo](../../atl/reference/worker-archetype.md) adecuado para controlar las solicitudes en cola en [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).|  
|[CNonStatelessWorker::Initialize](#initialize)|Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).|  
|[CNonStatelessWorker::Terminate](#terminate)|Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es un subproceso de trabajo simple para su uso con [CThreadPool](../../atl/reference/cthreadpool-class.md). Esta clase no proporciona las capacidades de control de la solicitud de su propio. En su lugar, crea una instancia de una instancia de *trabajo* por solicitud y delega la implementación de sus métodos para esa instancia.  
  
 La ventaja de esta clase es que proporciona una manera cómoda de cambiar el modelo de estado para las clases de subprocesos de trabajo existentes. `CThreadPool`Cree un trabajo único para la duración del subproceso, por lo que si la clase de trabajo contiene el estado, mantenga en varias solicitudes. Simplemente ajustando dicha clase en el `CNonStatelessWorker` plantilla antes de utilizarlo con `CThreadPool`, la duración del trabajador y el estado que contiene se limita a una única solicitud.  
  
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
 Este método crea una instancia de la *trabajo* (clase) en la pila y llama a [inicializar](worker-archetype.md#initialize) en ese objeto. Si la inicialización se realiza correctamente, este método también llama a [Execute](worker-archetype.md#execute) y [Terminate](worker-archetype.md#terminate) en el mismo objeto.  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase realizar cualquier inicialización `Initialize`.  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase administra el mismo tipo de elemento de trabajo que la clase utilizada para la *trabajo* parámetro de plantilla. Consulte [CNonStatelessWorker Introducción](../../atl/reference/cnonstatelessworker-class.md) para obtener más información.  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no lleva a cabo las operaciones de limpieza `Terminate`.  
  
## <a name="see-also"></a>Vea también  
 [CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)   
 [Arquetipo de trabajo](../../atl/reference/worker-archetype.md)   
 [Clases](../../atl/reference/atl-classes.md)

