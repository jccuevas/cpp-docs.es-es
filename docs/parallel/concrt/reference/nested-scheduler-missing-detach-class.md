---
title: nested_scheduler_missing_detach (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 0079fea0b157e194947931f88d1cb500167cb6e2
ms.lasthandoff: 02/24/2017

---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach (Clase)
Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[nested_scheduler_missing_detach (Constructor)](#ctor)|Sobrecargado. Construye un objeto `nested_scheduler_missing_detach`.|  
  
## <a name="remarks"></a>Comentarios  
 Se produce esta excepción cuando se anida un programador dentro de otro llamando a la `Attach` método de una `Scheduler` objeto en un contexto que ya es propiedad de o se adjunta a otro programador. El Runtime de simultaneidad produce esta excepción según la ocasión cuando puede detectar el escenario como ayuda para localizar el problema. No todas las instancias de no especifican la llamada la `CurrentScheduler::Detach` se garantiza que el método produce esta excepción.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-nestedschedulermissingdetach"></a><a name="ctor"></a>nested_scheduler_missing_detach 

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

