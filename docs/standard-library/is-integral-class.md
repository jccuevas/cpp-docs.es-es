---
title: "is_integral (Clase) | Microsoft Docs"
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
  - "std::tr1::is_integral"
  - "std.tr1.is_integral"
  - "is_integral"
  - "std.is_integral"
  - "std::is_integral"
  - "type_traits/std::is_integral"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_integral (clase) [TR1]"
  - "is_integral"
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_integral (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es entero.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_integral;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es uno de los tipos enteros o un formulario `cv-qualified` de uno de ellos; en caso contrario, es false.  
  
 Un tipo entero es uno de `bool`, `char`, `unsigned char`, `signed char`, `wchar_t`, `short`, `unsigned short`, `int`, `unsigned int`, `long` y `unsigned long`.  Además, con los compiladores que los proporcionan, un tipo entero puede ser uno de `long long`, `unsigned long long`, `__int64` y `unsigned __int64`.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_integral.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_integral<trivial> == " << std::boolalpha   
        << std::is_integral<trivial>::value << std::endl;   
    std::cout << "is_integral<int> == " << std::boolalpha   
        << std::is_integral<int>::value << std::endl;   
    std::cout << "is_integral<float> == " << std::boolalpha   
        << std::is_integral<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_integral\<trivial\> \=\= false**  
**is\_integral\<int\> \=\= true**  
**is\_integral\<float\> \=\= false**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_enum \(Clase\)](../standard-library/is-enum-class.md)   
 [is\_floating\_point \(Clase\)](../standard-library/is-floating-point-class.md)