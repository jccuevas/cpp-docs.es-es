---
title: Clase CNonStatelessWorker
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 6264bb6bc9070b5ce170b294f9db0d371e7b6b71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747666"
---
# <a name="cnonstatelessworker-class"></a>Clase CNonStatelessWorker

Recibe solicitudes de un grupo de subprocesos y las pasa a un objeto de trabajo que se crea y destruye en cada solicitud.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parámetros

*Trabajador*<br/>
Una clase de subproceso de trabajo que se ajusta al [arquetipo](../../atl/reference/worker-archetype.md) de trabajo adecuado para controlar las solicitudes en cola en [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CNonStatelessWorker::Ejecutar](#execute)|Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialize](#initialize)|Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Terminate](#terminate)|Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Observaciones

Esta clase es un subproceso de trabajo simple para su uso con [CThreadPool](../../atl/reference/cthreadpool-class.md). Esta clase no proporciona ninguna capacidad de control de solicitudes propia. En su lugar, crea una instancia de *Worker* por solicitud y delega la implementación de sus métodos en esa instancia.

La ventaja de esta clase es que proporciona una manera conveniente de cambiar el modelo de estado para las clases de subproceso de trabajo existentes. `CThreadPool`creará un único trabajador durante la duración del subproceso, por lo que si la clase de trabajo tiene estado, lo retendrá en varias solicitudes. Simplemente ajustando esa `CNonStatelessWorker` clase en `CThreadPool`la plantilla antes de usarla con , la duración del trabajador y el estado que contiene se limita a una sola solicitud.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>CNonStatelessWorker::Ejecutar

Implementación de [WorkerArchetype::Execute](worker-archetype.md#execute).

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Observaciones

Este método crea una instancia de la *clase Worker* en la pila y llama a [Initialize](worker-archetype.md#initialize) en ese objeto. Si la inicialización se realiza correctamente, este método también llama [a Execute](worker-archetype.md#execute) y [Terminate](worker-archetype.md#terminate) en el mismo objeto.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>CNonStatelessWorker::Initialize

Implementación de [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Esta clase no realiza `Initialize`ninguna inicialización en .

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>CNonStatelessWorker::RequestType

Implementación de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Observaciones

Esta clase controla el mismo tipo de elemento de trabajo que la clase utilizada para el parámetro de plantilla *Worker.* Consulte Información general sobre [CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) para obtener más información.

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>CNonStatelessWorker::Terminate

Implementación de [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Observaciones

Esta clase no realiza `Terminate`ninguna limpieza en .

## <a name="see-also"></a>Vea también

[Clase CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Arquetipo de trabajador](../../atl/reference/worker-archetype.md)<br/>
[Clases](../../atl/reference/atl-classes.md)
