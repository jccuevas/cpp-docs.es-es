---
title: invalid_scheduler_policy_thread_specification (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53e2d5ba1c8fd4d8afd4af88c45069b34717a66c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification (Clase)
Esta clase describe una excepción que se produce cuando se realiza un intento para establecer los límites de simultaneidad de un objeto `SchedulerPolicy`, de tal forma que el valor de la clave `MinConcurrency` es menor que el valor de la clave `MaxConcurrency`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_scheduler_policy_thread_specification : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Sobrecargado. Construye un objeto `invalid_scheduler_policy_value`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification) 

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
