---
title: IUMSScheduler (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs:
- C++
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
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
ms.openlocfilehash: 58ca59224b5d9cdeb282562349642736a1b22c74
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="iumsscheduler-structure"></a>IUMSScheduler (Estructura)
Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario (UMS). El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS. La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IUMSScheduler:: SetCompletionList](#setcompletionlist)|Asigna un `IUMSCompletionList` interfaz a un programador de subprocesos UMS.|  
  
## <a name="remarks"></a>Comentarios  
 Si está implementando un programador personalizado que comunica con el Administrador de recursos, y desea que los subprocesos UMS que se va a pasar a su programador en lugar de subprocesos de Win32 ordinarios, debería proporcionar una implementación de la `IUMSScheduler` interfaz. Además, debe establecer el valor de directiva de la clave de directiva de programador `SchedulerKind` como `UmsThreadDefault`. Si la directiva especifica el subproceso UMS, el `IScheduler` interfaz que se pasa como un parámetro a la [IResourceManager:: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) método debe ser un `IUMSScheduler` interfaz.  
  
 El Administrador de recursos es capaz de pasar subprocesos UMS sólo en sistemas operativos que tienen la característica UMS. sistemas operativos de 64 bits con versión de Windows 7 y versiones posteriores admiten los subprocesos UMS. Si crea una directiva del programador con el `SchedulerKind` clave establecida en el valor `UmsThreadDefault` y la plataforma subyacente no admite UMS, el valor de la `SchedulerKind` clave de esa directiva se cambiará al valor `ThreadScheduler`. Se debería volver leer siempre este valor de directiva antes de esperar recibir subprocesos UMS.  
  
 La `IUMSScheduler` interfaz es uno de los extremos de un canal bidireccional de comunicación entre un programador y el Administrador de recursos. El otro extremo está representado por la `IResourceManager` y `ISchedulerProxy` , las interfaces que se implementan mediante el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="setcompletionlist"></a>IUMSScheduler:: SetCompletionList (método)  
 Asigna un `IUMSCompletionList` interfaz a un programador de subprocesos UMS.  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `pCompletionList`  
 La interfaz de la lista de finalización para el programador. Hay una sola lista por programador.  
  
### <a name="remarks"></a>Comentarios  
 El Administrador de recursos invocará este método en un programador que especifica los subprocesos UMS, después de que el programador ha solicitado una asignación inicial de los recursos. El programador puede utilizar el `IUMSCompletionList` interfaz para determinar cuándo se ha desbloqueado proxy del subproceso UMS. Solo es válida para tener acceso a esta interfaz desde un proxy del subproceso se ejecuta en una raíz del procesador virtual asignada al programador UMS.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [IScheduler (estructura)](ischeduler-structure.md)   
 [IUMSCompletionList (estructura)](iumscompletionlist-structure.md)   
 [IResourceManager (estructura)](iresourcemanager-structure.md)

