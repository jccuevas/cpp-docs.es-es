---
title: "remove_const (Clase) | Microsoft Docs"
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
  - "std.tr1.remove_const"
  - "std::tr1::remove_const"
  - "remove_const"
  - "std.remove_const"
  - "std::remove_const"
  - "type_traits/std::remove_const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_const (clase) [TR1]"
  - "remove_const"
ms.assetid: feb76fb3-9228-41d6-80f6-2fbb04daec43
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove_const (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo no const a partir de un tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct remove_const;  
```  
  
```  
template<class T>  
  using remove_const_t = typename remove_const<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia de `remove_const<T>` contiene un tipo modificado que es `T1` cuando `T` tiene la forma `const T1`; si no es `T`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_const_t<const int>*)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_const_t<const int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_const\_t\<const int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_const \(Clase\)](../standard-library/add-const-class.md)   
 [remove\_cv \(Clase\)](../standard-library/remove-cv-class.md)