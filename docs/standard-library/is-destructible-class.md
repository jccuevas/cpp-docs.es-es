---
title: "is_destructible (clase) | Microsoft Docs"
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
  - "is_destructible"
  - "std.is_destructible"
  - "std::is_destructible"
  - "type_traits/std::is_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_destructible"
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# is_destructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es puedan destruir.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_destructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es un puedan destruir tipo, en caso contrario, contiene false. Puedan destruir tipos son tipos de referencia, tipos de objetos y tipos donde para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` es correcto. Otros tipos, incluidos los tipos incompletos, `void`, y tipos de función, no se puedan destruir tipos.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)