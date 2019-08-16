---
title: CWorkerThread (clase)
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
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496116"
---
# <a name="cworkerthread-class"></a>CWorkerThread (clase)

Esta clase crea un subproceso de trabajo o utiliza uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala uno de los identificadores.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

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

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Constructor para el subproceso de trabajo.|
|[CWorkerThread::~CWorkerThread](#dtor)|El destructor del subproceso de trabajo.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Llame a este método para agregar un identificador de un objeto que se pueda esperar a la lista mantenida por el subproceso de trabajo.|
|[CWorkerThread::AddTimer](#addtimer)|Llame a este método para agregar un temporizador de espera periódica a la lista que mantiene el subproceso de trabajo.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|
|[CWorkerThread::GetThreadId](#getthreadid)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|
|[CWorkerThread::Initialize](#initialize)|Llame a este método para inicializar el subproceso de trabajo.|
|[CWorkerThread::RemoveHandle](#removehandle)|Llame a este método para quitar un identificador de la lista de objetos que se van a esperar.|
|[CWorkerThread::Shutdown](#shutdown)|Llame a este método para cerrar el subproceso de trabajo.|

## <a name="remarks"></a>Comentarios

### <a name="to-use-cworkerthread"></a>Para usar CWorkerThread

1. Cree una instancia de esta clase.

1. Llame a [CWorkerThread:: Initialize](#initialize).

1. Llame a [CWorkerThread:: AddHandle](#addhandle) con el identificador de un objeto de kernel y un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

   \- o -

   Llame a [CWorkerThread:: AddTimer](#addtimer) con un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).

1. Implemente [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) para realizar alguna acción cuando se señale el identificador o el temporizador.

1. Para quitar un objeto de la lista de objetos que se van a esperar, llame a [CWorkerThread:: RemoveHandle](#removehandle).

1. Para finalizar el subproceso, llame a [CWorkerThread:: Shutdown](#shutdown).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

Llame a este método para agregar un identificador de un objeto que se pueda esperar a la lista mantenida por el subproceso de trabajo.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador de un objeto que se va a esperar.

*pClient*<br/>
Puntero a la interfaz [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) en el objeto al que se va a llamar cuando se señale el identificador.

*dwParam*<br/>
Parámetro que se va a pasar a [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señala el identificador.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Se llamará a [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) a través de *pClient* cuando se señale el identificador, *hObject*.

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

Llame a este método para agregar un temporizador de espera periódica a la lista que mantiene el subproceso de trabajo.

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
Puntero a la interfaz [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) en el objeto al que se va a llamar cuando se señale el identificador.

*dwParam*<br/>
Parámetro que se va a pasar a [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señala el identificador.

*phTimer*<br/>
enuncia Dirección de la variable de identificador que, si se ejecuta correctamente, recibe el identificador del temporizador recién creado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Se llamará a [IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) a través de *pClient* cuando se Señalice el temporizador.

Pase el identificador del temporizador de *phTimer* a [CWorkerThread:: RemoveHandle](#removehandle) para cerrar el temporizador.

##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread

El constructor.

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>  CWorkerThread::~CWorkerThread

Destructor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Comentarios

Llama a [CWorkerThread:: Shutdown](#shutdown).

##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle

Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del subproceso o NULL si no se ha inicializado el subproceso de trabajo.

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de subproceso o NULL si no se ha inicializado el subproceso de trabajo.

##  <a name="initialize"></a>  CWorkerThread::Initialize

Llame a este método para inicializar el subproceso de trabajo.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parámetros

*pThread*<br/>
Un subproceso de trabajo existente.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Se debe llamar a este método para inicializar el objeto después de la creación o después de una llamada a [CWorkerThread:: Shutdown](#shutdown).

Para tener dos o más `CWorkerThread` objetos que usen el mismo subproceso de trabajo, inicialice uno de ellos sin pasar ningún argumento y, a continuación, pase `Initialize` un puntero a ese objeto a los métodos de los demás. Los objetos inicializados con el puntero deben cerrarse antes del objeto que se usa para inicializarlos.

Vea [CWorkerThread:: Shutdown](#shutdown) para obtener información sobre cómo cambia el comportamiento del método cuando se inicializa con un puntero a un objeto existente.

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

Llame a este método para quitar un identificador de la lista de objetos que se van a esperar.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parámetros

*hObject*<br/>
Identificador que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Cuando se quita el identificador, se llamará a [IWorkerThreadClient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) en el objeto asociado que se pasó a [AddHandle](#addhandle). Si se produce un error `CWorkerThread` en esta llamada, llamará a la función [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Windows en el identificador.

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

Llame a este método para cerrar el subproceso de trabajo.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parámetros

*dwWait*<br/>
Tiempo en milisegundos que se debe esperar hasta que se cierre el subproceso de trabajo. El valor predeterminado de ATL_WORKER_THREAD_WAIT es 10 segundos. Si es necesario, puede definir su propio valor para este símbolo antes de incluir atlutil. h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente o un error HRESULT en caso de error, como si se supera el valor de tiempo de espera, *dwWait*.

### <a name="remarks"></a>Comentarios

Para volver a usar el objeto, llame a [CWorkerThread:: Initialize](#initialize) después de llamar a este método.

Tenga en cuenta `Shutdown` que llamar a en un objeto inicializado con un `CWorkerThread` puntero a otro objeto no tiene ningún efecto y siempre Devuelve S_OK.

## <a name="see-also"></a>Vea también

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Clases](../../atl/reference/atl-classes.md)<br/>
[Multithreading: crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient (interfaz)](../../atl/reference/iworkerthreadclient-interface.md)
