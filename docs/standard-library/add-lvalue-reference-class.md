---
title: "Clase add_lvalue_reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::add_lvalue_reference"
  - "add_lvalue_reference"
  - "type_traits/std::add_lvalue_reference"
  - "std.add_lvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_lvalue_reference"
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Clase add_lvalue_reference
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte una referencia en un tipo a partir de un tipo.  
  
## Sintaxis  
  
```  
template<class T>  
    struct add_lvalue_reference;  
  
template<class T>  
    using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `T` si `T` es una referencia lvalue. En caso contrario, es `T&`.  
  
## Ejemplo  
  
```  
#include <type_traits>   
#include <iostream>   
  
using namespace std;  
int main()  
{  
    int val = 0;  
    add_lvalue_reference_t<int> p = (int&)val;  
    p = p;  // to quiet "unused" warning   
    cout << "add_lvalue_reference_t<int> == "  
        << typeid(p).name() << endl;  
  
    return (0);  
}  
```  
  
  **add\_lvalue\_reference\_t\<int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_reference \(Clase\)](../standard-library/remove-reference-class.md)