---
title: "_1 (Objeto) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1._1"
  - "_1"
  - "std::tr1::_1"
  - "functional/std::tr1::_1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_1 (objeto) [TR1]"
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _1 (Objeto)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Marcadores de posición para argumentos reemplazables.  
  
## Sintaxis  
  
```  
namespace placeholders {  
  extern unspecified _1, _2, ... _M  
  } // namespace placeholders (within std)  
```  
  
## Comentarios  
 Los objetos `_1, _2, ... _M` son marcadores de posición que indican el primer, segundo, …, m\-ésimo argumentos, respectivamente en una llamada de función a un objeto devuelto por [bind \(Función\)](../Topic/bind%20Function.md).  Puede usar `_N` para especificar dónde debe incrustarse el enésimo argumento cuando se evalúa la expresión de enlace.  
  
 en esta implementación el valor de `M` es 20.  
  
## Ejemplo  
  
```cpp  
// std__functional_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)   
    {   
    std::cout << x << "^2 == " << x * x << std::endl;   
    }   
  
void product(double x, double y)   
    {   
    std::cout << x << "*" << y << " == " << x * y << std::endl;   
    }   
  
int main()   
    {   
    double arg[] = {1, 2, 3};   
  
    std::for_each(&arg[0], &arg[3], square);   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(square, _1));   
  
    return (0);   
    }  
  
```  
  
  **1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**  
**1\*2 \=\= 2**  
**2\*2 \=\= 4**  
**3\*2 \=\= 6**  
**1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [bind \(Función\)](../Topic/bind%20Function.md)   
 [is\_placeholder \(Clase\)](../standard-library/is-placeholder-class.md)