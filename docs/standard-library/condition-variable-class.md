---
title: "condition_variable (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "condition_variable/std::condition_variable"
dev_langs: 
  - "C++"
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
caps.latest.revision: 16
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# condition_variable (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice la clase `condition_variable` para esperar un evento cuando tenga un `mutex` de tipo `unique_lock<mutex>`.  Los objetos de este tipo pueden tener un rendimiento mejor que los objetos de tipo [condition\_variable\_any\<unique\_lock\<mutex\>\>](../standard-library/condition-variable-any-class.md).  
  
## Sintaxis  
  
```  
class condition_variable;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[condition\_variable::condition\_variable \(Constructor\)](../Topic/condition_variable::condition_variable%20Constructor.md)|Construye un objeto `condition_variable`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[condition\_variable::native\_handle \(Método\)](../Topic/condition_variable::native_handle%20Method.md)|Devuelve el tipo específico de la implementación que representa el identificador condition\_variable.|  
|[condition\_variable::notify\_all \(Método\)](../Topic/condition_variable::notify_all%20Method.md)|Desbloquea todos los subprocesos que están esperando el objeto `condition_variable`.|  
|[condition\_variable::notify\_one \(Método\)](../Topic/condition_variable::notify_one%20Method.md)|Desbloquea uno de los subprocesos que están esperando el objeto `condition_variable`.|  
|[condition\_variable::wait \(Método\)](../Topic/condition_variable::wait%20Method.md)|Bloquea un subproceso.|  
|[condition\_variable::wait\_for \(Método\)](../Topic/condition_variable::wait_for%20Method.md)|Bloquea un subproceso y establece un intervalo de tiempo después del cual el subproceso se desbloquea.|  
|[condition\_variable::wait\_until \(Método\)](../Topic/condition_variable::wait_until%20Method.md)|Bloquea un subproceso y establece un punto máximo en el tiempo en el que el subproceso se desbloquea.|  
  
## Requisitos  
 **Encabezado:** condition\_variable  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)