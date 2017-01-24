---
title: "is_move_assignable (clase) | Microsoft Docs"
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
  - "is_move_assignable"
  - "std.is_move_assignable"
  - "std::is_move_assignable"
  - "type_traits/std::is_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_move_assignable"
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_move_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo se puede mover asignado.  
  
## Sintaxis  
  
```  
template<class T>  
    struct is_move_assignable;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Un tipo es asignable de movimiento si una referencia a valor r al tipo se puede asignar a una referencia al tipo. El predicado de tipo es equivalente a `is_assignable<T&, T&&>`. Mover tipos asignables incluyen los tipos escalares referenciable y operadores de asignación de movimiento de tipos de clase que tengan generada por el compilador o definidos por el usuario.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)