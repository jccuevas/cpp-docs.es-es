---
title: "recursive_timed_mutex (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::recursive_timed_mutex"
dev_langs: 
  - "C++"
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# recursive_timed_mutex (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa *un tipo agotó la exclusión mutua*.  Los objetos de este tipo se utilizan para aplicar la exclusión mutua mediante el bloqueo limitado en tiempo dentro de un programa.  A diferencia de los objetos de [timed\_mutex](../standard-library/timed-mutex-class.md)escrito, el efecto de los métodos de bloqueo de llamada para los objetos de `recursive_timed_mutex` esté bien definido.  
  
## Sintaxis  
  
```  
class recursive_timed_mutex;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[recursive\_timed\_mutex::recursive\_timed\_mutex \(Constructor\)](../Topic/recursive_timed_mutex::recursive_timed_mutex%20Constructor.md)|Construye un objeto de `recursive_timed_mutex` que no está bloqueado.|  
|[recursive\_timed\_mutex::~recursive\_timed\_mutex \(Destructor\)](../Topic/recursive_timed_mutex::~recursive_timed_mutex%20Destructor.md)|Libera los recursos utilizados por el objeto de `recursive_timed_mutex` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[recursive\_timed\_mutex::lock \(Método\)](../Topic/recursive_timed_mutex::lock%20Method.md)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|  
|[recursive\_timed\_mutex::try\_lock \(Método\)](../Topic/recursive_timed_mutex::try_lock%20Method.md)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|  
|[recursive\_timed\_mutex::try\_lock\_for \(Método\)](../Topic/recursive_timed_mutex::try_lock_for%20Method.md)|Intente obtener la propiedad de `mutex` para un intervalo de tiempo especificado.|  
|[recursive\_timed\_mutex::try\_lock\_until \(Método\)](../Topic/recursive_timed_mutex::try_lock_until%20Method.md)|Intente obtener la propiedad de `mutex` hasta un momento específico.|  
|[recursive\_timed\_mutex::unlock \(Método\)](../Topic/recursive_timed_mutex::unlock%20Method.md)|Libera la propiedad de `mutex`.|  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)