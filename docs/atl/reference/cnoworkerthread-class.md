---
title: CNoWorkerThread (clase)
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: fcd103283738ce7d573faa2fb1025ee2af642021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258499"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread (clase)

Utilice esta clase como argumento para el `MonitorClass` parámetro de plantilla a las clases de caché si desea deshabilitar el mantenimiento de la caché dinámica.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CNoWorkerThread
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Equivalente a no funcionales [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Equivalente a no funcionales [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Equivalente a no funcionales [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Equivalente a no funcionales [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Equivalente a no funcionales [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Equivalente a no funcionales [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Equivalente a no funcionales [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Comentarios

Esta clase proporciona la misma interfaz pública que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Esta interfaz se espera que los proporcione el `MonitorClass` parámetro de plantilla a las clases de la memoria caché.

Los métodos de esta clase se implementan para no hacer nada. Los métodos que devuelven un HRESULT siempre devuelven S_OK y los métodos que devuelven un identificador de subproceso o identificador siempre devuelven 0.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

Equivalente a no funcionales [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

Equivalente a no funcionales [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

Equivalente a no funcionales [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve NULL.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

Equivalente a no funcionales [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

Equivalente a no funcionales [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

Equivalente a no funcionales [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

Equivalente a no funcionales [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

La implementación proporcionada por esta clase no hace nada.
