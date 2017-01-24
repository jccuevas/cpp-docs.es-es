---
title: "add_volatile (Clase) | Microsoft Docs"
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
  - "std::tr1::add_volatile"
  - "add_volatile"
  - "std.tr1.add_volatile"
  - "std.add_volatile"
  - "std::add_volatile"
  - "type_traits/std::add_volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_volatile (clase) [TR1]"
  - "add_volatile"
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 21
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_volatile (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo volátil a partir del tipo especificado.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct add_volatile;  
  
template<class T>  
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `Ty` si `Ty` es una referencia, una función o un tipo calificado como volátil; si no, es `volatile Ty`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_volatile\<int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_volatile \(Clase\)](../standard-library/remove-volatile-class.md)