---
title: "bad_function_call (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::bad_function_call"
  - "functional/std::tr1::bad_function_call"
  - "std.tr1.bad_function_call"
  - "bad_function_call"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_function_call (clase) [TR1]"
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# bad_function_call (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Informes una llamada de función CAST.  
  
## Sintaxis  
  
```  
class bad_function_call  
    : public std::exception {  
    };  
```  
  
## Comentarios  
 La clase describe una excepción para indicar que el error de una llamada a `operator()` en un objeto de [function \(Clase\)](../standard-library/function-class.md) porque el objeto estaba vacía.  
  
## Ejemplo  
  
```  
// std_tr1__functional__bad_function_call.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
typedef double (Fd)(double);   
typedef std::function<Fd> Myfunc;   
  
double square(double x)   
    {   
    return (x * x);   
    }   
  
int main()   
    {   
    Myfunc fd0(square);   
    std::cout << "x * x == " << fd0(3) << std::endl;   
  
    try   
        {   
        Myfunc fd1;   
        std::cout << fd1(3) << std::endl;   
        }   
    catch (const std::bad_function_call&)   
        {   
        std::cout << "bad function call" << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
  **x \* x \=\= 9**  
**llamada de función CAST**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std