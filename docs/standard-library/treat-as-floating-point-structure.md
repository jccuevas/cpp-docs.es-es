---
title: "treat_as_floating_point (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::treat_as_floating_point"
dev_langs: 
  - "C++"
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# treat_as_floating_point (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica si `Rep` se puede tratar como un tipo de punto flotante.  
  
## Sintaxis  
  
```  
template<class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## Comentarios  
 `Rep` se puede tratar como un tipo de punto flotante solo cuando la especialización `treat_as_floating_point<Rep>` se deriva de [true\_type](../Topic/true_type%20Typedef.md).  La clase de plantilla se puede especializar para un tipo definido por el usuario.  
  
## Requisitos  
 **Encabezado:** chrono  
  
 **Espacio de nombres:** std::chrono  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)