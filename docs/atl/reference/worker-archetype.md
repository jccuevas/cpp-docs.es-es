---
title: Arquetipo de trabajo
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 3efd77c38508df8302fa4e1dd5c9b51f66cd5e43
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915463"
---
# <a name="worker-archetype"></a>Arquetipo de trabajo

Las clases que cumplen con el arquetipo de *trabajo* proporcionan el código para procesar los elementos de trabajo en cola en un grupo de subprocesos.

**Implementación**

Para implementar una clase que se ajuste a este arquetipo, la clase debe proporcionar las siguientes características:

|Método|DESCRIPCIÓN|
|------------|-----------------|
|[Initialize](#initialize)|Se llama para inicializar el objeto de trabajo antes de que se pasen solicitudes a [EXECUTE](#execute).|
|[Execute](#execute)|Se llama para procesar un elemento de trabajo.|
|[Terminate](#terminate)|Se llama para anular la inicialización del objeto de trabajo después de que se hayan pasado todas las solicitudes a [EXECUTE](#execute).|

|Definición de tipo|DESCRIPCIÓN|
|-------------|-----------------|
|[RequestType](#requesttype)|Definición de tipos para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.|

Una clase de *trabajo* típica tiene el siguiente aspecto:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Implementaciones existentes**

Estas clases son compatibles con este arquetipo:

|Clase|DESCRIPCIÓN|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes del grupo de subprocesos y las pasa a un objeto de trabajo que se crea y se destruye para cada solicitud.|

**Uso**

Estos parámetros de plantilla esperan que la clase se ajuste a este arquetipo:

|Nombre de parámetro|Utilizada por|
|--------------------|-------------|
|*Trabajo*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Trabajo*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

## <a name="execute"></a>WorkerArchetype::Execute

Se llama para procesar un elemento de trabajo.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parámetros

*request*<br/>
El elemento de trabajo que se va a procesar. El elemento de trabajo es del mismo tipo que `RequestType`.

*pvWorkerParam*<br/>
Un parámetro personalizado que entiende la clase de trabajo. También se pasa `WorkerArchetype::Initialize` a `Terminate`y.

*pOverlapped*<br/>
Puntero a la estructura [superpuesta](/windows/desktop/api/minwinbase/ns-minwinbase-overlapped) utilizada para crear la cola en la que se pusieron en cola los elementos de trabajo.

## <a name="initialize"></a> WorkerArchetype::Initialize

Se llama para inicializar el objeto de trabajo antes de que `WorkerArchetype::Execute`se pasen solicitudes a.
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parámetros

*pvParam*<br/>
Un parámetro personalizado que entiende la clase de trabajo. También se pasa `WorkerArchetype::Terminate` a `WorkerArchetype::Execute`y.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

## <a name="requesttype"></a> WorkerArchetype::RequestType

Definición de tipos para el tipo de elemento de trabajo que puede ser procesado por la clase de trabajo.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Comentarios

Este tipo se debe utilizar como primer parámetro de `WorkerArchetype::Execute` y debe ser capaz de convertirse a y desde un ULONG_PTR.

## <a name="terminate"></a> WorkerArchetype::Terminate

Se llama para anular la inicialización del objeto de trabajo después de que `WorkerArchetype::Execute`se hayan pasado todas las solicitudes a).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parámetros

*pvParam*<br/>
Un parámetro personalizado que entiende la clase de trabajo. También se pasa `WorkerArchetype::Initialize` a `WorkerArchetype::Execute`y.

## <a name="see-also"></a>Vea también

[Conceptos](../../atl/active-template-library-atl-concepts.md)<br/>
[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
