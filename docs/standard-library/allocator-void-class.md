---
title: "allocator&lt;void&gt; (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator<void>"
  - "std::allocator<void>"
  - "std.allocator<void>"
  - "allocator<void>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator<void> (clase)"
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# allocator&lt;void&gt; (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una especialización de asignador de la clase de plantilla para escribir `void`, definir tipos que tienen sentido en este contexto.  
  
## Sintaxis  
  
```  
template<>  
   class allocator<void> {  
   typedef void *pointer;  
   typedef const void *const_pointer;  
   typedef void value_type;  
   template<class Other>  
      struct rebind;  
   allocator( );  
   allocator(  
      const allocator<void>&  
   );  
   template<class Other>  
      allocator(  
         const allocator<Other>&  
      );  
   template<class Other>  
      allocator<void>& operator=(  
         const allocator<Other>&  
      );  
   };  
```  
  
## Comentarios  
 La clase explícitamente especializa la clase de plantilla [allocator](../standard-library/allocator-class.md) para tipo *vacío.* Los constructores y operador de asignación se comportan igual que para la clase de plantilla, pero define sólo los tipos siguientes:  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md).  
  
-   [puntero](../Topic/allocator::pointer.md).  
  
-   [value\_type](../Topic/allocator::value_type.md).  
  
-   [reencuaderne](../Topic/allocator::rebind.md), una clase de plantilla anidados.  
  
## Requisitos  
 Memoria\<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)