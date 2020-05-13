---
title: Clase CThreadPool
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 5e52868f23883836919b96be9aec1815bc1c17b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747449"
---
# <a name="cthreadpool-class"></a>Clase CThreadPool

Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.

## <a name="syntax"></a>Sintaxis

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parámetros

*Trabajador*<br/>
La clase que se ajusta al [arquetipo](../../atl/reference/worker-archetype.md) de trabajo que proporciona el código utilizado para procesar los elementos de trabajo en cola en el grupo de subprocesos.

*ThreadTraits*<br/>
La clase que proporciona la función utilizada para crear los subprocesos en el grupo.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|El constructor del grupo de subprocesos.|
|[CThreadPool::-CThreadPool](#dtor)|El destructor del grupo de subprocesos.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementación de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Llame a este método para obtener el número de subprocesos en el grupo.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.|
|[CThreadPool::GetSize](#getsize)|Llame a este método para obtener el número de subprocesos en el grupo.|
|[CThreadPool::GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.|
|[CThreadPool::Initialize](#initialize)|Llame a este método para inicializar el grupo de subprocesos.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementación de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Llame a este método para poner en cola un elemento de trabajo que debe controlar un subproceso del grupo.|
|[CThreadPool::Release](#release)|Implementación de `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|
|[CThreadPool::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.|
|[CThreadPool::Shutdown](#shutdown)|Llame a este método para cerrar el grupo de subprocesos.|

## <a name="remarks"></a>Observaciones

Los subprocesos del grupo se crean y destruyen cuando el grupo se inicializa, cambia el tamaño o se apaga. Se creará una instancia de la clase *Worker* en la pila de cada subproceso de trabajo del grupo. Cada instancia vivirá durante la duración del subproceso.

Inmediatamente después de *Worker*la creación`Initialize` de un subproceso, Worker :: se llamará en el objeto asociado a ese subproceso. Inmediatamente antes de la *Worker*destrucción`Terminate` de un hilo, Trabajador :: será llamado. Ambos métodos deben aceptar un argumento **void.** <strong>\*</strong> El valor de este argumento se pasa al grupo de subprocesos a través del parámetro *pvWorkerParam* de [CThreadPool::Initialize](#initialize).

Cuando hay elementos de trabajo en la cola y subprocesos de trabajo disponibles `Execute` para el trabajo, un subproceso de trabajo extraerá un elemento de la cola y llamará al método del objeto *Worker* para ese subproceso. A continuación, se pasan tres elementos al método: el elemento de la cola, `pvWorkerParam` el mismo pasado a *Worker* `Initialize` :: y *Worker*:: `Terminate`, y un puntero a la estructura [OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) utilizada para la cola de puertos de finalización de E/S.

La clase *Worker* declara el tipo de los elementos que se pondrán en cola `RequestType`en el grupo de subprocesos proporcionando una propiedad de tipo Worker: *:*. Este tipo debe ser capaz de ser lanzado hacia y desde un ULONG_PTR.

Un ejemplo de una clase *Worker* es [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef

Implementación de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Observaciones

Esta clase no implementa el control de duración mediante el recuento de referencias.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

El constructor del grupo de subprocesos.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa el valor de tiempo de espera en ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool::-CThreadPool

El destructor del grupo de subprocesos.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Observaciones

Llama a [CThreadPool::Shutdown](#shutdown).

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

Llame a este método para obtener el número de subprocesos en el grupo.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de subprocesos del grupo.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de cola o NULL si el grupo de subprocesos no se ha inicializado.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize

Llame a este método para obtener el número de subprocesos en el grupo.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*pnNumThreads*<br/>
[fuera] Dirección de la variable que, en caso de éxito, recibe el número de subprocesos del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

Llame a este método para obtener el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*pdwMaxWait*<br/>
[fuera] Dirección de la variable que, en caso de éxito, recibe el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[CThreadPool::Shutdown](#shutdown) utiliza este valor de tiempo de espera si no se proporciona ningún otro valor a ese método.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Initialize

Llame a este método para inicializar el grupo de subprocesos.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parámetros

*pvWorkerParam*<br/>
El parámetro de trabajo que se pasará `Initialize` `Execute`a `Terminate` los métodos , y del objeto de subproceso de trabajo.

*nNumThreads*<br/>
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.  El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

*dwStackSize*<br/>
El tamaño de pila para cada subproceso del grupo.

*hCompletion*<br/>
Identificador de un objeto que se va a asociar al puerto de finalización.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface

Implementación de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Observaciones

Los objetos de esta clase se `IUnknown` pueden consultar correctamente para las interfaces [IThreadPoolConfig.](../../atl/reference/ithreadpoolconfig-interface.md)

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

Llame a este método para poner en cola un elemento de trabajo que debe controlar un subproceso del grupo.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parámetros

*Solicitud*<br/>
La solicitud que se va a poner en cola.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Este método agrega un elemento de trabajo a la cola. Los subprocesos del grupo seleccionan los elementos de la cola en el orden en que se reciben.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Release

Implementación de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Observaciones

Esta clase no implementa el control de duración mediante el recuento de referencias.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize

Llame a este método para establecer el número de subprocesos en el grupo.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*nNumThreads*<br/>
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos. El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Si el número de subprocesos especificado es menor que el número de subprocesos actualmente en el grupo, el objeto coloca un mensaje de apagado en la cola que se recogerá mediante un subproceso en espera. Cuando un subproceso en espera extrae el mensaje de la cola, notifica al grupo de subprocesos y sale del procedimiento de subprocesos. Este proceso se repite hasta que el número de subprocesos del grupo alcanza el número especificado o hasta que ningún subproceso ha salido dentro del período especificado por [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). En esta situación, el método devolverá un HRESULT correspondiente a WAIT_TIMEOUT y se cancela el mensaje de apagado pendiente.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout

Llame a este método para establecer el tiempo máximo en milisegundos que el grupo de subprocesos esperará a que se cierre un subproceso.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
El tiempo máximo solicitado en milisegundos que el grupo de subprocesos esperará a que se apague un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El tiempo de espera se inicializa en ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

Tenga en cuenta que *dwMaxWait* es el tiempo que el grupo esperará a que se apague un único subproceso. El tiempo máximo que se podría tardar en quitar varios subprocesos del grupo podría ser ligeramente menor que *dwMaxWait* multiplicado por el número de subprocesos.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Shutdown

Llame a este método para cerrar el grupo de subprocesos.

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
El tiempo máximo solicitado en milisegundos que el grupo de subprocesos esperará a que se apague un subproceso. Si se proporciona 0 o ningún valor, este método utilizará el tiempo de espera establecido por [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Observaciones

Este método publica una solicitud de apagado en todos los subprocesos del grupo. Si expira el tiempo de espera, este método llamará a [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) en cualquier subproceso que no haya salido. Este método se llama automáticamente desde el destructor de la clase.

## <a name="see-also"></a>Vea también

[Interfaz IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Clases](../../atl/reference/atl-classes.md)
