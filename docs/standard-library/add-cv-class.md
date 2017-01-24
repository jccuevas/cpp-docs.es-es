---
title: "add_cv (Clase) | Microsoft Docs"
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
  - "std.tr1.add_cv"
  - "add_cv"
  - "std::tr1::add_cv"
  - "std.add_cv"
  - "std::add_cv"
  - "type_traits/std::add_cv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_cv (clase) [TR1]"
  - "add_cv"
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_cv (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte un tipo en tipo const\/volatile.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct add_cv;  
  
template<class T>  
using add_cv_t = typename add_cv<T>::type;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia del modificador de tipo contiene el tipo modificado [add\_volatile \(Clase\)](../standard-library/add-volatile-class.md)`<` [add\_const \(Clase\)](../standard-library/add-const-class.md)`<Ty> >`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_cv_t<int> *p = (const volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_cv<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_cv\_t\<int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_const \(Clase\)](../standard-library/remove-const-class.md)   
 [remove\_volatile \(Clase\)](../standard-library/remove-volatile-class.md)