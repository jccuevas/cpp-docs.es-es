---
title: "is_unsigned (Clase) | Microsoft Docs"
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
  - "std::tr1::is_unsigned"
  - "is_unsigned"
  - "std.tr1.is_unsigned"
  - "std.is_unsigned"
  - "std::is_unsigned"
  - "type_traits/std::is_unsigned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_unsigned (clase) [TR1]"
  - "is_unsigned"
ms.assetid: ba5bec3d-796b-4e54-8595-a3941ec6a8dc
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_unsigned (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un entero sin signo.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_unsigned;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es un tipo entero sin signo o un tipo entero sin signo `cv-qualified`; en caso contrario, contiene false.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_unsigned.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_unsigned<trivial> == " << std::boolalpha   
        << std::is_unsigned<trivial>::value << std::endl;   
    std::cout << "is_unsigned<int> == " << std::boolalpha   
        << std::is_unsigned<int>::value << std::endl;   
    std::cout << "is_unsigned<unsigned int> == " << std::boolalpha   
        << std::is_unsigned<unsigned int>::value << std::endl;   
    std::cout << "is_unsigned<float> == " << std::boolalpha   
        << std::is_unsigned<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_unsigned\<trivial\> \=\= false**  
**is\_unsigned\<int\> \=\= false**  
**is\_unsigned\<unsigned int\> \=\= true**  
**is\_unsigned\<float\> \=\= false**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_signed \(Clase\)](../standard-library/is-signed-class.md)