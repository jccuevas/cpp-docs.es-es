---
title: "is_placeholder (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_placeholder"
  - "std.tr1.is_placeholder"
  - "functional/std::tr1::is_placeholder"
  - "std::tr1::is_placeholder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_placeholder (clase) [TR1]"
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# is_placeholder (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un marcador.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_placeholder {  
    static const int value;  
    };  
```  
  
## Comentarios  
 El valor constante `value` es 0 si el tipo `Ty` no es marcador; de lo contrario, su valor es la posición del argumento de la llamada de función a que enlaza.  Se utiliza para determinar el valor `N` para el marcador `_N`de Enésimo.  
  
## Ejemplo  
  
```  
// std_tr1__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>   
    void test_for_placeholder(const Expr&)   
    {   
    std::cout << std::is_placeholder<Expr>::value << std::endl;   
    }   
  
int main()   
    {   
    test_for_placeholder(3.0);   
    test_for_placeholder(_3);   
  
    return (0);   
    }  
  
```  
  
  **0**  
**3**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\_1 \(Objeto\)](../standard-library/1-object.md)