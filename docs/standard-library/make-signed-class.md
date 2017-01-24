---
title: "make_signed (Clase) | Microsoft Docs"
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
  - "std::tr1::make_signed"
  - "make_signed"
  - "std.tr1.make_signed"
  - "std.make_signed"
  - "std::make_signed"
  - "type_traits/std::make_signed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_signed (clase) [TR1]"
  - "make_signed"
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# make_signed (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hace que el tipo o el tipo con signo más pequeño sea igual o superior en tamaño al tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct make_signed;  
  
template<class T>  
    using make_signed_t = typename make_signed<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `is_signed<T>` es true. En caso contrario, es el tipo sin signo menor `UT` para el que `sizeof (T) <= sizeof (UT)`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)