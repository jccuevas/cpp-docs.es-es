---
title: IExecutionContext (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 4c4301d7afe46249d6d67ab2a6ec0a9fc2c7935e
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="iexecutioncontext-structure"></a>IExecutionContext (Estructura)
Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IExecutionContext:: Dispatch](#dispatch)|El método que se llama cuando un proxy del subproceso empieza a ejecutarse un contexto de ejecución determinada. Debe ser la rutina del trabajador principal para su programador.|  
|[IExecutionContext:: GetId](#getid)|Devuelve un identificador único para el contexto de ejecución.|  
|[IExecutionContext:: GetProxy](#getproxy)|Devuelve una interfaz para el proxy del subproceso que se está ejecutando en este contexto.|  
|[IExecutionContext:: GetScheduler](#getscheduler)|Devuelve una interfaz al programador al que pertenece este contexto de ejecución.|  
|[IExecutionContext:: SetProxy](#setproxy)|Asocia a un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de que inicia la ejecución del contexto `Dispatch` método.|  
  
## <a name="remarks"></a>Comentarios  
 Si está implementando un programador personalizado que interactúa con el Administrador de recursos del Runtime de simultaneidad, debe implementar la `IExecutionContext` interfaz. Los subprocesos creados por el Administrador de recursos trabajan en nombre de su programador ejecutando el `IExecutionContext::Dispatch` método.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IExecutionContext`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dispatch"></a>IExecutionContext:: Dispatch (método)  
 El método que se llama cuando un proxy del subproceso empieza a ejecutarse un contexto de ejecución determinada. Debe ser la rutina del trabajador principal para su programador.  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pDispatchState`  
 Un puntero al estado en el que está siendo enviado este contexto de ejecución. Para obtener más información sobre el estado del envío, consulte [DispatchState](dispatchstate-structure.md).  
  
##  <a name="getid"></a>IExecutionContext:: GetId (método)  
 Devuelve un identificador único para el contexto de ejecución.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador entero único.  
  
### <a name="remarks"></a>Comentarios  
 Debe utilizar el método `GetExecutionContextId` para obtener un identificador único para el objeto que implementa el `IExecutionContext` interfaz antes de utilizar la interfaz como un parámetro a los métodos proporcionados por el Administrador de recursos. Se espera que devuelva el mismo identificador cuando el `GetId` se invoca la función.  
  
 Un identificador obtenido de un origen diferente podría provocar un comportamiento indefinido.  
  
##  <a name="getproxy"></a>IExecutionContext:: GetProxy (método)  
 Devuelve una interfaz para el proxy del subproceso que se está ejecutando en este contexto.  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Interfaz `IThreadProxy`. Si no se ha inicializado el proxy del subproceso del contexto de ejecución con una llamada a `SetProxy`, la función debe devolver `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Invocará el Administrador de recursos del `SetProxy` método en un contexto de ejecución con un `IThreadProxy` interfaz como un parámetro, antes de escribir el `Dispatch` método en el en el contexto. Se espera que almacene este argumento y lo devuelva en llamadas a `GetProxy()`.  
  
##  <a name="getscheduler"></a>IExecutionContext:: GetScheduler (método)  
 Devuelve una interfaz al programador al que pertenece este contexto de ejecución.  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Interfaz `IScheduler`.  
  
### <a name="remarks"></a>Comentarios  
 Es necesario inicializar el contexto de ejecución con válido `IScheduler` interfaz antes de utilizarla como un parámetro a los métodos proporcionados por el Administrador de recursos.  
  
##  <a name="setproxy"></a>IExecutionContext:: SetProxy (método)  
 Asocia a un proxy del subproceso a este contexto de ejecución. El proxy del subproceso asociado invoca este método justo antes de que inicia la ejecución del contexto `Dispatch` método.  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pThreadProxy`  
 Una interfaz para el proxy del subproceso que se va a escribir el `Dispatch` método en este contexto de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Se espera que guarde el parámetro `pThreadProxy` y lo devuelva en una llamada a la `GetProxy` (método). El Administrador de recursos garantiza que el proxy del subproceso asociado al contexto de ejecución no cambiará mientras se ejecuta el proxy del subproceso del `Dispatch` (método).  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IScheduler (estructura)](ischeduler-structure.md)   
 [IThreadProxy (estructura)](ithreadproxy-structure.md)

