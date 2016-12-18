---
title: "result_of (Clase) | Microsoft Docs"
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
  - "functional/std::tr1::result_of"
  - "std::tr1::result_of"
  - "result_of"
  - "std.tr1.result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of (clase) [TR1]"
ms.assetid: 14ec0040-07f1-45a5-80b5-d0c9f9b00c8f
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un objeto accesible que contiene.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct result_of {  
    typedef T0 type;  
    };  
```  
  
#### Parámetros  
 `Ty`  
 Una descripción de una llamada de función \(vea la sección comentarios\).  
  
## Comentarios  
 La clase de plantilla define su miembro `type` como sinónimo del tipo de valor devuelto de una llamada de función descrita por el argumento `Ty`de la plantilla.  El argumento de plantilla debe tener el formato `Fty(T1, T2, ..., TN)`, donde es un tipo `Fty` accesible.  La plantilla determina el tipo de valor devuelto como el primer de las reglas siguientes que se aplica a:  
  
-   si `Fty` es un puntero a tipo de función `R(*)(U1, U2, ..., UN)` return\-type es `R`;  
  
-   si `Fty` es una referencia a la función escriba `R(&)(U1, U2, ..., UN)` que el tipo de valor devuelto es `R`;  
  
-   si `Fty` es un puntero a la función miembro escriba `R(U1::*)(U2, ..., UN)` que el tipo de valor devuelto es `R`;  
  
-   si `Fty` es un puntero al miembro de datos escriba `R U1::*` que el tipo de valor devuelto es `R`;  
  
-   si `Fty` es una clase con una definición `result_type` miembro return\-type es `Fty::result_type`;  
  
-   si `N` es 0 \(es decir, `Ty` tiene el formato `Fty()`\) que el tipo de valor devuelto es `void`;  
  
-   si `Fty` es una clase con una plantilla de miembro denominada `result` return\-type es `Fty::result<T1, T2, ..., TN>::type`;  
  
-   en todos los demás casos es un error.  
  
## Ejemplo  
  
```  
// std_tr1__functional__result_of.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
double square(double x)   
    {   
    return (x * x);   
    }   
  
template<class Fun,   
    class Arg>   
    void test_result(const Fun& fun, Arg arg)   
    {   
    typename std::result_of<Fun(Arg)>::type val = fun(arg);   
    std::cout << "val == " << val << std::endl;   
    }   
  
int main()   
    {   
    test_result(&square, 3.0);   
  
    return (0);   
    }  
  
```  
  
  **\=\= val 9**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std