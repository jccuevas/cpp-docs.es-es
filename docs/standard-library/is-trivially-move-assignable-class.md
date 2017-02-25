---
title: "is_trivially_move_assignable (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_move_assignable"
  - "std.is_trivially_move_assignable"
  - "std::is_trivially_move_assignable"
  - "type_traits/std::is_trivially_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_move_assignable"
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# is_trivially_move_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_trivially_move_assignable;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.  
  
 Un operador de asignación de movimiento para una clase `Ty` es trivial si:  
  
 se proporciona de forma implícita  
  
 la clase `Ty` no tiene ninguna función virtual  
  
 la clase `Ty` no tiene ninguna base virtual  
  
 las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales  
  
 las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)