---
title: Clase CWorkerThread | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 24
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
ms.openlocfilehash: ab1c92c1b7442025f91007ef971d81d087351212
ms.lasthandoff: 02/24/2017

---
# <a name="cworkerthread-class"></a>Clase CWorkerThread
Esta clase crea un subproceso de trabajo o usa uno existente, espera en uno o más identificadores de objeto de kernel y ejecuta una función de cliente especificado cuando se señala a uno de los identificadores.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>Parámetros  
 `ThreadTraits`  
 La clase que proporciona la función de creación de subproceso, como [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) o [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-structures"></a>Estructuras protegidas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|El constructor para el subproceso de trabajo.|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|El destructor para el subproceso de trabajo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|Llamar a este método para agregar el identificador de un objeto que puede esperar a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::AddTimer](#addtimer)|Llamar a este método para agregar un temporizador periódico que puede esperar a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::GetThreadId](#getthreadid)|Llamar a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::Initialize](#initialize)|Llame a este método para inicializar el subproceso de trabajo.|  
|[CWorkerThread::RemoveHandle](#removehandle)|Llame a este método para quitar un identificador de la lista de objetos que pueden esperar.|  
|[CWorkerThread::Shutdown](#shutdown)|Llamar a este método para cerrar el subproceso de trabajo.|  
  
## <a name="remarks"></a>Comentarios  
  
### <a name="to-use-cworkerthread"></a>Usar CWorkerThread  
  
1.  Cree una instancia de esta clase.  
  
2.  Llame a [CWorkerThread::Initialize](#initialize).  
  
3.  Llame a [CWorkerThread::AddHandle](#addhandle) con el identificador de un objeto de kernel y un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     -O bien-  
  
     Llame a [CWorkerThread::AddTimer](#addtimer) con un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implemente [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) para realizar alguna acción cuando se señala el identificador o el temporizador.  
  
5.  Para quitar un objeto de la lista de objetos de espera, llame a [CWorkerThread::RemoveHandle](#removehandle).  
  
6.  Para finalizar el subproceso, llame a [CWorkerThread::Shutdown](#shutdown).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="addhandle"></a>CWorkerThread::AddHandle  
 Llamar a este método para agregar el identificador de un objeto que puede esperar a la lista mantenida por el subproceso de trabajo.  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 El identificador de un objeto que puede esperar.  
  
 `pClient`  
 El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto al que llamar cuando se señala el controlador.  
  
 `dwParam`  
 El parámetro que se pasan a [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señala el controlador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) se llamará a través de `pClient` cuando el identificador `hObject`, se señala.  
  
##  <a name="addtimer"></a>CWorkerThread::AddTimer  
 Llamar a este método para agregar un temporizador periódico que puede esperar a la lista mantenida por el subproceso de trabajo.  
  
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
  
 `pClient`  
 El puntero a la [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md) interfaz en el objeto al que llamar cuando se señala el controlador.  
  
 `dwParam`  
 El parámetro que se pasan a [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) cuando se señala el controlador.  
  
 `phTimer`  
 [out] Dirección de la variable de identificador que se ejecuta correctamente, recibe el identificador para el temporizador recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) llamará a `pClient` cuando se señala el temporizador.  
  
 Pase el controlador de temporizador de `phTimer` a [CWorkerThread::RemoveHandle](#removehandle) para cerrar el temporizador.  
  
##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread  
 El constructor.  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread  
 Destructor.  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CWorkerThread::Shutdown](#shutdown).  
  
##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle  
 Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de subproceso o NULL si no se ha inicializado el subproceso de trabajo.  
  
##  <a name="getthreadid"></a>CWorkerThread::GetThreadId  
 Llamar a este método para obtener el identificador de subproceso del subproceso de trabajo.  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de subproceso o NULL si no se ha inicializado el subproceso de trabajo.  
  
##  <a name="initialize"></a>CWorkerThread::Initialize  
 Llame a este método para inicializar el subproceso de trabajo.  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pThread`  
 Un subproceso de trabajo existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a este método para inicializar el objeto después de la creación o después de llamar a [CWorkerThread::Shutdown](#shutdown).  
  
 Tener dos o más `CWorkerThread` utilizar el mismo subproceso de trabajo de objetos, uno de ellos sin pasar argumentos, a continuación, pasan un puntero a ese objeto para inicializar el `Initialize` métodos de las demás. Los objetos que se inicialice con el puntero deben apagarse antes que el objeto que se usa para inicializarlos.  
  
 Consulte [CWorkerThread::Shutdown](#shutdown) para obtener información sobre cómo se cambia el comportamiento de ese método cuando se inicializa mediante un puntero a un objeto existente.  
  
##  <a name="removehandle"></a>CWorkerThread::RemoveHandle  
 Llame a este método para quitar un identificador de la lista de objetos que pueden esperar.  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hObject`  
 El identificador para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se quita el identificador [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) se llamará en el objeto asociado que se pasó a [AddHandle](#addhandle). Si se produce un error en esta llamada, `CWorkerThread` llamará Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) función en el identificador.  
  
##  <a name="shutdown"></a>CWorkerThread::Shutdown  
 Llamar a este método para cerrar el subproceso de trabajo.  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwWait`  
 El tiempo en milisegundos para esperar el subproceso de trabajo cerrar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK éxito o error HRESULT en caso de error, por ejemplo, si el valor de tiempo de espera, `dwWait`, se ha superado.  
  
### <a name="remarks"></a>Comentarios  
 Para volver a usar el objeto, llame a [CWorkerThread::Initialize](#initialize) después de llamar a este método.  
  
 Tenga en cuenta que la llamada a **apagado** en un objeto que se inicializa con un puntero a otro `CWorkerThread` objeto no tiene ningún efecto y siempre devuelve S_OK.  
  
## <a name="see-also"></a>Vea también  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [Clases](../../atl/reference/atl-classes.md)   
 [Subprocesamiento múltiple: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)   
 [Interfaz IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)

