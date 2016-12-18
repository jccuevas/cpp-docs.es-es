---
title: "is_trivially_copyable (clase) | Microsoft Docs"
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
  - "is_trivially_copyable"
  - "std.is_trivially_copyable"
  - "std::is_trivially_copyable"
  - "type_traits/std::is_trivially_copyable"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_copyable"
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_copyable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un tipo de copiar de forma trivial.  
  
## Sintaxis  
  
```  
template<class T>  
    struct is_trivially_copyable;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es copiar de forma trivial tipo, en caso contrario, contiene false. Copiar de forma trivial tipos no tienen operaciones de copia no trivial, las operaciones de desplazamiento ni destructores. Por lo general, una operación de copia se considera trivial si se puede implementar como una copia bit a bit. Tipos integrados y matrices de tipos de copiar de forma trivial son copiar de forma trivial.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)