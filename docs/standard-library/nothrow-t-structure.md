---
title: "nothrow_t (Estructura) | Microsoft Docs"
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
  - "nothrow_t"
  - "std.nothrow_t"
  - "std::nothrow_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nothrow_t (clase)"
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# nothrow_t (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct se utiliza como un parámetro de función el operador new para indicar que la función debe devolver un puntero NULL para notificar un error de asignación, en lugar de una excepción.  
  
## Sintaxis  
  
```  
struct std::nothrow_t {};  
```  
  
## Comentarios  
 Struct ayuda al compilador que seleccione la versión correcta del constructor.  [nothrow](../Topic/nothrow%20\(%3Cnew%3E\).md) es un sinónimo de los objetos de `std::nothrow_t`escrito.  
  
## Ejemplo  
 Vea [operador nuevo](../Topic/operator%20new%20\(%3Cnew%3E\).md) y [operador new &#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) para obtener ejemplos de cómo `std::nothrow_t` se utiliza como parámetro de la función.  
  
## Requisitos  
 **Header:** \<nuevo\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)