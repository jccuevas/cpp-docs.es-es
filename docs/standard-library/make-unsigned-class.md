---
title: "make_unsigned (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.make_unsigned"
  - "make_unsigned"
  - "std::tr1::make_unsigned"
  - "std.make_unsigned"
  - "std::make_unsigned"
  - "type_traits/std::make_unsigned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_unsigned (clase) [TR1]"
  - "make_unsigned"
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# make_unsigned (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hace que el tipo o el tipo sin signo más pequeño sea igual o superior en tamaño al tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct make_unsigned;  
  
template<class T>  
    using make_unsigned_t = typename make_unsigned<T>::type;  
  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`T`|Tipo que se va a modificar.|  
  
## Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `is_unsigned<T>` es true.  En caso contrario, es el tipo con signo menor `ST` para el que `sizeof (T) <= sizeof (ST)`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)