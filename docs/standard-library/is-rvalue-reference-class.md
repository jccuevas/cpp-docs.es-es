---
title: "is_rvalue_reference (Clase) | Microsoft Docs"
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
  - "std.tr1.is_rvalue_reference"
  - "is_rvalue_reference"
  - "std::tr1::is_rvalue_reference"
  - "std.is_rvalue_reference"
  - "std::is_rvalue_reference"
  - "type_traits/std::is_rvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_rvalue_reference (clase) [TR1]"
  - "is_rvalue_reference"
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_rvalue_reference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es una referencia a un valor R.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_rvalue_reference;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia de este predicado de tipo contiene true si el tipo `Ty` es una referencia a un [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Lvalues y rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)