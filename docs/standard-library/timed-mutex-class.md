---
title: "timed_mutex (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::timed_mutex"
dev_langs: 
  - "C++"
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# timed_mutex (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa *un tipo agotó la exclusión mutua*.  Los objetos de este tipo se utilizan para aplicar la exclusión mutua con el bloqueo limitado en tiempo dentro de un programa.  
  
## Sintaxis  
  
```  
class timed_mutex;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[timed\_mutex::timed\_mutex \(Constructor\)](../Topic/timed_mutex::timed_mutex%20Constructor.md)|Construye un objeto de `timed_mutex` que no está bloqueado.|  
|[timed\_mutex::~timed\_mutex \(Destructor\)](../Topic/timed_mutex::~timed_mutex%20Destructor.md)|Libera los recursos utilizados por el objeto de `timed_mutex` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[timed\_mutex::lock \(Método\)](../Topic/timed_mutex::lock%20Method.md)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|  
|[timed\_mutex::try\_lock \(Método\)](../Topic/timed_mutex::try_lock%20Method.md)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|  
|[timed\_mutex::try\_lock\_for \(Método\)](../Topic/timed_mutex::try_lock_for%20Method.md)|Intente obtener la propiedad de `mutex` para un intervalo de tiempo especificado.|  
|[timed\_mutex::try\_lock\_until \(Método\)](../Topic/timed_mutex::try_lock_until%20Method.md)|Intente obtener la propiedad de `mutex` hasta un momento específico.|  
|[timed\_mutex::unlock \(Método\)](../Topic/timed_mutex::unlock%20Method.md)|Libera la propiedad de `mutex`.|  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)