---
title: "Clase is_trivial | Microsoft Docs"
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
  - "is_trivial"
  - "std.is_trivial"
  - "std::is_trivial"
  - "type_traits/std::is_trivial"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivial"
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase is_trivial
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un tipo trivial.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_trivial;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` es un tipo trivial; en caso contrario, es false. Los tipos triviales son tipos escalares, tipos de clase que se pueden copiar de forma trivial, matrices de estos tipos y versiones de tipo cv\-qualified \(const, volatile, const volatile\) de estos tipos.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)