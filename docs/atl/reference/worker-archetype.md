---
title: Arquetipo de trabajador
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: c9ed9b30b94a8debe133bc213c12063750bfb15a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747347"
---
# <a name="worker-archetype"></a>Arquetipo de trabajador

Las clases que se ajustan al arquetipo de *trabajo* proporcionan el código para procesar los elementos de trabajo en cola en un grupo de subprocesos.

**Implementación**

Para implementar una clase que se ajuste a este arquetipo, la clase debe proporcionar las siguientes características:

|Método|Descripción|
|------------|-----------------|
|[Initialize](#initialize)|Se llama para inicializar el objeto de trabajo antes de que se pasen las solicitudes a [Execute](#execute).|
|[Ejecutar](#execute)|Se llama para procesar un elemento de trabajo.|
|[Terminate](#terminate)|Se llama para anular la inicialización del objeto de trabajo después de que se hayan pasado todas las solicitudes a [Execute](#execute).|

|Definición de tipos|Descripción|
|-------------|-----------------|
|[RequestType](#requesttype)|Una propiedad typedef para el tipo de elemento de trabajo que puede procesar la clase de trabajo.|

Una clase *de trabajador* típica tiene este aspecto:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Implementaciones existentes**

Estas clases se ajustan a este arquetipo:

|Clase|Descripción|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes del grupo de subprocesos y las pasa a un objeto de trabajo que se crea y destruye para cada solicitud.|

**Uso**

Estos parámetros de plantilla esperan que la clase se ajuste a este arquetipo:

|Nombre de parámetro|Usado por|
|--------------------|-------------|
|*Trabajador*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Trabajador*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Ejecutar

Se llama para procesar un elemento de trabajo.

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parámetros

*Solicitud*<br/>
El elemento de trabajo que se va a procesar. El elemento de trabajo es `RequestType`del mismo tipo que .

*pvWorkerParam*<br/>
Un parámetro personalizado entendido por la clase de trabajo. También pasó `WorkerArchetype::Initialize` `Terminate`a y .

*pOverlapped*<br/>
Puntero a la estructura [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilizada para crear la cola en la que se ponen en cola los elementos de trabajo.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialize

Se llama para inicializar el objeto de `WorkerArchetype::Execute`trabajo antes de que se pasen las solicitudes a .

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parámetros

*pvParam*<br/>
Un parámetro personalizado entendido por la clase de trabajo. También pasó `WorkerArchetype::Terminate` `WorkerArchetype::Execute`a y .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType

Una propiedad typedef para el tipo de elemento de trabajo que puede procesar la clase de trabajo.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Observaciones

Este tipo debe utilizarse como `WorkerArchetype::Execute` primer parámetro de y debe ser capaz de ser lanzado a y desde un ULONG_PTR.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Terminate

Se llama para anular la inicialización del `WorkerArchetype::Execute`objeto de trabajo después de que se hayan pasado todas las solicitudes a ).

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parámetros

*pvParam*<br/>
Un parámetro personalizado entendido por la clase de trabajo. También pasó `WorkerArchetype::Initialize` `WorkerArchetype::Execute`a y .

## <a name="see-also"></a>Vea también

[Conceptos](../../atl/active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
