---
title: CNonStatelessWorker (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb3b6411e9ce34ba0196d25c8a63f3f066d78549
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765127"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker (clase)

Recibe solicitudes de un grupo de subprocesos y los pasa a un objeto de trabajo que se crea y destruye en cada solicitud.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class Worker>  
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parámetros

*Trabajo*  
Una clase de subproceso de trabajo que cumplen el [worker (Arquetipo)](../../atl/reference/worker-archetype.md) adecuado para controlar las solicitudes en cola en [CThreadPool](../../atl/reference/cthreadpool-class.md).

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

Esta clase es un subproceso de trabajo simple para su uso con [CThreadPool](../../atl/reference/cthreadpool-class.md). Esta clase no proporciona ninguna funcionalidad de tratamiento de solicitudes de su propio. En su lugar, crea una instancia de una instancia de *trabajo* por solicitud y delega la implementación de sus métodos para esa instancia.

La ventaja de esta clase es que proporciona una manera cómoda de cambiar el modelo de estado de las clases de subproceso de trabajo existentes. `CThreadPool` creará un trabajo único para la duración del subproceso, por lo que si la clase de trabajo contiene el estado, mantenga en varias solicitudes. Simplemente encapsulando esa clase en el `CNonStatelessWorker` plantilla antes de usarlo con `CThreadPool`, la duración del trabajador y el estado contiene se limita a una única solicitud.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).  

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Comentarios

Este método crea una instancia de la *trabajo* clase en la pila y llama a [inicializar](worker-archetype.md#initialize) en ese objeto. Si la inicialización es correcta, este método también llama a [Execute](worker-archetype.md#execute) y [Terminate](worker-archetype.md#terminate) en el mismo objeto.  

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Esta clase realizar cualquier inicialización `Initialize`.

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Comentarios

Esta clase controla el mismo tipo de elemento de trabajo que la clase utilizada para la *trabajo* parámetro de plantilla. Consulte [CNonStatelessWorker Introducción](../../atl/reference/cnonstatelessworker-class.md) para obtener más información.

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Comentarios

Esta clase no realiza las operaciones de limpieza `Terminate`.

## <a name="see-also"></a>Vea también

[CThreadPool (clase)](../../atl/reference/cthreadpool-class.md)   
[Worker (Arquetipo)](../../atl/reference/worker-archetype.md)   
[Clases](../../atl/reference/atl-classes.md)
