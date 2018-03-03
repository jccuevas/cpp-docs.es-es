---
title: Clase CNoWorkerThread | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36af37fae778a572d790a137073c62cfde22019c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cnoworkerthread-class"></a>Clase CNoWorkerThread
Utilice esta clase como argumento para el `MonitorClass` parámetro de plantilla a las clases de caché si desea deshabilitar el mantenimiento de la memoria caché dinámica.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
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
  
 Los métodos de esta clase se implementan para no hacer nada. Los métodos que devuelven un valor HRESULT siempre devuelven S_OK y los métodos que devuelven un identificador de subproceso o de identificador siempre devuelven 0.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="addhandle"></a>CNoWorkerThread::AddHandle  
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
  
##  <a name="addtimer"></a>CNoWorkerThread::AddTimer  
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
  
##  <a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle  
 No funcional equivalente de [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="getthreadid"></a>CNoWorkerThread::GetThreadId  
 No funcional equivalente de [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="initialize"></a>CNoWorkerThread::Initialize  
 No funcional equivalente de [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="removehandle"></a>CNoWorkerThread::RemoveHandle  
 No funcional equivalente de [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.  
  
##  <a name="shutdown"></a>CNoWorkerThread::Shutdown  
 No funcional equivalente de [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve S_OK.  
  
### <a name="remarks"></a>Comentarios  
 La implementación proporcionada por esta clase no hace nada.
