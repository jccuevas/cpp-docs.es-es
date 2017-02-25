---
title: "scheduler_ptr (Estructura) (Runtime de simultaneidad) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pplinterface/concurrency::scheduler_ptr"
dev_langs: 
  - "C++"
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# scheduler_ptr (Estructura) (Runtime de simultaneidad)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa un puntero a un programador.  Esta clase existe para permitir la especificación de una duración compartida mediante shared\_ptr o simplemente permitir una referencia sin formato mediante un puntero sin formato.  
  
## Sintaxis  
  
```  
struct scheduler_ptr;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_ptr::scheduler\_ptr \(Constructor\) \(Runtime de simultaneidad\)](../Topic/scheduler_ptr::scheduler_ptr%20Constructor%20\(Concurrency%20Runtime\).md)|Sobrecargado.  Crea un puntero de programador que va de shared\_ptr al programador|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_ptr::get \(Método\) \(Runtime de simultaneidad\)](../Topic/scheduler_ptr::get%20Method%20\(Concurrency%20Runtime\).md)|Devuelve el puntero sin formato al programador|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_ptr::operator \(Operador booleano\) \(Runtime de simultaneidad\)](../Topic/scheduler_ptr::operator%20bool%20Operator%20\(Concurrency%20Runtime\).md)|Prueba si el puntero del programador no es null|  
|[Operador scheduler\_ptr::operator\-\> \(Runtime de simultaneidad\)](../Topic/scheduler_ptr::operator-%3E%20Operator%20\(Concurrency%20Runtime\).md)|Se comporta como un puntero|  
  
## Jerarquía de herencia  
 `scheduler_ptr`  
  
## Requisitos  
 **Encabezado:** pplinterface.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)