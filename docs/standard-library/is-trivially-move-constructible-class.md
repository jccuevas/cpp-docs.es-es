---
title: "is_trivially_move_constructible (clase) | Microsoft Docs"
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
  - "is_trivially_move_constructible"
  - "std.is_trivially_move_constructible"
  - "std::is_trivially_move_constructible"
  - "type_traits/std::is_trivially_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_move_constructible"
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_move_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor de movimiento trivial.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_trivially_move_constructible;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un constructor de movimiento trivial; en caso contrario, contiene false.  
  
 Un constructor de movimiento para una clase `Ty` es trivial si:  
  
 se declara de forma implícita  
  
 sus tipos de parámetro son equivalentes a los de una declaración implícita  
  
 la clase `Ty` no tiene ninguna función virtual  
  
 la clase `Ty` no tiene ninguna base virtual  
  
 la clase no tiene ningún miembro de datos no estáticos volátil  
  
 todas las bases directas de la clase `Ty` tienen constructores de movimiento trivial  
  
 las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales  
  
 las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)