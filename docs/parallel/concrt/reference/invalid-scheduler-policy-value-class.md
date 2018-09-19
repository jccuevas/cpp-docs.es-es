---
title: invalid_scheduler_policy_value (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae46d9f9de26e80a97d4ea2e9a692caec3445c75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068161"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value (Clase)
Esta clase describe una excepción que se produce cuando una clave de directiva de un objeto `SchedulerPolicy` se establece en un valor no válido para esa clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Sobrecargado. Construye un objeto `invalid_scheduler_policy_value`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value) 

 Construye un objeto `invalid_scheduler_policy_value`.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Parámetros  
*_Cuerpo*<br/>
Mensaje descriptivo del error.  
  

## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [SchedulerPolicy (clase)](schedulerpolicy-class.md)
