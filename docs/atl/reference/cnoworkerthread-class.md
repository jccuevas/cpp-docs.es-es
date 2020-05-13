---
title: Clase CNoWorkerThread
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
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326709"
---
# <a name="cnoworkerthread-class"></a>Clase CNoWorkerThread

Utilice esta clase como `MonitorClass` argumento para que el parámetro template almacene en caché las clases si desea deshabilitar el mantenimiento dinámico de la memoria caché.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CNoWorkerThread
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Equivalente no funcional de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Equivalente no funcional de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Equivalente no funcional de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Equivalente no funcional de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Equivalente no funcional de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Equivalente no funcional de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Equivalente no funcional de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Observaciones

Esta clase proporciona la misma interfaz pública que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Se espera que el `MonitorClass` parámetro de plantilla proporcione esta interfaz para almacenar en caché las clases.

Los métodos de esta clase se implementan para no hacer nada. Los métodos que devuelven un HRESULT siempre devuelven S_OK y los métodos que devuelven un IDENTIFICADOR de mano o subproceso siempre devuelven 0.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::AddHandle

Equivalente no funcional de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer

Equivalente no funcional de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle

Equivalente no funcional de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve NULL.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId

Equivalente no funcional de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 0.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Initialize

Equivalente no funcional de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle

Equivalente no funcional de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Shutdown

Equivalente no funcional de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve S_OK.

### <a name="remarks"></a>Observaciones

La implementación proporcionada por esta clase no hace nada.
