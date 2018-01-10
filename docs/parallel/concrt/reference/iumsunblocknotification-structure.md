---
title: IUMSUnblockNotification (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs: C++
helpviewer_keywords: IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3febe10f7c71e1c1d478dd6f6b6f565c4134e033
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification (Estructura)
Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSUnblockNotification:: GetContext](#getcontext)|Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Cuando se devuelve este método y el contexto de ejecución subyacente se ha vuelto a programar mediante una llamada a la `IThreadProxy::SwitchTo` método, esta interfaz ya no es válida.|  
|[IUMSUnblockNotification:: GetNextUnblockNotification](#getnextunblocknotification)|Devuelve el siguiente `IUMSUnblockNotification` interfaz en la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getcontext"></a>IUMSUnblockNotification:: GetContext (método)  
 Devuelve el `IExecutionContext` interfaz para el contexto de ejecución asociado con el proxy del subproceso que se ha desbloqueado. Cuando se devuelve este método y el contexto de ejecución subyacente se ha vuelto a programar mediante una llamada a la `IThreadProxy::SwitchTo` método, esta interfaz ya no es válida.  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `IExecutionContext` interfaz para el contexto de ejecución a un proxy del subproceso que se ha desbloqueado.  
  
##  <a name="getnextunblocknotification"></a>IUMSUnblockNotification:: GetNextUnblockNotification (método)  
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
