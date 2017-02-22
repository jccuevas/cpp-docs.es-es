---
title: "lock_guard (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "mutex/std::lock_guard"
dev_langs: 
  - "C++"
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# lock_guard (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una plantilla que se pueden crear instancias para crear un objeto cuyo destructor unblock `mutex`.  
  
## Sintaxis  
  
```  
template<class Mutex>  
class lock_guard;  
```  
  
## Comentarios  
 El argumento `Mutex` de plantilla debe llamar a *un tipo mutex*.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`lock_guard::mutex_type`|Sinónimo del argumento `Mutex`de la plantilla.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[lock\_guard::lock\_guard \(Constructor\)](../Topic/lock_guard::lock_guard%20Constructor.md)|Construye un objeto `lock_guard`.|  
|[lock\_guard::~lock\_guard \(Destructor\)](../Topic/lock_guard::~lock_guard%20Destructor.md)|Desbloquea `mutex` que se pasó al constructor.|  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)