---
title: "is_move_constructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_move_constructible"
  - "std.is_move_constructible"
  - "std::is_move_constructible"
  - "type_traits/std::is_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_move_constructible"
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_move_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor de movimiento.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_move_constructible;  
```  
  
#### Parámetros  
 T  
 El tipo que se debe evaluar  
  
## Comentarios  
 Un predicado de tipo que se evalúa como true si el tipo `T` puede crearse mediante el uso de una operación de movimiento. Este predicado equivale a `is_constructible<T, T&&>`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)