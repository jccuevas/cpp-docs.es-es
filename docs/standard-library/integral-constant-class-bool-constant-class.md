---
title: "integral_constant (clase), bool_constant (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.integral_constant"
  - "integral_constant"
  - "std::tr1::integral_constant"
  - "std.integral_constant"
  - "std::integral_constant"
  - "type_traits/std::integral_constant"
  - "std.bool_constant"
  - "std::bool_constant"
  - "type_traits/std::bool_constant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "integral_constant (clase) [TR1]"
  - "integral_constant"
  - "bool_constant"
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# integral_constant (clase), bool_constant (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un entero constante de un tipo y valor.  
  
## Sintaxis  
  
```  
template <class T, T v>  
    struct integral_constant {  
        static constexpr T value = v;  
        typedef T value_type;  
        typedef integral_constant<T, v> type;  
        constexpr operator value_type() const noexcept { return (value); }  
        constexpr value_type operator()() const noexcept { return (value); }  
    };  
  
template <bool v>  
    using bool_constant = integral_constant<bool, v>;  
  
```  
  
#### Parámetros  
 `T`  
 Tipo de la constante.  
  
 `v`  
 Valor de la constante.  
  
## Comentarios  
 La `integral_constant` clase de plantilla cuando especializado con un tipo entero `T` y un valor `v` de ese tipo, representa un objeto que contiene una constante de ese tipo entero con el valor especificado. El miembro con el nombre `type` es un alias para el tipo de especialización de plantilla generadas y `value` miembro contiene el valor `v` utilizado para crear la especialización.  
  
 La `bool_constant` clase de plantilla es una especialización explícita parcial de `integral_constant` que utiliza `bool` como la `T` argumento.  
  
## Ejemplo  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant < int, 5 > == 5 integral_constant < bool false > == false  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [false\_type \(Typedef\)](../Topic/false_type%20Typedef.md)   
 [true\_type \(Typedef\)](../Topic/true_type%20Typedef.md)