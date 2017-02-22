---
title: "is_nothrow_move_assignable (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_nothrow_move_assignable"
  - "std.is_nothrow_move_assignable"
  - "std::is_nothrow_move_assignable"
  - "type_traits/std::is_nothrow_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_move_assignable"
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# is_nothrow_move_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si el tipo tiene un operador de asignación de movimiento [nothrow](../cpp/nothrow-cpp.md).  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_nothrow_move_assignable;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un operador de asignación de movimiento nothrow; en caso contrario, contiene false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)