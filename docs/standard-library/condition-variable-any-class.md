---
title: "condition_variable_any (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "condition_variable/std::condition_variable_any"
dev_langs: 
  - "C++"
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# condition_variable_any (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice la clase `condition_variable_any` para esperar un evento que tenga cualquier tipo  `mutex`.  
  
## Sintaxis  
  
```  
class condition_variable_any;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[condition\_variable\_any::condition\_variable\_any \(Constructor\)](../Topic/condition_variable_any::condition_variable_any%20Constructor.md)|Construye un objeto `condition_variable_any`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[condition\_variable\_any::notify\_all \(Método\)](../Topic/condition_variable_any::notify_all%20Method.md)|Desbloquea todos los subprocesos que están esperando el objeto `condition_variable_any`.|  
|[condition\_variable\_any::notify\_one \(Método\)](../Topic/condition_variable_any::notify_one%20Method.md)|Desbloquea uno de los subprocesos que están esperando el objeto `condition_variable_any`.|  
|[condition\_variable\_any::wait \(Método\)](../Topic/condition_variable_any::wait%20Method.md)|Bloquea un subproceso.|  
|[condition\_variable\_any::wait\_for \(Método\)](../Topic/condition_variable_any::wait_for%20Method.md)|Bloquea un subproceso y establece un intervalo de tiempo después del cual el subproceso se desbloquea.|  
|[condition\_variable\_any::wait\_until \(Método\)](../Topic/condition_variable_any::wait_until%20Method.md)|Bloquea un subproceso y establece un punto máximo en el tiempo en el que el subproceso se desbloquea.|  
  
## Requisitos  
 **Encabezado:** condition\_variable  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<condition\_variable\>](../standard-library/condition-variable.md)