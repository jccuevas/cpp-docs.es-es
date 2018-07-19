---
title: CWorkerThread (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e29bf1c8265a0d92200cda2704b750dfd8db3d6f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885645"
---
# <a name="cworkerthread-class"></a>CWorkerThread (clase)
Esta clase crea un subproceso de trabajo o usa uno existente, espera en uno o varios identificadores de objeto de kernel y ejecuta una función de cliente especificada cuando se señala a uno de los controladores.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Parámetros  
 *ThreadTraits*  
 La clase que proporciona la función de creación de subproceso, como [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) o [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-structures"></a>Estructuras protegidas  
  
|nombre|Descripción|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|El constructor para el subproceso de trabajo.|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|El destructor para el subproceso de trabajo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Llame a este método para agregar el identificador de un objeto que puede esperar a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::AddTimer](#addtimer)|Llame a este método para agregar un temporizador periódico que puede esperar a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::Initialize](#initialize)|Llame a este método para inicializar el subproceso de trabajo.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Llame a este método para quitar un identificador de la lista de objetos que puede esperar.|  
|[CWorkerThread::Shutdown](#shutdown)|Llame a este método para apagar el subproceso de trabajo.|  
  
## <a name="remarks"></a>Comentarios  
  
### <a name="to-use-cworkerthread"></a>Para usar CWorkerThread  
  
1.  Cree una instancia de esta clase.  
  
2.  Llame a [CWorkerThread::Initialize](#initialize).  
  
3.  Llame a [CWorkerThread::AddHandle](#addhandle) con el identificador de un objeto de kernel y un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     - O  
  
     Llame a [CWorkerThread::AddTimer](#addtimer) con un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implemente [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) para realizar alguna acción cuando se señala el identificador o un temporizador.  
  
5.  Para quitar un objeto de la lista de objetos que puede esperar, llame a [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Para terminar el subproceso, llame a [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="addhandle"></a>  CWorkerThread::AddHandle  
 Llame a este método para agregar el identificador de un objeto que puede esperar a la lista mantenida por el subproceso de trabajo.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *hObject*  
 El identificador de un objeto que puede esperar.  
  
 *pClient*  
 El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto que se llama cuando se señala el controlador.  
  
 *dwParam*  
 El parámetro que se pasarán al [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando el identificador se señala.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se llamará a través de *pClient* cuando el identificador, *hObject*, se señala.  
  
##  <a name="addtimer"></a>  CWorkerThread::AddTimer  
 Llame a este método para agregar un temporizador periódico que puede esperar a la lista mantenida por el subproceso de trabajo.  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dwInterval*  
 Especifica el período del temporizador en milisegundos.  
  
 *pClient*  
 El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto que se llama cuando se señala el controlador.  
  
 *dwParam*  
 El parámetro que se pasarán al [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando el identificador se señala.  
  
 *phTimer*  
 [out] Dirección de la variable de identificador que, si se ejecuta correctamente, recibe el identificador para el temporizador recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se llamará a través de *pClient* cuando se señala el temporizador.  
  
 Pasar el identificador de temporizador de *phTimer* a [CWorkerThread::RemoveHandle](#removehandle) para cerrar el temporizador.  
  
##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread  
 El constructor.  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>  CWorkerThread:: ~ CWorkerThread  
 Destructor.  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle  
 Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de subproceso o NULL si no se ha inicializado el subproceso de trabajo.  
  
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
 *subprocesos de POSIX*  
 Un subproceso de trabajo existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método debe llamarse para inicializar el objeto después de la creación o después de llamar a [CWorkerThread::Shutdown](#shutdown).  
  
 Tener dos o más `CWorkerThread` objetos usar el mismo subproceso de trabajo, uno de ellos sin pasar ningún argumento, a continuación, pasa un puntero a ese objeto para inicializar el `Initialize` métodos de los demás. Los objetos que se inicializa con el puntero deben apagarse antes que el objeto que se usan para inicializarlos.  
  
 Consulte [CWorkerThread::Shutdown](#shutdown) para obtener información sobre cómo se cambia el comportamiento de ese método cuando se inicializa mediante un puntero a un objeto existente.  
  
##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle  
 Llame a este método para quitar un identificador de la lista de objetos que puede esperar.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *hObject*  
 Para quitar el identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se quita el identificador [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) se llamará en el objeto asociado a la que se pasó a [AddHandle](#addhandle). Si se produce un error en esta llamada, `CWorkerThread` llamará el Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) función en el identificador.  
  
##  <a name="shutdown"></a>  CWorkerThread::Shutdown  
 Llame a este método para apagar el subproceso de trabajo.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *dwWait*  
 Tiempo en milisegundos para esperar el subproceso de trabajo para que se cierre. ATL_WORKER_THREAD_WAIT el valor predeterminado es 10 segundos. Si es necesario, puede definir su propio valor para este símbolo antes de incluir atlutil.h. 
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si funciona correctamente, o un error HRESULT en caso de error, por ejemplo, si el valor de tiempo de espera, *dwWait*, se supera.  
  
### <a name="remarks"></a>Comentarios  
 Para volver a usar el objeto, llame a [CWorkerThread::Initialize](#initialize) después de llamar a este método.  
  
 Tenga en cuenta que al llamar a `Shutdown` en un objeto que se inicializa con un puntero a otro `CWorkerThread` objeto no tiene ningún efecto y siempre devuelve S_OK.  
  
## <a name="see-also"></a>Vea también  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Clases](../../atl/reference/atl-classes.md)   
 [Multithreading: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient (interfaz)](../../atl/reference/iworkerthreadclient-interface.md)
