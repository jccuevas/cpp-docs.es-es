---
title: nested_scheduler_missing_detach (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs: C++
helpviewer_keywords: nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a499467962c8393cc8fe64136fea422a85ef8aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach (Clase)
Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[nested_scheduler_missing_detach)](#ctor)|Sobrecargado. Construye un objeto `nested_scheduler_missing_detach`.|  
  
## <a name="remarks"></a>Comentarios  
 Se produce esta excepción cuando se anida un programador dentro de otra mediante una llamada a la `Attach` método de una `Scheduler` objeto en un contexto que ya es propiedad de o adjunta a otro programador. El Runtime de simultaneidad produce esta excepción según la ocasión cuando puede detectar el escenario como una ayuda para localizar el problema. No todas las instancias de olvida llamar a la `CurrentScheduler::Detach` método se garantiza que producen esta excepción.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>nested_scheduler_missing_detach) 

 Construye un objeto `nested_scheduler_missing_detach`.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Scheduler (clase)](scheduler-class.md)
