---
title: IUMSUnblockNotification (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 19
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 6fba6c36987107e2e8100c8b296c279592220682
ms.lasthandoff: 02/24/2017

---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification (Estructura)
Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IUMSUnblockNotification:: GetContext (método)](#getcontext)|Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Cuando se devuelve este método y el contexto de ejecución subyacente se ha reprogramado a través de una llamada a la `IThreadProxy::SwitchTo` (método), esta interfaz ya no es válida.|  
|[IUMSUnblockNotification:: GetNextUnblockNotification (método)](#getnextunblocknotification)|Devuelve el siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namegetcontexta--iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMSUnblockNotification:: GetContext (método)  
 Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Cuando se devuelve este método y el contexto de ejecución subyacente se ha reprogramado a través de una llamada a la `IThreadProxy::SwitchTo` (método), esta interfaz ya no es válida.  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `IExecutionContext` interfaz para el contexto de ejecución a un proxy del subproceso que se ha desbloqueado.  
  
##  <a name="a-namegetnextunblocknotificationa--iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMSUnblockNotification:: GetNextUnblockNotification (método)  
 Devuelve el siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IUMSScheduler (estructura)](iumsscheduler-structure.md)   
 [IUMSCompletionList (estructura)](iumscompletionlist-structure.md)

