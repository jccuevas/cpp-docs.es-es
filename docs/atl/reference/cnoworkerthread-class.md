---
title: Clase CNoWorkerThread | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CNoWorkerThread
- ATL.CNoWorkerThread
- CNoWorkerThread
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
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
ms.openlocfilehash: 4c38d778849a31d55a657fc1022c2e9f4a370eec
ms.lasthandoff: 02/24/2017

---
# <a name="cnoworkerthread-class"></a>Clase CNoWorkerThread
Utilice esta clase como argumento para el `MonitorClass` parámetro de plantilla a las clases de caché si desea deshabilitar el mantenimiento de la memoria caché dinámica.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|No funcional equivalente de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|  
|[CNoWorkerThread::AddTimer](#addtimer)|No funcional equivalente de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|No funcional equivalente de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|No funcional equivalente de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|  
|[CNoWorkerThread::Initialize](#initialize)|No funcional equivalente de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|No funcional equivalente de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|  
|[CNoWorkerThread::Shutdown](#shutdown)|No funcional equivalente de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona la misma interfaz pública que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Esta interfaz debe proporcionar el `MonitorClass` parámetro de plantilla a las clases de caché.  
  
 Los métodos de esta clase se implementan que no haga nada. Los métodos que devuelven un HRESULT siempre devuelven S_OK y los métodos que devuelven un identificador de subproceso o de identificador siempre devuelven 0.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="a-nameaddhandlea--cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::AddHandle  
 No funcional equivalente de [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-nameaddtimera--cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer  
 No funcional equivalente de [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-namegetthreadhandlea--cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle  
 No funcional equivalente de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-namegetthreadida--cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId  
 No funcional equivalente de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-nameinitializea--cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Initialize  
 No funcional equivalente de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-nameremovehandlea--cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle  
 No funcional equivalente de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="a-nameshutdowna--cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Shutdown  
 No funcional equivalente de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.

