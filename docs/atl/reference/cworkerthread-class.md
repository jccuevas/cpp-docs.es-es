---
title: Clase CWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330220"
---
# <a name="cworkerthread-class"></a>Clase CWorkerThread

Esta clase crea un subproceso de trabajo o utiliza uno existente, espera en uno o varios identificadores de objeto sor kernel y ejecuta una función de cliente especificada cuando se señala uno de los identificadores.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parámetros

*ThreadTraits*<br/>
La clase que proporciona la función de creación de subprocesos, como [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) o [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Miembros

### <a name="protected-structures"></a>Estructuras protegidas

|Nombre|Descripción|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|El constructor para el subproceso de trabajo.|
|[CWorkerThread::-CWorkerThread](#dtor)|El destructor del subproceso de trabajo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Llame a este método para agregar el identificador de un objeto que se puede esperar a la lista mantenida por el subproceso de trabajo.|
|[CWorkerThread::AddTimer](#addtimer)|Llame a este método para agregar un temporizador esperable periódico a la lista mantenida por el subproceso de trabajo.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|
|[CWorkerThread::GetThreadId](#getthreadid)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|
|[CWorkerThread::Initialize](#initialize)|Llame a este método para inicializar el subproceso de trabajo.|
|[CWorkerThread::RemoveHandle](#removehandle)|Llame a este método para quitar un identificador de la lista de objetos que se pueden esperar.|
|[CWorkerThread::Shutdown](#shutdown)|Llame a este método para cerrar el subproceso de trabajo.|

## <a name="remarks"></a>Observaciones

### <a name="to-use-cworkerthread"></a>Para usar CWorkerThread

1. Cree una instancia de esta clase.

1. Llame a [CWorkerThread::Initialize](#initialize).

1. Llame a [CWorkerThread::AddHandle](#addhandle) con el identificador de un objeto de kernel y un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- o -

   Llame a [CWorkerThread::AddTimer](#addtimer) con un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implemente [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) para realizar alguna acción cuando se señale el identificador o el temporizador.

1. Para quitar un objeto de la lista de objetos que se pueden esperar, llame a [CWorkerThread::RemoveHandle](#removehandle).

1. Para terminar el subproceso, llame a [CWorkerThread::Shutdown](#shutdown).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle

Llame a este método para agregar el identificador de un objeto que se puede esperar a la lista mantenida por el subproceso de trabajo.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
El identificador de un objeto que se puede esperar.

*pClient*<br/>
El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto que se va a llamar cuando se señala el identificador.

*dwParam*<br/>
El parámetro que se pasará a [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señale el identificador.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se llamará a través de *pClient* cuando se señale el identificador, *hObject*.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer

Llame a este método para agregar un temporizador esperable periódico a la lista mantenida por el subproceso de trabajo.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parámetros

*dwInterval*<br/>
Especifica el período del temporizador en milisegundos.

*pClient*<br/>
El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto que se va a llamar cuando se señala el identificador.

*dwParam*<br/>
El parámetro que se pasará a [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señale el identificador.

*phTimer*<br/>
[fuera] Dirección de la variable HANDLE que, en caso de éxito, recibe el identificador del temporizador recién creado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se llamará a través de *pClient* cuando se señale el temporizador.

Pase el identificador del temporizador de *phTimer* a [CWorkerThread::RemoveHandle](#removehandle) para cerrar el temporizador.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread

El constructor.

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread::-CWorkerThread

Destructor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Observaciones

Llama a [CWorkerThread::Shutdown](#shutdown).

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de subproceso o NULL si el subproceso de trabajo no se ha inicializado.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId

Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de subproceso o NULL si el subproceso de trabajo no se ha inicializado.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Initialize

Llame a este método para inicializar el subproceso de trabajo.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parámetros

*Pthread*<br/>
Un subproceso de trabajo existente.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Se debe llamar a este método para inicializar el objeto después de la creación o después de una llamada a [CWorkerThread::Shutdown](#shutdown).

Para que dos `CWorkerThread` o más objetos usen el mismo subproceso de trabajo, inicialice uno `Initialize` de ellos sin pasar ningún argumento y, a continuación, pase un puntero a ese objeto a los métodos de los demás. Los objetos inicializados con el puntero deben cerrarse antes del objeto utilizado para inicializarlos.

Consulte [CWorkerThread::Shutdown](#shutdown) para obtener información sobre cómo cambia el comportamiento de ese método cuando se inicializa mediante un puntero a un objeto existente.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle

Llame a este método para quitar un identificador de la lista de objetos que se pueden esperar.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
El asa que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Cuando se quita el identificador [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) se llamará en el objeto asociado que se pasó a [AddHandle](#addhandle). Si se produce `CWorkerThread` un error en esta llamada, llamará a la función [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Windows en el identificador.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Shutdown

Llame a este método para cerrar el subproceso de trabajo.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parámetros

*dwWait*<br/>
El tiempo en milisegundos que se debe esperar a que se apague el subproceso de trabajo. ATL_WORKER_THREAD_WAIT valor predeterminado es 10 segundos. Si es necesario, puede definir su propio valor para este símbolo antes de incluir atlutil.h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error, como si se supera el valor de tiempo de espera, *dwWait*.

### <a name="remarks"></a>Observaciones

Para reutilizar el objeto, llame a [CWorkerThread::Initialize](#initialize) después de llamar a este método.

Tenga en `Shutdown` cuenta que llamar a un `CWorkerThread` objeto inicializado con un puntero a otro objeto no tiene ningún efecto y siempre devuelve S_OK.

## <a name="see-also"></a>Consulte también

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Clases](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)<br/>
[Interfaz IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)
