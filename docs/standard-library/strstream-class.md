---
title: "strstream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::strstream"
  - "strstream"
  - "std.strstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstream (clase)"
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# strstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción y la extracción de objetos codificados y elementos usando un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## Sintaxis  
  
```  
  
class strstream : public iostream  
  
```  
  
## Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso.  Considere el uso de [stringstream](../Topic/stringstream.md) o [wstringstream](../Topic/wstringstream.md) en su lugar.  
  
### Constructores  
  
|||  
|-|-|  
|[strstream](../Topic/strstream::strstream.md)|Construye un objeto de tipo `strstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[freeze](../Topic/strstream::freeze.md)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|  
|[pcount](../Topic/strstream::pcount.md)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|  
|[rdbuf](../Topic/strstream::rdbuf.md)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](../Topic/strstream::str.md)|Llama a [freeze](../Topic/strstreambuf::freeze.md), y, a continuación, devuelve un puntero al principio de la secuencia controlada.|  
  
## Requisitos  
 **Encabezado:** \<strstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [iostream](../Topic/iostream.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)