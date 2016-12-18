---
title: "thread (Clase) | Microsoft Docs"
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
  - "thread/std::thread"
dev_langs: 
  - "C++"
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# thread (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define un objeto que se utiliza para observar y administrar un subproceso de ejecución dentro de una aplicación.  
  
## Sintaxis  
  
```  
class thread;  
```  
  
## Comentarios  
 Se puede utilizar un objeto `thread` para observar y administrar un subproceso de ejecución dentro de una aplicación.  Un objeto thread creado con el constructor predeterminado no está asociado a ningún subproceso de ejecución.  Un objeto thread construido mediante un objeto al que se puede llamar crea un nuevo subproceso de ejecución y llama al objeto al que se puede llamar en ese subproceso.  Los objetos thread se pueden mover pero no copiar.  Por tanto, un subproceso de ejecución solo se puede asociar a un objeto thread.  
  
 Cada subproceso de ejecución tiene un identificador único de tipo `thread::id`.  La función `this_thread::get_id` devuelve el identificador del subproceso que realiza la llamada.  La función miembro `thread::get_id` devuelve el identificador del subproceso administrado por un objeto thread.  Para un objeto thread creado con el constructor predeterminado, el método `thread::get_id` devuelve un objeto cuyo valor es el mismo para todos los objetos thread creados con el constructor predeterminado y diferente del valor devuelto por `this_thread::get_id` para cualquier subproceso de ejecución que se pueda unir en el momento de la llamada.  
  
## Miembros  
  
### Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread::id \(Clase\)](../Topic/thread::id%20Class.md)|Identifica de forma única el subproceso asociado.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread::thread \(Constructor\)](../Topic/thread::thread%20Constructor.md)|Construye un objeto `thread`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread::detach \(Método\)](../Topic/thread::detach%20Method.md)|Desasocia el subproceso asociado del objeto `thread`.|  
|[thread::get\_id \(Método\)](../Topic/thread::get_id%20Method.md)|Devuelve el identificador único del subproceso asociado.|  
|[thread::hardware\_concurrency \(Método\)](../Topic/thread::hardware_concurrency%20Method.md)|Estático.  Devuelve una estimación del número de contextos de subprocesos de hardware.|  
|[thread::join \(Método\)](../Topic/thread::join%20Method.md)|Se bloquea hasta que el subproceso asociado se completa.|  
|[thread::joinable \(Método\)](../Topic/thread::joinable%20Method.md)|Especifica si se puede unir el subproceso asociado.|  
|[thread::native\_handle \(Método\)](../Topic/thread::native_handle%20Method.md)|Devuelve el tipo específico de la implementación que representa el identificador de subproceso.|  
|[thread::swap \(Método\)](../Topic/thread::swap%20Method.md)|Intercambia el estado de objeto con un objeto `thread` especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[thread::operator\= \(Operador\)](../Topic/thread::operator=%20Operator.md)|Asocia un subproceso al objeto `thread` actual.|  
  
## Requisitos  
 **Encabezado:** thread  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread\>](../standard-library/thread.md)