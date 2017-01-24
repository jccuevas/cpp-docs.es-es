---
title: "recursive_mutex (Clase) | Microsoft Docs"
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
  - "mutex/std::recursive_mutex"
dev_langs: 
  - "C++"
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: 9
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# recursive_mutex (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un *tipo de exclusión mutua*.  A diferencia de [mutex](../standard-library/mutex-class-stl.md), el comportamiento de llamadas a bloquear los métodos de los objetos bloqueados ya esté bien definido.  
  
## Sintaxis  
  
```  
class recursive_mutex;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[recursive\_mutex::recursive\_mutex \(Constructor\)](../Topic/recursive_mutex::recursive_mutex%20Constructor.md)|Construye un objeto `recursive_mutex`.|  
|[recursive\_mutex::~recursive\_mutex \(Destructor\)](../Topic/recursive_mutex::~recursive_mutex%20Destructor.md)|Libera los recursos utilizados por el objeto de `recursive_mutex` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[recursive\_mutex::lock \(Método\)](../Topic/recursive_mutex::lock%20Method.md)|Bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad mutex.|  
|[recursive\_mutex::try\_lock \(Método\)](../Topic/recursive_mutex::try_lock%20Method.md)|Intente obtener la propiedad mutex sin bloquearse.|  
|[recursive\_mutex::unlock \(Método\)](../Topic/recursive_mutex::unlock%20Method.md)|Propiedad de las versiones de exclusión mutua.|  
  
## Requisitos  
 **Encabezado:** mutex  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex\>](../standard-library/mutex.md)