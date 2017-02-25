---
title: "promise (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::promise"
dev_langs: 
  - "C++"
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# promise (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un *proveedor asincrónico*.  
  
## Sintaxis  
  
```  
template<class Ty>  
class promise;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[promise::promise \(Constructor\)](../Topic/promise::promise%20Constructor.md)|Construye un objeto `promise`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[promise::get\_future \(Método\)](../Topic/promise::get_future%20Method.md)|Devuelve un [futuro](../standard-library/future-class.md) asociado a este compromiso.|  
|[promise::set\_exception \(Método\)](../Topic/promise::set_exception%20Method.md)|Establece de forma atómica el resultado de este compromiso para indicar una excepción.|  
|[promise::set\_exception\_at\_thread\_exit \(Método\)](../Topic/promise::set_exception_at_thread_exit%20Method.md)|Establece de forma atómica el resultado de este compromiso para indicar una excepción y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual \(normalmente al salir del subproceso\).|  
|[promise::set\_value \(Método\)](../Topic/promise::set_value%20Method.md)|Establece de forma atómica el resultado de este compromiso para indicar un valor.|  
|[promise::set\_value\_at\_thread\_exit \(Método\)](../Topic/promise::set_value_at_thread_exit%20Method.md)|Establece de forma atómica el resultado de este compromiso para indicar un valor y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual \(normalmente al salir del subproceso\).|  
|[promise::swap \(Método\)](../Topic/promise::swap%20Method.md)|Intercambia el *estado asincrónico asociado* de este compromiso con el de un objeto promise especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[promise::operator\= \(Operador\)](../Topic/promise::operator=%20Operator.md)|Asignación del estado compartido de este objeto promise.|  
  
## Jerarquía de herencia  
 `promise`  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)