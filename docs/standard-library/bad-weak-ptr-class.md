---
title: "bad_weak_ptr (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::tr1::bad_weak_ptr"
  - "std::tr1::bad_weak_ptr"
  - "bad_weak_ptr"
  - "tr1::bad_weak_ptr"
  - "tr1.bad_weak_ptr"
  - "std.tr1.bad_weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_weak_ptr (clase)"
  - "bad_weak_ptr (clase) [TR1]"
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# bad_weak_ptr (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Informa de una excepción weak\_ptr errónea.  
  
## Sintaxis  
  
```  
class bad_weak_ptr  
    : public std::exception {  
public:  
    bad_weak_ptr();  
    const char *what() throw();  
    };  
```  
  
## Comentarios  
 La clase describe una excepción que se puede iniciar desde el constructor [shared\_ptr \(Clase\)](../standard-library/shared-ptr-class.md) que toma un argumento de tipo [weak\_ptr \(Clase\)](../standard-library/weak-ptr-class.md).  La función miembro `what` devuelve `"bad_weak_ptr"`.  
  
## Ejemplo  
  
```  
// std_tr1__memory__bad_weak_ptr.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::weak_ptr<int> wp;   
  
     {   
    std::shared_ptr<int> sp(new int);   
    wp = sp;   
     }   
  
    try   
        {   
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired   
        }   
    catch (const std::bad_weak_ptr&)   
        {   
        std::cout << "bad weak pointer" << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
  **puntero débil erróneo**   
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [weak\_ptr \(Clase\)](../standard-library/weak-ptr-class.md)