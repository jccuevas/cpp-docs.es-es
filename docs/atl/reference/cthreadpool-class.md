---
title: CThreadPool (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CThreadPool
- ATL::CThreadPool
- CThreadPool
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 632514d03e7037ef42a1566462db5dec6f5cc1e5
ms.lasthandoff: 02/24/2017

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
 La clase que se ajuste a la [Arquetipo de trabajo](../../atl/reference/worker-archetype.md) que proporciona el código utilizado para procesar elementos en cola en el grupo de subprocesos de trabajo.  
  
 `ThreadTraits`  
 La clase que proporciona la función utilizada para crear los subprocesos en el grupo.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|El constructor para el grupo de subprocesos.|  
|[CThreadPool:: ~ CThreadPool](#dtor)|El destructor para el grupo de subprocesos.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|Implementación de `IUnknown::AddRef`.|  
|[CThreadPool::GetNumThreads](#getnumthreads)|Llame a este método para obtener el número de subprocesos en el grupo.|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.|  
|[CThreadPool:: GetSize](#getsize)|Llame a este método para obtener el número de subprocesos en el grupo.|  
|[CThreadPool::GetTimeout](#gettimeout)|Llame a este método para obtener el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.|  
|[CThreadPool::Initialize](#initialize)|Llame a este método para inicializar el grupo de subprocesos.|  
|[CThreadPool::QueryInterface](#queryinterface)|Implementación de **IUnknown:: QueryInterface**.|  
|[CThreadPool::QueueRequest](#queuerequest)|Llamar a este método para poner en cola un elemento de trabajo para ser controladas por un subproceso del grupo.|  
|[CThreadPool::Release](#release)|Implementación de `IUnknown::Release`.|  
|[CThreadPool:: SetSize](#setsize)|Llame a este método para establecer el número de subprocesos en el grupo.|  
|[CThreadPool::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.|  
|[CThreadPool::Shutdown](#shutdown)|Llamar a este método para cerrar el grupo de subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 Se crean y se destruye cuando se inicializa, cambia el tamaño o cerrar el grupo de subprocesos en el grupo. Una instancia de la clase *trabajo* se creará en la pila de cada subproceso de trabajo en el grupo. Cada instancia residirá durante la vigencia del subproceso.  
  
 Inmediatamente después de la creación de un subproceso *trabajo*:: `Initialize` se llamará en el objeto asociado a ese subproceso. Inmediatamente antes de la destrucción de un subproceso *trabajo*:: `Terminate` se llamará. Ambos métodos deben aceptar una **void\* ** argumento. El valor de este argumento se pasa al grupo de subprocesos a través de la `pvWorkerParam` parámetro de [CThreadPool::Initialize](#initialize).  
  
 Cuando hay elementos de trabajo en los subprocesos de trabajo y de cola disponible para el trabajo, un subproceso de trabajo extraerá un elemento de la cola y llamar a la **Execute** método de la *trabajo* objeto de ese subproceso. Tres elementos, a continuación, se pasan al método: el elemento de la cola, el mismo `pvWorkerParam` pasado a *trabajo*:: `Initialize` y *trabajo*:: `Terminate`y un puntero a la [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) estructura utilizada para la cola de puerto de finalización de E/S.  
  
 El *trabajo* clase declara el tipo de los elementos que se pondrán en cola en el grupo de subprocesos al proporcionar un typedef, *trabajo*:: `RequestType`. Este tipo debe ser capaz de que se va a convertir a un **ULONG_PTR**.  
  
 Un ejemplo de un *trabajo* clase es [CNonStatelessWorker clase](../../atl/reference/cnonstatelessworker-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUnknown`  
  
 [Interfaz IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="a-nameaddrefa--cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef  
 Implementación de `IUnknown::AddRef`.  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no implementa control de duración con el recuento de referencias.  
  
##  <a name="a-namecthreadpoola--cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool  
 El constructor para el grupo de subprocesos.  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el valor de tiempo de espera para [ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10).  
  
##  <a name="a-namedtora--cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 El destructor para el grupo de subprocesos.  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CThreadPool::Shutdown](#shutdown).  
  
##  <a name="a-namegetnumthreadsa--cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 Llame a este método para obtener el número de subprocesos en el grupo.  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de subprocesos en el grupo.  
  
##  <a name="a-namegetqueuehandlea--cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 Llame a este método para obtener el identificador del puerto de finalización de E/S utilizado para poner en cola los elementos de trabajo.  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de la cola o NULL si no se ha inicializado el grupo de subprocesos.  
  
##  <a name="a-namegetsizea--cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool:: GetSize  
 Llame a este método para obtener el número de subprocesos en el grupo.  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pnNumThreads`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el número de subprocesos en el grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namegettimeouta--cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout  
 Llame a este método para obtener el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pdwMaxWait`  
 [out] Dirección de la variable que se ejecuta correctamente, recibe el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza este valor de tiempo de espera [CThreadPool::Shutdown](#shutdown) si no se proporciona ningún otro valor para ese método.  
  
##  <a name="a-nameinitializea--cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Initialize  
 Llame a este método para inicializar el grupo de subprocesos.  
  
```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pvWorkerParam`  
 El parámetro de trabajo que se pasará al objeto de subproceso de trabajo `Initialize`, **Execute**, y `Terminate` métodos.  
  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
 `dwStackSize`  
 El tamaño de pila para cada subproceso del grupo.  
  
 *hCompletion*  
 El identificador de un objeto para asociar el puerto de terminación.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="a-namequeryinterfacea--cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface  
 Implementación de **IUnknown:: QueryInterface**.  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Objetos de esta clase se pueden consultar correctamente para la **IUnknown** y [interfaz IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfaces.  
  
##  <a name="a-namequeuerequesta--cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest  
 Llamar a este método para poner en cola un elemento de trabajo para ser controladas por un subproceso del grupo.  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `request`  
 La solicitud se ponga en cola.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega un elemento de trabajo a la cola. Los subprocesos en el grupo elegir elementos de la cola en el orden en que se reciben.  
  
##  <a name="a-namereleasea--cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Release  
 Implementación de `IUnknown::Release`.  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no implementa control de duración con el recuento de referencias.  
  
##  <a name="a-namesetsizea--cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool:: SetSize  
 Llame a este método para establecer el número de subprocesos en el grupo.  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nNumThreads`  
 El número solicitado de subprocesos en el grupo.  
  
 Si `nNumThreads` es negativo, su valor absoluto se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
 Si `nNumThreads` es cero, [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571) se multiplicará por el número de procesadores del equipo para obtener el número total de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Si el número de subprocesos especificado es menor que el número de subprocesos actualmente en el grupo, el objeto coloca un mensaje de cierre en la cola para ser recogidas por un subproceso en espera. Cuando un subproceso en espera extrae el mensaje de la cola, notifica el grupo de subprocesos y sale del procedimiento de subproceso. Este proceso se repite hasta que el número de subprocesos en el grupo alcanza el número especificado o hasta que ningún subproceso ha terminado dentro del período especificado por [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). En esta situación el método devolverá un HRESULT correspondiente a **WAIT_TIMEOUT** y se cancela el mensaje de cierre pendiente.  
  
##  <a name="a-namesettimeouta--cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout  
 Llame a este método para establecer el tiempo máximo en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 Tiempo máximo solicitado en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El tiempo de espera se inicializa en [ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10) en el constructor.  
  
 Tenga en cuenta que `dwMaxWait` es el tiempo que esperará el grupo de un solo subproceso apagar. El tiempo máximo que puede adoptar para quitar varios subprocesos del grupo podría ser ligeramente menor `dwMaxWait` multiplicado por el número de subprocesos.  
  
##  <a name="a-nameshutdowna--cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Shutdown  
 Llamar a este método para cerrar el grupo de subprocesos.  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwMaxWait`  
 Tiempo máximo solicitado en milisegundos que se va a esperar un subproceso cerrar el grupo de subprocesos. Si se especifica 0 o ningún valor, este método utilizará el tiempo de espera establecido por [CThreadPool::SetTimeout](#settimeout).  
  
### <a name="remarks"></a>Comentarios  
 Este método envía una solicitud de cierre a todos los subprocesos en el grupo. Si se agota el tiempo de espera, este método llamará [TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717) en cualquier subproceso que no se cerró. Este método se llama automáticamente desde el destructor de la clase.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IThreadPoolConfig (interfaz)](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Clases](../../atl/reference/atl-classes.md)

