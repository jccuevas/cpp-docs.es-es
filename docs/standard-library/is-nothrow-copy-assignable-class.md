---
title: "Clase is_nothrow_copy_assignable | Microsoft Docs"
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
  - "is_nothrow_copy_assignable"
  - "std.is_nothrow_copy_assignable"
  - "std::is_nothrow_copy_assignable"
  - "type_traits/std::is_nothrow_copy_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_copy_assignable"
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase is_nothrow_copy_assignable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un operador de asignación de copia que se sabe que el compilador no se iniciará.  
  
## Sintaxis  
  
```  
template<class T>  
    struct is_nothrow_copy_assignable;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true para un tipo referenciable `T` donde `is_nothrow_assignable<T&, const T&>` contiene true; en caso contrario, contiene false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_nothrow\_assignable \(clase\)](../standard-library/is-nothrow-assignable-class.md)   
 [nothrow](../cpp/nothrow-cpp.md)