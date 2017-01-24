---
title: "is_nothrow_destructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_destructible"
  - "std.is_nothrow_destructible"
  - "std::is_nothrow_destructible"
  - "type_traits/std::is_nothrow_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_destructible"
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_destructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es puedan destruir y el compilador conoce el destructor no se iniciará.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_nothrow_destructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es un tipo que se puedan destruir y el compilador conoce el destructor no se iniciará. De lo contrario, contiene false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)