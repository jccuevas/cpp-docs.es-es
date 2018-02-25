---
title: invalid_scheduler_policy_key Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ecb6525ec8d5d02cdb8bd9edfeb7ff937847bae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key (Clase)
Esta clase describe una excepción que se produce cuando una clave no válida o desconocida se pasa a un constructor de objeto `SchedulerPolicy`, o el método `SetPolicyValue` de un objeto `SchedulerPolicy` se pasa a una clave que se debe cambiar mediante otros medios como el método `SetConcurrencyLimits`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_scheduler_policy_key : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid_scheduler_policy_key](#ctor)|Sobrecargado. Construye un objeto `invalid_scheduler_policy_key`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a> invalid_scheduler_policy_key 

 Construye un objeto `invalid_scheduler_policy_key`.  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [SchedulerPolicy (clase)](schedulerpolicy-class.md)
