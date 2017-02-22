---
title: "is_standard_layout (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_standard_layout"
  - "std::tr1::is_standard_layout"
  - "is_standard_layout"
  - "std.is_standard_layout"
  - "std::is_standard_layout"
  - "type_traits/std::is_standard_layout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_standard_layout (clase) [TR1]"
  - "is_standard_layout"
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# is_standard_layout (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un diseño estándar.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_standard_layout;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Ty`|El tipo que se va a consultar.|  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es una clase que tiene un diseño estándar de objetos miembro en memoria; en caso contrario, es false.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)