---
title: CThreadPool (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6739e179843864c952a5e864de1389b466d7ca7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 La clase conforme a la [Arquetipo trabajo](../../atl/reference/worker-archetype.md) proporcionar el código utilizado para procesar elementos en cola en el grupo de subprocesos de trabajo.  
  
 `ThreadTraits`  
 La clase proporciona la función usada para crear los subprocesos en el grupo.  
  
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
|[CThreadPool::GetNumThreads](#getnumthreads)|Llamar a este método para obtener el número de subprocesos en el grupo.|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.|  
|[CThreadPool:: GetSize](#getsize)|Llamar a este método para obtener el número de subprocesos en el grupo.|  
|[CThreadPool::GetTimeout](#gettimeout)|Llamar a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.|  
|[CThreadPool::Initialize](#initialize)|Llamar a este método para inicializar el grupo de subprocesos.|  
|[CThreadPool::QueryInterface](#queryinterface)|Implementación de **IUnknown:: QueryInterface**.|  
|[CThreadPool::QueueRequest](#queuerequest)|Llamar a este método para poner en cola un elemento de trabajo para ser controladas por un subproceso en el grupo.|  
|[CThreadPool::Release](#release)|Implementación de `IUnknown::Release`.|  
|[CThreadPool:: SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|  
|[CThreadPool::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.|  
|[CThreadPool::Shutdown](#shutdown)|Llamar a este método para cerrar el grupo de subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 Se crean y se destruyen cuando se inicializa, se cambia el tamaño o se apaga el grupo de subprocesos en el grupo. Una instancia de clase *trabajo* se creará en la pila de cada subproceso de trabajo en el grupo. Cada instancia residirá durante la duración del subproceso.  
  
 Inmediatamente después de la creación de un subproceso, *trabajo*:: `Initialize` se llamará en el objeto asociado a ese subproceso. Inmediatamente antes de la destrucción de un subproceso, *trabajo*:: `Terminate` se llamará. Ambos métodos deben aceptar un **void\***  argumento. El valor de este argumento se pasa al grupo de subprocesos a través de la `pvWorkerParam` parámetro de [CThreadPool::Initialize](#initialize).  
  
 Cuando hay elementos de trabajo en los subprocesos de trabajo y de cola disponible para el trabajo, un subproceso de trabajo extraerá un elemento de la cola y llamar a la **Execute** método de la *trabajo* objeto de ese subproceso. Tres elementos, a continuación, se pasan al método: el elemento de la cola, el mismo `pvWorkerParam` pasado a *trabajo*:: `Initialize` y *trabajo*:: `Terminate`y un puntero a la [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) estructura usada para la cola de puerto de finalización de E/S.  
  
 El *trabajo* clase declara el tipo de los elementos que se pondrán en cola en el grupo de subprocesos al proporcionar una definición de tipo, *trabajo*:: `RequestType`. Este tipo debe ser capaz de que se va a convertir a y desde una **ULONG_PTR**.  
  
 Un ejemplo de un *trabajo* clase es [CNonStatelessWorker clase](../../atl/reference/cnonstatelessworker-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUnknown`  
  
 [Interfaz IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="addref"></a>CThreadPool::AddRef  
 Implementación de `IUnknown::AddRef`.  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no implementa control de duración con recuento de referencias.  
  
##  <a name="cthreadpool"></a>CThreadPool::CThreadPool  
 El constructor para el grupo de subprocesos.  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el valor de tiempo de espera para `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.  
  
##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 El destructor para el grupo de subprocesos.  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CThreadPool::Shutdown](#shutdown).  
  
##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 Llamar a este método para obtener el número de subprocesos en el grupo.  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de subprocesos en el grupo.  
  
##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de la cola o NULL si no se ha inicializado el grupo de subprocesos.  
  
##  <a name="getsize"></a>CThreadPool:: GetSize  
 Llamar a este método para obtener el número de subprocesos en el grupo.  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pnNumThreads`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="gettimeout"></a>CThreadPool::GetTimeout  
 Llamar a este método para obtener el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pdwMaxWait`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este valor de tiempo de espera se utiliza por [CThreadPool::Shutdown](#shutdown) si no se proporciona ningún otro valor para ese método.  
  
##  <a name="initialize"></a>CThreadPool::Initialize  
 Llamar a este método para inicializar el grupo de subprocesos.  
  
```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pvWorkerParam`  
 El parámetro de trabajo que se pasa para el objeto de subproceso de trabajo `Initialize`, **Execute**, y `Terminate` métodos.  
  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, `ATLS_DEFAULT_THREADSPERPROC` se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.
  
 `dwStackSize`  
 El tamaño de pila para cada subproceso en el grupo.  
  
 *hCompletion*  
 El identificador de un objeto para asociar el puerto de terminación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="queryinterface"></a>CThreadPool::QueryInterface  
 Implementación de **IUnknown:: QueryInterface**.  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Objetos de esta clase se pueden consultar correctamente para la **IUnknown** y [interfaz IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfaces.  
  
##  <a name="queuerequest"></a>CThreadPool::QueueRequest  
 Llamar a este método para poner en cola un elemento de trabajo para ser controladas por un subproceso en el grupo.  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `request`  
 La solicitud para poner en cola.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega un elemento de trabajo a la cola. Los subprocesos en el grupo de seleccionar elementos de la cola en el orden en el que se reciben.  
  
##  <a name="release"></a>CThreadPool::Release  
 Implementación de `IUnknown::Release`.  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no implementa control de duración con recuento de referencias.  
  
##  <a name="setsize"></a>CThreadPool:: SetSize  
 Llame a este método para establecer el número de subprocesos en el grupo.  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, `ATLS_DEFAULT_THREADSPERPROC` se multiplicará por el número de procesadores en el equipo para obtener el número total de subprocesos. El valor predeterminado es 2 subprocesos por procesador. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h.
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si el número de subprocesos especificado es menor que el número de subprocesos actualmente en el grupo, el objeto coloca un mensaje de cierre en la cola para ser recogidas por un subproceso en espera. Cuando un subproceso en espera extrae el mensaje fuera de la cola, se notifica el grupo de subprocesos y sale del procedimiento de subproceso. Este proceso se repite hasta que el número de subprocesos en el grupo alcanza el número especificado o hasta que ningún subproceso ha terminado dentro del período especificado por [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). En esta situación, el método devolverá un valor HRESULT correspondiente a **WAIT_TIMEOUT** y se cancela el mensaje de cierre pendiente.  
  
##  <a name="settimeout"></a>CThreadPool::SetTimeout  
 Llame a este método para establecer el tiempo máximo en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El tiempo de espera se inicializa en `ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`. El tiempo predeterminado es de 36 segundos. Si es necesario, puede definir su propio valor entero positivo para este símbolo antes de incluir atlutil.h. 
  
 Tenga en cuenta que `dwMaxWait` es el tiempo que esperará el grupo de a un único subproceso para apagar. El tiempo máximo que puede realizar para quitar varios subprocesos del grupo podría ser un poco menos de `dwMaxWait` multiplicado por el número de subprocesos.  
  
##  <a name="shutdown"></a>CThreadPool::Shutdown  
 Llamar a este método para cerrar el grupo de subprocesos.  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 El tiempo máximo solicitado en milisegundos que esperará el grupo de subprocesos para que un subproceso a apagar. Si se especifica 0 o ningún valor, este método utilizará el tiempo de espera establecido [CThreadPool::SetTimeout](#settimeout).  
  
### <a name="remarks"></a>Comentarios  
 Este método envía una solicitud de cierre a todos los subprocesos en el grupo. Si se agota el tiempo de espera, este método llamará [TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717) en cualquier subproceso que no se cerró. Este método se llama automáticamente desde el destructor de la clase.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Clases](../../atl/reference/atl-classes.md)
