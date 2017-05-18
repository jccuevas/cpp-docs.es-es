---
title: missing_wait (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 70b1c77660992b33de2204fd4f4221ed6e957e21
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="missingwait-class"></a>missing_wait (Clase)
Esta clase describe una excepción que se produce cuando todavía existen tareas programadas para un objeto `task_group` o `structured_task_group` en el momento que el destructor de objeto se ejecuta. Nunca se producirá esta excepción si el destructor se alcanza debido al desenredo de pila como el resultado de una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[missing_wait](#ctor)|Sobrecargado. Construye un objeto `missing_wait`.|  
  
## <a name="remarks"></a>Comentarios  
 Está ausente del flujo de excepción, usted es responsable de llamar a cualquiera el `wait` o `run_and_wait` método de una `task_group` o `structured_task_group` objeto antes de permitir que ese objeto se destruya. El runtime produce esta excepción como una indicación de que se olvidó de llamar el `wait` o `run_and_wait` (método).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>missing_wait 

 Construye un objeto `missing_wait`.  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [task_group (clase)](task-group-class.md)   
 [esperar](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group (clase)](structured-task-group-class.md)

