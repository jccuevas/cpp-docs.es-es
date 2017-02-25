---
title: "remove_volatile (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::remove_volatile"
  - "std.tr1.remove_volatile"
  - "remove_volatile"
  - "std.remove_volatile"
  - "std::remove_volatile"
  - "type_traits/std::remove_volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_volatile (clase) [TR1]"
  - "remove_volatile"
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_volatile (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo no volátil a partir de un tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct remove_volatile;  
  
template<class T>  
  using remove_volatile_t = typename remove_volatile<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia de `remove_volatile<T>` contiene un tipo modificado que es `T1` cuando `T` tiene la forma `volatile T1`; si no es `T`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_volatile_t<volatile int> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << " remove_volatile_t<volatile int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_volatile\_t\<volatile int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_volatile \(Clase\)](../standard-library/add-volatile-class.md)