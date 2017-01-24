---
title: "extent (Clase) | Microsoft Docs"
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
  - "std.tr1.extent"
  - "extent"
  - "std::tr1::extent"
  - "std.extent"
  - "std::extent"
  - "type_traits/std::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent (clase) [TR1]"
  - "extent"
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# extent (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene una dimensión de matriz.  
  
## Sintaxis  
  
```  
template<class Ty, unsigned I = 0>  
    struct extent;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
 `I`  
 La matriz que se enlaza a la consulta.  
  
## Comentarios  
 Si `Ty` es un tipo de matriz con `I` dimensiones como mínimo, la consulta de tipo contiene el número de elementos de la dimensión que especifica `I`.  Si `Ty` no es un tipo de matriz o el rango es menor que `I`, o si `I` es cero y `Ty` es de tipo "matriz de límite desconocido de `U`", la consulta de tipo contiene el valor 0.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **extent 0 \=\= 5**  
**extent 1 \=\= 10**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_all\_extents \(Clase\)](../standard-library/remove-all-extents-class.md)   
 [remove\_extent \(Clase\)](../standard-library/remove-extent-class.md)