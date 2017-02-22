---
title: "is_trivially_destructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_trivially_destructible"
  - "std.is_trivially_destructible"
  - "std::is_trivially_destructible"
  - "type_traits/std::is_trivially_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_destructible"
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_trivially_destructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es muy puedan destruir.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_trivially_destructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es un tipo que se puedan destruir y el compilador conoce el destructor utilizar ninguna operación no trivial. De lo contrario, contiene false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)