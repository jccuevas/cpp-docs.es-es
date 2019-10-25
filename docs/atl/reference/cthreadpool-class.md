---
title: CThreadPool (clase)
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
ms.openlocfilehash: f0b732efdce5cf04349f468363b8d86621d90204
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496304"
---
# <a name="cthreadpool-class"></a>CThreadPool (clase)

Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.

## <a name="syntax"></a>Sintaxis

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parámetros

*Trabajo*<br/>
La clase que se ajusta al [arquetipo de trabajo](../../atl/reference/worker-archetype.md) que proporciona el código que se usa para procesar los elementos de trabajo en cola en el grupo de subprocesos.

*ThreadTraits*<br/>
Clase que proporciona la función utilizada para crear los subprocesos del grupo.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Constructor para el grupo de subprocesos.|
|[CThreadPool::~CThreadPool](#dtor)|El destructor para el grupo de subprocesos.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementación de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Llame a este método para obtener el número de subprocesos del grupo.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Llame a este método para obtener el identificador del puerto de finalización de e/s usado para poner en cola los elementos de trabajo.|
|[CThreadPool::GetSize](#getsize)|Llame a este método para obtener el número de subprocesos del grupo.|
|[CThreadPool::GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.|
|[CThreadPool::Initialize](#initialize)|Llame a este método para inicializar el grupo de subprocesos.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementación de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Llame a este método para poner en cola un elemento de trabajo para que lo controle un subproceso del grupo.|
|[CThreadPool::Release](#release)|Implementación de `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Llame a este método para establecer el número de subprocesos del grupo.|
|[CThreadPool::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.|
|[CThreadPool::Shutdown](#shutdown)|Llame a este método para cerrar el grupo de subprocesos.|

## <a name="remarks"></a>Comentarios

Los subprocesos del grupo se crean y destruyen cuando el grupo se inicializa, cambia de tamaño o se apaga. Se creará una instancia de clase *Worker* en la pila de cada subproceso de trabajo del grupo. Cada instancia activará la duración del subproceso.

Inmediatamente después de la creación de unsubproceso,`Initialize` se llamará a Worker:: en el objeto asociado a ese subproceso. Inmediatamente antes de la destrucción de unsubproceso,`Terminate` se llamará a Worker::. Ambos métodos deben aceptar un argumento **void** <strong>\*</strong> . El valor de este argumento se pasa al grupo de subprocesos mediante el parámetro *pvWorkerParam* de [CThreadPool:: Initialize](#initialize).

Cuando hay elementos de trabajo en la cola y los subprocesos de trabajo están disponibles para el trabajo, un subproceso de trabajo extrae `Execute` un elemento de la cola y llama al método del objeto de *trabajo* para ese subproceso. A continuación, se pasan tres elementos al método: el elemento de la cola, el mismo `pvWorkerParam` pasado a *Worker*: : `Initialize` y *Worker*:: `Terminate`, y un puntero a la estructura [superpuesta](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) que se usa para la cola del puerto de finalización de e/s.

La clase de *trabajo* declara el tipo de los elementos que se pondrán en cola en el grupo de subprocesos proporcionando unTypeDef, Worker `RequestType`::. Este tipo debe ser capaz de convertirse a y desde un ULONG_PTR.

Un ejemplo de una clase de *trabajo* es la [clase CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

##  <a name="addref"></a>  CThreadPool::AddRef

Implementación de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Comentarios

Esta clase no implementa el control de duración mediante el recuento de referencias.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

Constructor para el grupo de subprocesos.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa el valor de tiempo de espera en ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil. h.

##  <a name="dtor"></a>  CThreadPool::~CThreadPool

El destructor para el grupo de subprocesos.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Comentarios

Llama a [CThreadPool:: Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Llame a este método para obtener el número de subprocesos del grupo.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de subprocesos del grupo.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Llame a este método para obtener el identificador del puerto de finalización de e/s usado para poner en cola los elementos de trabajo.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de la cola o NULL si el grupo de subprocesos no se ha inicializado.

##  <a name="getsize"></a>  CThreadPool::GetSize

Llame a este método para obtener el número de subprocesos del grupo.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*pnNumThreads*<br/>
enuncia Dirección de la variable que, si se ejecuta correctamente, recibe el número de subprocesos del grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Llame a este método para obtener el tiempo máximo, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*pdwMaxWait*<br/>
enuncia Dirección de la variable que, si se ejecuta correctamente, recibe el tiempo máximo, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

[CThreadPool:: Shutdown](#shutdown) usa este valor de tiempo de espera si no se proporciona ningún otro valor a ese método.

##  <a name="initialize"></a>  CThreadPool::Initialize

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
Parámetro de trabajo que se va a pasar a los métodos, `Initialize` `Execute`y `Terminate` del objeto de subproceso de trabajo.

*nNumThreads*<br/>
Número solicitado de subprocesos del grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.  El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil. h.

*dwStackSize*<br/>
Tamaño de la pila para cada subproceso del grupo.

*hCompletion*<br/>
Identificador de un objeto que se va a asociar al puerto de finalización.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Implementación de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Comentarios

Los objetos de esta clase se pueden consultar correctamente para `IUnknown` las interfaces e [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) .

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Llame a este método para poner en cola un elemento de trabajo para que lo controle un subproceso del grupo.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parámetros

*request*<br/>
La solicitud que se va a poner en cola.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Este método agrega un elemento de trabajo a la cola. Los subprocesos del grupo seleccionan los elementos de la cola en el orden en que se reciben.

##  <a name="release"></a>  CThreadPool::Release

Implementación de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Comentarios

Esta clase no implementa el control de duración mediante el recuento de referencias.

##  <a name="setsize"></a>  CThreadPool::SetSize

Llame a este método para establecer el número de subprocesos del grupo.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*nNumThreads*<br/>
Número solicitado de subprocesos del grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores de la máquina para obtener el número total de subprocesos. El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil. h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Si el número de subprocesos especificados es menor que el número de subprocesos actualmente en el grupo, el objeto coloca un mensaje de cierre en la cola para que un subproceso en espera lo recoja. Cuando un subproceso en espera extrae el mensaje de la cola, lo notifica al grupo de subprocesos y sale del procedimiento de subproceso. Este proceso se repite hasta que el número de subprocesos del grupo alcanza el número especificado o hasta que no se sale del subproceso en el período especificado por [GetTimeout](#gettimeout)/ [setTimeout](#settimeout). En esta situación, el método devolverá un valor HRESULT correspondiente a WAIT_TIMEOUT y se cancelará el mensaje de cierre pendiente.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Llame a este método para establecer el tiempo máximo, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
Tiempo máximo solicitado, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El tiempo de espera se inicializa en ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil. h.

Tenga en cuenta que *dwMaxWait* es el tiempo que el Grupo esperará a que se cierre un solo subproceso. El tiempo máximo que se podría tomar para quitar varios subprocesos del grupo podría ser ligeramente menor que *dwMaxWait* multiplicado por el número de subprocesos.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Llame a este método para cerrar el grupo de subprocesos.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*<br/>
Tiempo máximo solicitado, en milisegundos, que el grupo de subprocesos esperará a que se cierre un subproceso. Si se especifica 0 o no se proporciona ningún valor, este método usará el tiempo de espera establecido por [CThreadPool:: setTimeout](#settimeout).

### <a name="remarks"></a>Comentarios

Este método envía una solicitud de cierre a todos los subprocesos del grupo. Si el tiempo de espera expira, este método llamará a [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) en cualquier subproceso que no haya salido. Se llama a este método automáticamente desde el destructor de la clase.

## <a name="see-also"></a>Vea también

[IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Clases](../../atl/reference/atl-classes.md)
