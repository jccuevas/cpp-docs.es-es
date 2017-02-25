---
title: "cancellation_token_source (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pplcancellation_token/concurrency::cancellation_token_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_source (clase)"
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# cancellation_token_source (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `cancellation_token_source` representa la capacidad para cancelar una operación que se puede cancelar.  
  
## Sintaxis  
  
```  
class cancellation_token_source;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token\_source::cancellation\_token\_source \(Constructor\)](../Topic/cancellation_token_source::cancellation_token_source%20Constructor.md)|Sobrecargado.  Construye un nuevo objeto `cancellation_token_source`.  El origen se puede usar para marcar la cancelación de una operación cancelable.|  
|[cancellation\_token\_source::~cancellation\_token\_source \(Destructor\)](../Topic/cancellation_token_source::~cancellation_token_source%20Destructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token\_source::cancel \(Método\)](../Topic/cancellation_token_source::cancel%20Method.md)|Cancela el token.  Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.|  
|[cancellation\_token\_source::create\_linked\_source \(Método\)](../Topic/cancellation_token_source::create_linked_source%20Method.md)|Sobrecargado.  Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.|  
|[cancellation\_token\_source::get\_token \(Método\)](../Topic/cancellation_token_source::get_token%20Method.md)|Devuelve un token de cancelación asociado a este origen.  El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token\_source::operator\!\= \(Operador\)](../Topic/cancellation_token_source::operator!=%20Operator.md)||  
|[cancellation\_token\_source::operator\= \(Operador\)](../Topic/cancellation_token_source::operator=%20Operator.md)||  
|[cancellation\_token\_source::operator\=\= \(Operador\)](../Topic/cancellation_token_source::operator==%20Operator.md)||  
  
## Jerarquía de herencia  
 `cancellation_token_source`  
  
## Requisitos  
 **Encabezado:** pplcancellation\_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)