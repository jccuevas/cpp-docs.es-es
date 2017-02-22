---
title: "aligned_storage (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "aligned_storage"
  - "std::tr1::aligned_storage"
  - "std.tr1.aligned_storage"
  - "std.aligned_storage"
  - "std::aligned_storage"
  - "type_traits/std::aligned_storage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_storage (clase) [TR1]"
  - "aligned_storage"
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# aligned_storage (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo alineado como corresponda.  
  
## Sintaxis  
  
```  
template<std::size_t Len, std::size_t Align>  
    struct aligned_storage;  
  
template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>  
    using aligned_storage_t = typename aligned_storage<Len, Align>::type;  
```  
  
#### Parámetros  
 `Len`  
 Tamaño del objeto.  
  
 `Align`  
 Alineación del objeto.  
  
## Comentarios  
 La definición de tipo de plantilla miembro `type` es un sinónimo de un tipo POD con alineación `Align` y tamaño `Len`.`Align` debe ser igual a `alignment_of<T>::value` algún tipo `T`, o la alineación predeterminada.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
typedef std::aligned_storage<sizeof (int),   
    std::alignment_of<double>::value>::type New_type;   
int main()   
    {   
    std::cout << "alignment_of<int> == "   
        << std::alignment_of<int>::value << std::endl;   
    std::cout << "aligned to double == "   
        << std::alignment_of<New_type>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
alignment_of < int > == 4 alineado a double == 8  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [alignment\_of \(Clase\)](../standard-library/alignment-of-class.md)