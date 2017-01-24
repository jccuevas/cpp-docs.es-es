---
title: "is_reference (Clase) | Microsoft Docs"
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
  - "std.tr1.is_reference"
  - "std::tr1::is_reference"
  - "is_reference"
  - "std.is_reference"
  - "std::is_reference"
  - "type_traits/std::is_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_reference (clase) [TR1]"
  - "is_reference"
ms.assetid: 3d9e631f-3092-430c-843e-e914ab58c257
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_reference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es una referencia.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_reference;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una referencia a un objeto o una función; de lo contrario, contiene false.  
  
## Ejemplo  
  
```  
// std__type_traits__is_reference.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_reference<trivial> == " << std::boolalpha   
        << std::is_reference<trivial>::value << std::endl;   
    std::cout << "is_reference<trivial&> == " << std::boolalpha   
        << std::is_reference<trivial&>::value << std::endl;   
    std::cout << "is_reference<int()> == " << std::boolalpha   
        << std::is_reference<int()>::value << std::endl;   
    std::cout << "is_reference<int(&)()> == " << std::boolalpha   
        << std::is_reference<int(&)()>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_reference\<trivial\> \=\= false**  
**is\_reference\<trivial&\> \=\= true**  
**is\_reference\<int\(\)\> \=\= false**  
**is\_reference\<int\(&\)\(\)\> \=\= true**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_pointer \(Clase\)](../standard-library/is-pointer-class.md)