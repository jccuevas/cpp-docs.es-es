---
title: IUMSCompletionList (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 65655e4e03a7b187e0bbadbd576bc088bb57f7c8
ms.lasthandoff: 03/17/2017

---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList (Estructura)
Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IUMSCompletionList:: GetUnblockNotifications](#getunblocknotifications)|Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado proxy se han desbloqueado desde la última vez que este método se ha invocado.|  
  
## <a name="remarks"></a>Comentarios  
 Un programador debe ser extraordinariamente cuidadoso sobre qué acciones se realizan después de usar esta interfaz para los elementos de la lista de finalización de la cola. Los elementos se deben colocar en la lista del programador de contextos ejecutables y ser accesible normalmente tan pronto como sea posible. Es muy posible que uno de los elementos quitados se ha concedido la propiedad de un bloqueo arbitrario. El programador no puede hacer llamadas de función arbitraria que se pueden bloquear entre la llamada a elementos de la cola y la colocación de los elementos en una lista que puede obtenerse generalmente desde dentro del programador.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getunblocknotifications"></a>IUMSCompletionList:: GetUnblockNotifications (método)  
 Recupera una cadena de `IUMSUnblockNotification` interfaces que representan los contextos de ejecución cuyo subproceso asociado proxy se han desbloqueado desde la última vez que este método se ha invocado.  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena de `IUMSUnblockNotification` interfaces.  
  
### <a name="remarks"></a>Comentarios  
 Las notificaciones devueltas no son válidas una vez que se reprograman los contextos de ejecución.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [IUMSScheduler (estructura)](iumsscheduler-structure.md)   
 [IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)

