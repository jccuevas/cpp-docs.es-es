---
title: "is_lvalue_reference (Clase) | Microsoft Docs"
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
  - "std.tr1.is_lvalue_reference"
  - "std::tr1::is_lvalue_reference"
  - "is_lvalue_reference"
  - "std.is_lvalue_reference"
  - "std::is_lvalue_reference"
  - "type_traits/std::is_lvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_lvalue_reference (clase) [TR1]"
  - "is_lvalue_reference"
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_lvalue_reference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es una referencia a un valor L.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_lvalue_reference;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia de este predicado de tipo contiene true si el tipo `Ty` es una referencia a un objeto o una función; de lo contrario, contiene false.  Tenga en cuenta que es posible que `Ty` no sea una referencia a un valor R.  Para más información sobre los valores R, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Lvalues y rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)