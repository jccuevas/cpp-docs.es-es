---
title: invalid_multiple_scheduling (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs: C++
helpviewer_keywords: invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa021ec655162cb75837ac1475e5cb9094f79fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling (Clase)
Esta clase describe una excepción que se produce cuando un objeto `task_handle` se programa varias veces mediante el método `run` de un objeto `task_group` o `structured_task_group` sin una llamada que se interponga a los métodos `wait` o `run_and_wait`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid_multiple_scheduling)](#ctor)|Sobrecargado. Construye un objeto `invalid_multiple_scheduling`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>invalid_multiple_scheduling) 

 Construye un objeto `invalid_multiple_scheduling`.  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [task_handle (clase)](task-handle-class.md)   
 [task_group (clase)](task-group-class.md)   
 [ejecutar](task-group-class.md)   
 [espera](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group (clase)](structured-task-group-class.md)
