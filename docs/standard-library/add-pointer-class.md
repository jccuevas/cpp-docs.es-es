---
title: "add_pointer (Clase) | Microsoft Docs"
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
  - "std::tr1::add_pointer"
  - "std.tr1.add_pointer"
  - "add_pointer"
  - "std.add_pointer"
  - "std::add_pointer"
  - "type_traits/std::add_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_pointer (clase) [TR1]"
  - "add_pointer"
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_pointer (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un puntero\-a\-tipo a partir de un tipo especificado.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct add_pointer;  
  
template<class T>  
using add_pointer_t = typename add_pointer<T>::type;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a modificar.  
  
## Comentarios  
 El tipo miembro typedef denomina el mismo tipo como `remove_reference<T>::type*`.  
  
 Como no es válido crear punteros a partir de referencias, `add_pointer` quita la referencia, si existe, del tipo especificado antes de crear un puntero\-a\-tipo.  Por consiguiente, se puede usar un tipo con `add_pointer` sin que preocupe el hecho de si el tipo es una referencia.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra que `add_pointer` de un tipo es igual que un puntero a ese tipo.  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_pointer_t<int> *p = (int **)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_pointer_t<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_pointer\_t\<int\> \=\= int \***   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_pointer \(Clase\)](../standard-library/remove-pointer-class.md)