---
title: "literales chrono | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# literales chrono
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\(C \+\+ 14\) El encabezado \<chrono\> define 12 [literales definidos por el usuario](../cpp/user-defined-literals-cpp.md) para facilitar el uso de literales que representan horas, minutos, segundos, milisegundos, microsegundos y nanosegundos. Cada literal definido por el usuario tiene una sobrecarga de entero y de punto flotante. Los literales se definen en el espacio de nombres en línea literals::chrono\_literals que se incluye en el ámbito automáticamente cuando std:: chrono está en el ámbito.  
  
## Sintaxis  
  
```vb  
inline namespace literals {  
    inline namespace chrono_literals {  
  
        // return integral hours  
        constexpr chrono::hours operator "" h(unsigned long long Val);  
  
        // return floating-point hours  
        constexpr chrono::duration<double, ratio<3600> > operator "" h(long double Val);  
  
        // return integral minutes  
        constexpr chrono::minutes(operator "" min)(unsigned long long Val);  
  
        // return floating-point minutes  
        constexpr chrono::duration<double, ratio<60> >(operator "" min)(long double Val);  
  
        // return integral seconds  
        constexpr chrono::seconds operator "" s(unsigned long long Val);  
  
        // return floating-point seconds  
        constexpr chrono::duration<double> operator "" s(long double Val);  
  
        // return integral milliseconds  
        constexpr chrono::milliseconds operator "" ms(unsigned long long Val);  
  
         // return floating-point milliseconds  
        constexpr chrono::duration<double, milli> operator "" ms(long double Val);  
  
        // return integral microseconds      
        constexpr chrono::microseconds operator "" us(unsigned long long Val);  
  
        // return floating-point microseconds  
        inline constexpr chrono::duration<double, micro> operator "" us(long double Val);  
  
        // return integral nanoseconds  
        inline constexpr chrono::nanoseconds operator "" ns(unsigned long long Val);  
  
        // return floating-point nanoseconds  
        constexpr chrono::duration<double, nano> operator "" ns(long double Val);  
    }// inline namespace chrono_literals  
}// inline namespace literals  
```  
  
```c#  
  
```  
  
## Valor devuelto  
 Los literales que toman un argumento `long long` devuelven un valor o el tipo correspondiente. Los literales que toman un argumento de punto flotante devuelven una [duración](../standard-library/duration-class.md).  
  
## Comentarios  
  
## Ejemplo  
 En los siguientes ejemplos se muestra cómo utilizar los literales chrono.  
  
```  
constexpr auto day = 24h;  
constexpr auto week = 24h * 7;  
constexpr auto my_duration_unit = 108ms;  
```  
  
## Requisitos  
 **Encabezado**: \<chrono\>  
  
 **Espacio de nombres**: std::literals::chrono\_literals  
  
## Vea también  
 [\< chrono \>](../standard-library/chrono.md)