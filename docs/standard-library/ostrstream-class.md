---
title: "ostrstream (Clase) | Microsoft Docs"
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
  - "std.oststream"
  - "oststream"
  - "std::oststream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostrstream (clase)"
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: 20
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ostrstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## Sintaxis  
  
```  
  
class ostrstream : public ostream  
  
```  
  
## Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso.  Considere el uso de [ostringstream](../Topic/ostringstream.md) o [wostringstream](../Topic/wostringstream.md) en su lugar.  
  
### Constructores  
  
|||  
|-|-|  
|[ostrstream](../Topic/ostrstream::ostrstream.md)|Construye un objeto de tipo `ostrstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[freeze](../Topic/ostrstream::freeze.md)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|  
|[pcount](../Topic/ostrstream::pcount.md)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|  
|[rdbuf](../Topic/ostrstream::rdbuf.md)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](../Topic/ostrstream::str.md)|Llama a [freeze](../Topic/strstreambuf::freeze.md), y, a continuación, devuelve un puntero al principio de la secuencia controlada.|  
  
## Requisitos  
 **Encabezado:** \<strstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [ostream](../Topic/ostream.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)