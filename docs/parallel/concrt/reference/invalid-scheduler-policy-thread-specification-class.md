---
title: invalid_scheduler_policy_thread_specification (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
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
ms.openlocfilehash: d9b49f65d8b862a7b85cdf3e09137f326fa8a1fa
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification (Clase)
Esta clase describe una excepción que se produce cuando se realiza un intento para establecer los límites de simultaneidad de un objeto `SchedulerPolicy`, de tal forma que el valor de la clave `MinConcurrency` es menor que el valor de la clave `MaxConcurrency`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_scheduler_policy_thread_specification : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[invalid_scheduler_policy_thread_specification] (no válido-programador-directiva-valor-class.md #ctor|Sobrecargado. Construye un objeto `invalid_scheduler_policy_value`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
##  <a name="ctor"></a>invalid_scheduler_policy_thread_specification 

 Construye un objeto `invalid_scheduler_policy_value`.  
  
```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  

## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [SchedulerPolicy (clase)](schedulerpolicy-class.md)

