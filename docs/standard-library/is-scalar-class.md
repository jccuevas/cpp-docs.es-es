---
title: "is_scalar (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_scalar"
  - "std::tr1::is_scalar"
  - "is_scalar"
  - "std.is_scalar"
  - "std::is_scalar"
  - "type_traits/std::is_scalar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_scalar (clase) [TR1]"
  - "is_scalar"
ms.assetid: a0cdfc9a-f27e-4808-890f-6ed7942db60c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_scalar (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es escalar.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_scalar;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia de tipo predicado contiene true si el tipo `Ty` es un entero, un punto flotante, una enumeración, un puntero o un puntero a miembro, o bien un formulario `cv-qualified` de uno de ellos; en caso contrario, contiene false.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_scalar.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_scalar<trivial> == " << std::boolalpha   
        << std::is_scalar<trivial>::value << std::endl;   
    std::cout << "is_scalar<trivial *> == " << std::boolalpha   
        << std::is_scalar<trivial *>::value << std::endl;   
    std::cout << "is_scalar<int> == " << std::boolalpha   
        << std::is_scalar<int>::value << std::endl;   
    std::cout << "is_scalar<float> == " << std::boolalpha   
        << std::is_scalar<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_scalar\<trivial\> \=\= false**  
**is\_scalar\<trivial \*\> \=\= true**  
**is\_scalar\<int\> \=\= true**  
**is\_scalar\<float\> \=\= true**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_compound \(Clase\)](../standard-library/is-compound-class.md)