---
title: IUMSCompletionList (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee957355510a2f62f5317d330403dc246ee8f2e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList (Estructura)
Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSCompletionList:: GetUnblockNotifications](#getunblocknotifications)|Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado proxies han desbloqueado desde la última vez que este método se invoca.|  
  
## <a name="remarks"></a>Comentarios  
 Un programador debe ser extraordinariamente cuidadoso sobre qué acciones se realizan después de usar esta interfaz para quitar elementos de la lista de finalización de la cola. Los elementos se deben colocar en la lista del programador de contextos ejecutables y ser accesibles a nivel general tan pronto como sea posible. Es muy posible que uno de los elementos quitados de la cola se ha concedido la propiedad de un bloqueo arbitrario. El programador no puede realizar ninguna llamada de función arbitraria que se puede bloquear entre la llamada para quitar elementos de la cola y la colocación de los elementos en una lista que generalmente accesibles desde dentro del programador.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getunblocknotifications"></a>  IUMSCompletionList:: GetUnblockNotifications (método)  
 Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado proxies han desbloqueado desde la última vez que este método se invoca.  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena de `IUMSUnblockNotification` interfaces.  
  
### <a name="remarks"></a>Comentarios  
 Las notificaciones devueltas no son válidas una vez que se vuelve a programar los contextos de ejecución.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IUMSScheduler (estructura)](iumsscheduler-structure.md)   
 [IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)
