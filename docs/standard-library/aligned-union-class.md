---
title: "Clase aligned_union | Microsoft Docs"
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
  - "aligned_union"
  - "std.aligned_union"
  - "std::aligned_union"
  - "type_traits/std::aligned_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aligned_union"
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
caps.latest.revision: 10
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Clase aligned_union
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona un tipo POD convenientemente alineado y lo suficientemente grande como para almacenar un tipo de unión y el tamaño necesario.  
  
## Sintaxis  
  
```  
template <std::size_t Len, class... Types>  
    struct aligned_union;  
  
template <std::size_t Len, class... Types>  
    using aligned_union_t = typename aligned_union<Len, Types...>::type;  
```  
  
#### Parámetros  
 `Len`  
 El valor de alineación para el tipo más grande de la unión.  
  
 `Types`  
 Los distintos tipos de la unión subyacente.  
  
## Comentarios  
 Utilice la clase de plantilla para obtener la alineación y el tamaño necesario para almacenar una unión en el almacenamiento sin inicializar. La definición de tipo de miembro `type` Escriba adecuados para el almacenamiento de cualquier tipo que aparece en una SUCESIÓN de nombres `Types`; el tamaño mínimo es `Len`. El miembro estático `alignment_value` de tipo `std::size_t` contiene la alineación más estricta necesaria de todos los tipos enumerados en `Types`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar `aligned_union` para asignar un búfer de pila alineada para colocar una unión.  
  
```  
// std__type_traits__aligned_union.cpp  
#include <iostream>  
#include <type_traits>  
  
union U_type  
{  
    int i;  
    float f;  
    double d;  
    U_type(float e) : f(e) {}  
};  
  
typedef std::aligned_union<16, int, float, double>::type aligned_U_type;  
  
int main()  
{  
    // allocate memory for a U_type aligned on a 16-byte boundary  
    aligned_U_type au;  
    // do placement new in the aligned memory on the stack  
    U_type* u = new (&au) U_type(1.0f);  
    if (nullptr != u)  
    {  
        std::cout << "value of u->i is " << u->i << std::endl;  
        // must clean up placement objects manually!  
        u->~U_type();  
    }  
}  
```  
  
```Output  
valor de se -> i es 1065353216  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [alignment\_of \(Clase\)](../standard-library/alignment-of-class.md)