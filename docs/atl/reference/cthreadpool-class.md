---
title: CThreadPool (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9753599f08d1e8ee238097027c501a0b56e40300
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757399"
---
# <a name="cthreadpool-class"></a>CThreadPool (clase)

Esta clase proporciona un grupo de subprocesos de trabajo que procesan una cola de elementos de trabajo.

## <a name="syntax"></a>Sintaxis

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parámetros

*Trabajo*  
La clase que se ajuste a la [worker (Arquetipo)](../../atl/reference/worker-archetype.md) que proporciona el código que se usa para procesar elementos en cola en el grupo de subprocesos de trabajo.

*ThreadTraits*  
La clase que proporciona la función utilizada para crear los subprocesos en el grupo.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|El constructor para el grupo de subprocesos.|
|[CThreadPool:: ~ CThreadPool](#dtor)|El destructor para el grupo de subprocesos.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementación de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Llame a este método para obtener el número de subprocesos del grupo.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.|
|[CThreadPool:: GetSize](#getsize)|Llame a este método para obtener el número de subprocesos del grupo.|
|[CThreadPool::GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.|
|[CThreadPool::Initialize](#initialize)|Llame a este método para inicializar el grupo de subprocesos.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementación de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Llame a este método para poner en cola un elemento de trabajo que va a administrar un subproceso del grupo.|
|[CThreadPool::Release](#release)|Implementación de `IUnknown::Release`.|
|[CThreadPool:: SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|
|[CThreadPool::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.|
|[CThreadPool::Shutdown](#shutdown)|Llame a este método para cerrar el grupo de subprocesos.|

## <a name="remarks"></a>Comentarios

Se crean y se destruyen cuando se inicializa, cambia el tamaño o cerrar el grupo de subprocesos en el grupo. Una instancia de clase *trabajo* se crearán en la pila de cada subproceso de trabajo en el grupo. Cada instancia se encontrarán durante la vigencia del subproceso.

Inmediatamente después de la creación de un subproceso, *trabajo*::`Initialize` se llamará en el objeto asociado a ese subproceso. Inmediatamente antes de la destrucción de un subproceso, *trabajo*::`Terminate` se llamará. Ambos métodos deben aceptar una **void** <strong>\*</strong> argumento. El valor de este argumento se pasa al grupo de subprocesos a través de la *pvWorkerParam* parámetro de [CThreadPool::Initialize](#initialize).

Cuando hay elementos de trabajo en los subprocesos de trabajo y de cola disponible para el trabajo, un subproceso de trabajo extrae un elemento fuera de la cola y llame a la `Execute` método de la *trabajo* objeto para ese subproceso. Tres elementos, a continuación, se pasan al método: el elemento de la cola, el mismo `pvWorkerParam` pasado a *trabajo*:: `Initialize` y *trabajo*:: `Terminate`y un puntero a la [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) estructura usada para la cola de puerto de finalización de E/S.

El *trabajo* clase declara el tipo de los elementos que se pondrán en cola en el grupo de subprocesos, ya que proporciona una definición de tipo *trabajo*:: `RequestType`. Este tipo debe ser capaz de que se va a convertir a y desde un ULONG_PTR.

Un ejemplo de un *trabajo* clase es [CNonStatelessWorker (clase)](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="addref"></a>  CThreadPool::AddRef

Implementación de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Comentarios

Esta clase no implementa el control de duración con un recuento de referencias.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

El constructor para el grupo de subprocesos.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa el valor de tiempo de espera para ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

##  <a name="dtor"></a>  CThreadPool:: ~ CThreadPool

El destructor para el grupo de subprocesos.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Comentarios

Las llamadas [CThreadPool::Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Llame a este método para obtener el número de subprocesos del grupo.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de subprocesos del grupo.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de la cola o NULL si no se ha inicializado el grupo de subprocesos.

##  <a name="getsize"></a>  CThreadPool:: GetSize

Llame a este método para obtener el número de subprocesos del grupo.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*pnNumThreads*  
[out] Dirección de la variable que, si se ejecuta correctamente, recibe el número de subprocesos en el grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Llame a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*pdwMaxWait*  
[out] Dirección de la variable que, si se ejecuta correctamente, recibe el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este valor de tiempo de espera se utiliza por [CThreadPool::Shutdown](#shutdown) si no se proporciona ningún otro valor para ese método.

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

*pvWorkerParam*  
El parámetro de trabajo que se pasarán al objeto de subproceso de trabajo `Initialize`, `Execute`, y `Terminate` métodos.

*nNumThreads*  
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

*dwStackSize*  
El tamaño de pila para cada subproceso del grupo.

*hCompletion*  
El identificador de un objeto para asociar el puerto de terminación.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Implementación de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Comentarios

Objetos de esta clase se pueden consultar correctamente para el `IUnknown` y [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfaces.

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Llame a este método para poner en cola un elemento de trabajo que va a administrar un subproceso del grupo.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parámetros

*Solicitud*  
La solicitud para poner en cola.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Este método agrega un elemento de trabajo a la cola. Los subprocesos en el grupo elegir elementos de la cola en el orden en que se reciben.

##  <a name="release"></a>  CThreadPool::Release

Implementación de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valor devuelto

Siempre devuelve 1.

### <a name="remarks"></a>Comentarios

Esta clase no implementa el control de duración con un recuento de referencias.

##  <a name="setsize"></a>  CThreadPool:: SetSize

Llame a este método para establecer el número de subprocesos en el grupo.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parámetros

*nNumThreads*  
El número solicitado de subprocesos en el grupo.

Si *nNumThreads* es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.

Si *nNumThreads* es cero, ATLS_DEFAULT_THREADSPERPROC se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos. El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Si el número de subprocesos especificado es menor que el número de subprocesos actualmente en el grupo, en el objeto se coloca un mensaje de cierre en la cola para recoger un subproceso en espera. Cuando un subproceso en espera extrae el mensaje de la cola, que notifica el grupo de subprocesos y cierra el procedimiento de subproceso. Este proceso se repite hasta que el número de subprocesos en el grupo alcanza el número especificado o hasta que ningún subproceso ha terminado dentro del período especificado por [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). En esta situación, el método devolverá un HRESULT correspondiente a WAIT_TIMEOUT y se cancela el mensaje de cierre pendiente.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*  
El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El tiempo de espera se inicializa en ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.

Tenga en cuenta que *dwMaxWait* es el tiempo que esperará el grupo para que un solo subproceso para que se cierre. El tiempo máximo que se puede tomar para quitar varios subprocesos del grupo podría ser ligeramente inferior a *dwMaxWait* multiplicado por el número de subprocesos.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Llame a este método para cerrar el grupo de subprocesos.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parámetros

*dwMaxWait*  
El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos de un subproceso para que se cierre. Si se especifica 0 o ningún valor, este método usará el tiempo de espera establecido por [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Comentarios

Este método envía una solicitud de cierre a todos los subprocesos del grupo. Si se agota el tiempo de espera, se llamará este método [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) en cualquier subproceso que no se cerró. Este método se llama automáticamente desde el destructor de la clase.

## <a name="see-also"></a>Vea también

[IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)   
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
[Clases](../../atl/reference/atl-classes.md)
