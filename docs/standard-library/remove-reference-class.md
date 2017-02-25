---
title: "remove_reference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.remove_reference"
  - "std::tr1::remove_reference"
  - "remove_reference"
  - "std.remove_reference"
  - "std::remove_reference"
  - "type_traits/std::remove_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_reference (clase) [TR1]"
  - "remove_reference"
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# remove_reference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo que no es de referencia a partir de un tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct remove_reference;  
  
template<class T>  using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia de `remove_reference<T>` contiene un tipo modificado que es `T1` cuando `T` tiene la forma `T1&`; si no es `T`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Clase add\_lvalue\_reference](../standard-library/add-lvalue-reference-class.md)