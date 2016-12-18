---
title: "is_trivially_copy_assignable | Microsoft Docs"
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
  - "is_trivially_copy_assignable"
  - "std.is_trivially_copy_assignable"
  - "std::is_trivially_copy_assignable"
  - "type_traits/std::is_trivially_copy_assignable"
dev_langs: 
  - "C++"
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 12
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_copy_assignable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un operador de asignación de copia trivial.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_trivially_copy_constructible;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de copias trivial; en caso contrario, contiene false.  
  
 Un constructor de asignación para una clase `Ty` es trivial si:  
  
 se proporciona de forma implícita  
  
 la clase `Ty` no tiene ninguna función virtual  
  
 la clase `Ty` no tiene ninguna base virtual  
  
 las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación triviales  
  
 las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)