---
title: "completion_future (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::completion_future"
dev_langs: 
  - "C++"
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# completion_future (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa un futuro que corresponde a la operación asincrónica de C\+\+ AMP.  
  
## Sintaxis  
  
```  
class completion_future;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[completion\_future::completion\_future \(Constructor\)](../Topic/completion_future::completion_future%20Constructor.md)|Inicializa una nueva instancia de la clase `completion_future`.|  
|[completion\_future::~completion\_future \(Destructor\)](../Topic/completion_future::~completion_future%20Destructor.md)|Destruye el objeto `completion_future`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[completion\_future::get \(Método\)](../Topic/completion_future::get%20Method.md)|Espera hasta que se completa la operación asincrónica asociada.|  
|[completion\_future::then \(Método\)](../Topic/completion_future::then%20Method.md)|Encadena un objeto de función de llamada de devolución al objeto `completion_future` que se ejecuta cuando la operación asincrónica asociada finaliza la ejecución.|  
|[completion\_future::to\_task \(Método\)](../Topic/completion_future::to_task%20Method.md)|Devuelve un objeto `task` que corresponde a la operación asíncrona asociada.|  
|[completion\_future::valid \(Método\)](../Topic/completion_future::valid%20Method.md)|Obtiene un valor booleano que indica si el objeto está asociado a una operación asincrónica.|  
|[completion\_future::wait \(Método\)](../Topic/completion_future::wait%20Method.md)|Bloquea hasta que la operación asíncrona asociada se completa.|  
|[completion\_future::wait\_for \(Método\)](../Topic/completion_future::wait_for%20Method.md)|Bloquea hasta que se completa la operación asíncrona asociada o hasta que el tiempo especificado por `_Rel_time` ha transcurrido.|  
|[completion\_future::wait\_until \(Método\)](../Topic/completion_future::wait_until%20Method.md)|Bloquea hasta que se completa la operación asincrónica asociada o hasta que la hora actual supera el valor especificado por `_Abs_time`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[completion\_future::operator std::shared\_future\<void\> \(Operador\)](../Topic/completion_future::operator%20std::shared_future%3Cvoid%3E%20Operator.md)|Convierte implícitamente el objeto `completion_future` a un objeto `std::shared_future` .|  
|[completion\_future::operator\= \(Operador\)](../Topic/completion_future::operator=%20Operator.md)|Copia el contenido del objeto especificado `completion_future` en este.|  
  
## Jerarquía de herencia  
 `completion_future`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)