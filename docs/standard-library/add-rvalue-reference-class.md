---
title: "add_rvalue_reference (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "type_traits/std::add_rvalue_reference"
  - "std::add_rvalue_reference"
  - "add_rvalue_reference"
  - "std.add_rvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_rvalue_reference (clase)"
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# add_rvalue_reference (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo de referencia rvalue del parámetro de plantilla, si es un tipo de objeto o función. De lo contrario, debido a la semántica de contracción de referencias, el tipo es el mismo que el parámetro de plantilla.  
  
## Sintaxis  
  
```cpp  
template<class T>  
    struct add_rvalue_reference;  
  
template<class T>  
    using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;  
```  
  
#### Parámetros  
 T  
 Tipo que se va a modificar.  
  
## Comentarios  
 La `add_rvalue_reference` clase tiene un miembro denominado `type`, que es un alias para el tipo de una referencia rvalue para el parámetro de plantilla `T`. La semántica de contracción de referencia implica que, para los tipos no sean de objeto y una función no `T`, `T&&` es un `T`. Por ejemplo, cuando `T` es un tipo de referencia de valor l,  `add_rvalue_reference<T>::type` es el tipo de referencia de valor l, no una referencia rvalue.  
  
 Para mayor comodidad, \< type\_traits \> define una plantilla de aplicación auxiliar, `add_rvalue_reference_t`, ese alias el `type` miembro de `add_rvalue_reference`.  
  
## Ejemplo  
 Este ejemplo de código usa static\_assert para mostrar cómo se crean los tipos de referencia rvalue mediante `add_rvalue_reference` y `add_rvalue_reference_t`, y cómo el resultado de `add_rvalue_reference` en una referencia a un valor no es una referencia rvalue tipo, pero se contrae en el tipo de referencia de valor l.  
  
```cpp  
// ex_add_rvalue_reference.cpp  
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp  
#include <type_traits>   
#include <iostream>   
#include <string>  
  
using namespace std;  
int main()  
{  
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,   
        "Expected add_rvalue_reference_t<string> to be string&&");  
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,   
        "Expected add_rvalue_reference_t<string*> to be string*&&");  
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,   
        "Expected add_rvalue_reference_t<string&> to be string&");  
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,   
        "Expected add_rvalue_reference_t<string&&> to be string&&");  
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;  
    return 0;  
}  
  
/*Output:  
All static_assert tests of add_rvalue_reference passed.  
*/  
```  
  
## Requisitos  
 Encabezado: \<type\_traits\> Espacio de nombres: std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Clase add\_lvalue\_reference](../standard-library/add-lvalue-reference-class.md)   
 [is\_rvalue\_reference \(Clase\)](../standard-library/is-rvalue-reference-class.md)