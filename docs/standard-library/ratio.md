---
title: "&lt;ratio&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ratio/std::mega"
  - "ratio/std::peta"
  - "ratio/std::ratio_greater"
  - "ratio/std::micro"
  - "ratio/std::ratio_add"
  - "ratio/std::ratio_not_equal"
  - "ratio/std::hecto"
  - "ratio/std::nano"
  - "ratio/std::ratio_less_equal"
  - "ratio/std::ratio_less"
  - "ratio/std::centi"
  - "ratio/std::ratio_greater_equal"
  - "ratio/std::ratio_subtract"
  - "<ratio>"
  - "ratio/std::atto"
  - "ratio/std::tera"
  - "ratio/std::milli"
  - "ratio/std::ratio_multiply"
  - "ratio/std::kilo"
  - "ratio/std::ratio_divide"
  - "ratio/std::giga"
  - "ratio/std::pico"
  - "ratio/std::femto"
  - "ratio/std::ratio_equal"
  - "ratio/std::ratio"
  - "ratio/std::exa"
  - "ratio/std::deci"
  - "ratio/std::deca"
dev_langs: 
  - "C++"
ms.assetid: 8543e912-2d84-45ea-b3c0-bd7bfacee405
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# &lt;ratio&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya la proporción estándar \<de encabezado\> para definir constantes y las plantillas que se utilizan para almacenar y manipular los números racionales en tiempo de compilación.  
  
## Sintaxis  
  
```cpp  
#include <ratio>  
```  
  
### estructura de la relación  
  
```  
template <intmax_t N, intmax_t D = 1>  
struct ratio  
{  
    static constexpr intmax_t num;  
    static constexpr intmax_t den;  
    typedef ratio<num, den> type;  
};  
```  
  
 [ratio Structure](http://msdn.microsoft.com/es-es/3f7961f4-802b-4251-b3c3-090ef91c0dba) define las constantes estáticas `num` y `den` tales que `num` \/n\/d \=\= de `den` y `num` y `den` no tiene ningún factor común.  `num` \/ `den` es `value` representado por la clase de plantilla.  Por consiguiente, `type` designa la creación `ratio<N0, D0>` que \=\= N0 de `num` y \=\= D0 de `den` .  
  
### Especializaciones  
 \<la proporción\> también define las especializaciones de `ratio` con el formato siguiente.  
  
 `template <class R1, class R2> struct ratio_specialization`  
  
 Cada especialización toma dos parámetros de plantilla que deben ser especializaciones de `ratio`.  El valor de `type` está determinado por una operación lógica asociada.  
  
|Name|Valor de `type`|  
|----------|---------------------|  
|`ratio_add`|`R1 + R2`|  
|`ratio_divide`|`R1 / R2`|  
|`ratio_equal`|`R1 == R2`|  
|`ratio_greater`|`R1 > R2`|  
|`ratio_greater_equal`|`R1 >= R2`|  
|`ratio_less`|`R1 < R2`|  
|`ratio_less_equal`|`R1 <= R2`|  
|`ratio_multiply`|`R1 * R2`|  
|`ratio_not_equal`|`!(R1 == R2)`|  
|`ratio_subtract`|`R1 - R2`|  
  
### typedefs  
  
```  
  
typedef ratio<1,        1000000000000000000> atto;  
typedef ratio<1,           1000000000000000> femto;  
typedef ratio<1,              1000000000000> pico;  
typedef ratio<1,                 1000000000> nano;  
typedef ratio<1,                    1000000> micro;  
typedef ratio<1,                       1000> milli;  
typedef ratio<1,                        100> centi;  
typedef ratio<1,                         10> deci;  
typedef ratio<                        10, 1> deca;  
typedef ratio<                       100, 1> hecto;  
typedef ratio<                      1000, 1> kilo;  
typedef ratio<                   1000000, 1> mega;  
typedef ratio<                1000000000, 1> giga;  
typedef ratio<             1000000000000, 1> tera;  
typedef ratio<          1000000000000000, 1> peta;  
typedef ratio<       1000000000000000000, 1> exa;  
  
```  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)