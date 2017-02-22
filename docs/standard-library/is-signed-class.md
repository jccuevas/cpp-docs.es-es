---
title: "is_signed (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_signed"
  - "std.tr1.is_signed"
  - "std::tr1::is_signed"
  - "std.is_signed"
  - "std::is_signed"
  - "type_traits/std::is_signed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_signed (clase) [TR1]"
  - "is_signed"
ms.assetid: 20ae44d9-22ad-4fbd-b26a-f18c62689451
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_signed (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compruebe si el tipo es un entero con signo.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_signed;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es un tipo entero con signo o un tipo entero con signo `cv-qualified`; en caso contrario, contiene false.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_signed.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_signed<trivial> == " << std::boolalpha   
        << std::is_signed<trivial>::value << std::endl;   
    std::cout << "is_signed<int> == " << std::boolalpha   
        << std::is_signed<int>::value << std::endl;   
    std::cout << "is_signed<unsigned int> == " << std::boolalpha   
        << std::is_signed<unsigned int>::value << std::endl;   
    std::cout << "is_signed<float> == " << std::boolalpha   
        << std::is_signed<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_signed\<trivial\> \=\= false**  
**is\_signed\<int\> \=\= true**  
**is\_signed\<unsigned int\> \=\= false**  
**is\_signed\<float\> \=\= false**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_unsigned \(Clase\)](../standard-library/is-unsigned-class.md)