---
title: "strstreambuf (Clase) | Microsoft Docs"
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
  - "std.strstreambuf"
  - "strstreambuf"
  - "std::strstreambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstreambuf (clase)"
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
caps.latest.revision: 25
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strstreambuf (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un búfer de secuencia que controla la transmisión de elementos hacia y desde una secuencia de elementos almacenados en un objeto de matriz `char`.  
  
## Sintaxis  
  
```  
  
class strstreambuf : public streambuf  
  
```  
  
## Comentarios  
 En función de cómo se haya construido el objeto, se puede asignar, extender y liberar según sea necesario para dar cabida a los cambios en la secuencia.  
  
 Un objeto de clase `strstreambuf` almacena varios bits de información de modo como su modo `strstreambuf`. Estos bits indican si la secuencia controlada:  
  
-   Se ha asignado y debe liberarse finalmente.  
  
-   Es modificable.  
  
-   Es extensible mediante la reasignación de almacenamiento.  
  
-   Se ha quedado inmovilizada y, por tanto, se debe movilizar antes de que se destruya el objeto o liberar \(en el caso de estar asignado\) por parte de un organismo que no sea el objeto.  
  
 Una secuencia controlada inmovilizada no se puede modificar ni extender, independientemente del estado de estos bits de modo independiente.  
  
 El objeto también almacena punteros a dos funciones que controlan la asignación `strstreambuf`. Si se trata de punteros nulos, el objeto diseña su propio método para asignar y liberar el almacenamiento de la secuencia controlada.  
  
> [!NOTE]
>  Esta clase está en desuso. Considere el uso de [stringbuf](../Topic/stringbuf.md) o [wstringbuf](../Topic/wstringbuf.md) en su lugar.  
  
### Constructores  
  
|||  
|-|-|  
|[strstreambuf](../Topic/strstreambuf::strstreambuf.md)|Construye un objeto de tipo `strstreambuf`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[freeze](../Topic/strstreambuf::freeze.md)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|  
|[desbordamiento](../Topic/strstreambuf::overflow.md)|Función virtual protegida a la que se puede llamar cuando se inserta un carácter nuevo en un búfer lleno.|  
|[pbackfail](../Topic/strstreambuf::pbackfail.md)|Función miembro virtual protegida que intenta recolocar un elemento en el flujo de entrada y, después, convertirlo en el elemento actual \(al que apunta el puntero siguiente\).|  
|[pcount](../Topic/strstreambuf::pcount.md)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|  
|[seekoff](../Topic/strstreambuf::seekoff.md)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|  
|[seekpos](../Topic/strstreambuf::seekpos.md)|Función miembro virtual protegida que trata de modificar las posiciones actuales de las secuencias controladas.|  
|[str](../Topic/strstreambuf::str.md)|Llama a [freeze](../Topic/strstreambuf::freeze.md), y, a continuación, devuelve un puntero al principio de la secuencia controlada.|  
|[underflow](../Topic/strstreambuf::underflow.md)|Función virtual protegida que extrae el elemento actual del flujo de entrada.|  
  
## Requisitos  
 **Encabezado:** \<strstream\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [streambuf](../Topic/streambuf.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)