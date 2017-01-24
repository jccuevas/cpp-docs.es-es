---
title: "Clase is_nothrow_move_constructible | Microsoft Docs"
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
  - "is_nothrow_move_constructible"
  - "std.is_nothrow_move_constructible"
  - "std::is_nothrow_move_constructible"
  - "type_traits/std::is_nothrow_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_move_constructible"
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase is_nothrow_move_constructible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor de movimiento [nothrow](../cpp/nothrow-cpp.md).  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_nothrow_move_constructible;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un constructor de movimiento nothrow; en caso contrario, contiene false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)