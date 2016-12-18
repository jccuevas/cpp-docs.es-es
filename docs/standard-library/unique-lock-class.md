---
title: "unique_lock (Clase) | Microsoft Docs"
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
  - "mutex/std::unique_lock"
dev_langs: 
  - "C++"
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unique_lock (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una plantilla que se pueden crear instancias para crear objetos que administran el bloqueo y desbloqueo de `mutex`.  
  
## Sintaxis  
  
```  
template<class Mutex>  
class unique_lock;  
```  
  
## Comentarios  
 El argumento `Mutex` de plantilla debe llamar a *un tipo mutex*.  
  
 Internamente, `unique_lock` almacena un puntero a un objeto asociado de `mutex` y a `bool` que indica si el subproceso actual posee `mutex`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`unique_lock::mutex_type`|Sinónimo del argumento `Mutex`de la plantilla.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unique\_lock::unique\_lock \(Constructor\)](../Topic/unique_lock::unique_lock%20Constructor.md)|Construye un objeto `unique_lock`.|  
|[unique\_lock::~unique\_lock \(Destructor\)](../Topic/unique_lock::~unique_lock%20Destructor.md)|Libera los recursos asociados al objeto de `unique_lock` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unique\_lock::lock \(Método\)](../Topic/unique_lock::lock%20Method.md)|Bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad de `mutex`asociado.|  
|[unique\_lock::mutex \(Método\)](../Topic/unique_lock::mutex%20Method.md)|Recupera el puntero almacenado a `mutex`asociado.|  
|[unique\_lock::owns\_lock \(Método\)](../Topic/unique_lock::owns_lock%20Method.md)|Especifica si el subproceso de llamada posee `mutex`asociado.|  
|[unique\_lock::release \(Método\)](../Topic/unique_lock::release%20Method.md)|Desasocia el objeto de `unique_lock` de objeto asociado de `mutex` .|  
|[unique\_lock::swap \(Método\)](../Topic/unique_lock::swap%20Method.md)|Cambie `mutex` y el estado asociados de la propiedad con el de un objeto especificado.|  
|[unique\_lock::try\_lock \(Método\)](../Topic/unique_lock::try_lock%20Method.md)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|  
|[unique\_lock::try\_lock\_for \(Método\)](../Topic/unique_lock::try_lock_for%20Method.md)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|  
|[unique\_lock::try\_lock\_until \(Método\)](../Topic/unique_lock::try_lock_until%20Method.md)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|  
|[unique\_lock::unlock \(Método\)](../Topic/unique_lock::unlock%20Method.md)|Propiedad de `mutex`asociado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unique\_lock::operator bool \(Operador\)](../Topic/unique_lock::operator%20bool%20Operator.md)|Especifica si el subproceso de la llamada tiene la propiedad de `mutex`asociado.|  
|[unique\_lock::operator\= \(Operador\)](../Topic/unique_lock::operator=%20Operator.md)|Copia el puntero almacenado de `mutex` y el estado asociado de la propiedad de un objeto especificado.|  
  
## Jerarquía de herencia  
 `unique_lock`  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)