---
title: "istrstream (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istrstream"
  - "std::istrstream"
  - "std.istrstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istrstream (clase)"
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# istrstream (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## Sintaxis  
  
```  
  
class istrstream : public istream  
  
```  
  
## Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso. Considere el uso de [istringstream](../Topic/istringstream.md) o [wistringstream](../Topic/wistringstream.md) en su lugar.  
  
### Constructores  
  
|||  
|-|-|  
|[istrstream](../Topic/istrstream::istrstream.md)|Construye un objeto de tipo `istrstream`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](../Topic/istrstream::rdbuf.md)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](../Topic/istrstream::str.md)|Llama a [freeze](../Topic/strstreambuf::freeze.md), y, a continuación, devuelve un puntero al principio de la secuencia controlada.|  
  
## Requisitos  
 **Encabezado:** \<strstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [istream](../Topic/istream.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)