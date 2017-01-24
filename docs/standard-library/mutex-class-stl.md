---
title: "mutex (Clase, STL) | Microsoft Docs"
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
  - "mutex/std::mutex"
dev_langs: 
  - "C++"
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: 11
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mutex (Clase, STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un *tipo de exclusión mutua*.  Los objetos de este tipo se pueden usar para aplicar la exclusión mutua dentro de un programa.  
  
## Sintaxis  
  
```  
class mutex;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[mutex::mutex \(Constructor, STL\)](../Topic/mutex::mutex%20Constructor%20\(STL\).md)|Construye un objeto `mutex`.|  
|[mutex::~mutex \(Destructor, STL\)](../Topic/mutex::~mutex%20Destructor%20\(STL\).md)|Libera todos los recursos utilizados por el objeto `mutex`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[mutex::lock \(Método, STL\)](../Topic/mutex::lock%20Method%20\(STL\).md)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|  
|[mutex::native\_handle \(método STL\)](../Topic/mutex::native_handle%20Method%20\(STL\).md)|Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua.|  
|[mutex::try\_lock \(Método, STL\)](../Topic/mutex::try_lock%20Method%20\(STL\).md)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|  
|[mutex::unlock \(Método, STL\)](../Topic/mutex::unlock%20Method%20\(STL\).md)|Libera la propiedad de `mutex`.|  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)