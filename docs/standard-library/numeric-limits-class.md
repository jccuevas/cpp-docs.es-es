---
title: "numeric_limits (Clase) | Microsoft Docs"
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
  - "std::numeric_limits"
  - "std.numeric_limits"
  - "numeric_limits"
  - "limits/std::numeric_limits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric_limits (clase)"
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
caps.latest.revision: 26
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# numeric_limits (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe propiedades aritméticas de tipos numéricos integrados.  
  
## Sintaxis  
  
```  
template<classType> class numeric_limits  
```  
  
#### Parámetros  
 `Type`  
 Tipo de datos del elemento fundamental cuyas propiedades se están probando, consultando o estableciendo.  
  
## Comentarios  
 El encabezado define especializaciones explícitas para los tipos `wchar_t`, `bool`, `char`, `signed char`, `unsigned char`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long`, `float`, `double`, `long double`**,** `long long`, `unsigned long long`, `char16_t` y `char32_t`. Para estas especializaciones explícitas, el miembro [numeric\_limits::is\_specialized](../Topic/numeric_limits::is_specialized.md) es `true` y todos los miembros pertinentes tienen valores significativos. El programa puede proporcionar especializaciones explícitas adicionales. La mayoría de las funciones miembro de la clase describen o prueban implementaciones posibles de `float`.  
  
 Para una especialización arbitraria, ningún miembro tiene valores significativos. Un objeto de miembro que no tiene un valor significativo almacena cero \(o `false`\) y una función miembro que no devuelve un valor significativo devuelve `Type(0)`.  
  
### Constantes y funciones estáticas  
  
|||  
|-|-|  
|[denorm\_min](../Topic/numeric_limits::denorm_min.md)|Devuelve el valor más pequeño distinto de cero desnormalizado.|  
|[digits](../Topic/numeric_limits::digits.md)|Devuelve el número de dígitos de base que el tipo puede representar sin pérdida de precisión.|  
|[digits10](../Topic/numeric_limits::digits10.md)|Devuelve el número de dígitos decimales que el tipo puede representar sin pérdida de precisión.|  
|[epsilon](../Topic/numeric_limits::epsilon.md)|Devuelve la diferencia entre 1 y el valor más pequeño mayor que 1, que el tipo de datos puede representar.|  
|[has\_denorm](../Topic/numeric_limits::has_denorm.md)|Comprueba si un tipo permite valores no normalizados.|  
|[has\_denorm\_loss](../Topic/numeric_limits::has_denorm_loss.md)|Comprueba si se detecta la pérdida de precisión como una pérdida de desnormalización en lugar de como un resultado inexacto.|  
|[has\_infinity](../Topic/numeric_limits::has_infinity.md)|Comprueba si un tipo tiene una representación de infinito positivo.|  
|[has\_quiet\_NaN](../Topic/numeric_limits::has_quiet_NaN.md)|Comprueba si un tipo tiene una representación para un NaN \(no es un número\) silencioso, que no sea de señalización.|  
|[has\_signaling\_NaN](../Topic/numeric_limits::has_signaling_NaN.md)|Comprueba si un tipo tiene una representación para un NaN \(no es un número\) de señalización.|  
|[infinity](../Topic/numeric_limits::infinity.md)|Representación de infinito positivo de un tipo, si está disponible.|  
|[is\_bounded](../Topic/numeric_limits::is_bounded.md)|Comprueba si el conjunto de valores que un tipo puede representar es finito.|  
|[is\_exact](../Topic/numeric_limits::is_exact.md)|Comprueba si los cálculos realizados en un tipo están libres de errores de redondeo.|  
|[is\_iec559](../Topic/numeric_limits::is_iec559.md)|Comprueba si un tipo se ajusta a los estándares IEC 559.|  
|[is\_integer](../Topic/numeric_limits::is_integer.md)|Comprueba si un tipo tiene una representación de entero.|  
|[is\_modulo](../Topic/numeric_limits::is_modulo.md)|Comprueba si un tipo tiene una representación de módulo.|  
|[is\_signed](../Topic/numeric_limits::is_signed.md)|Comprueba si un tipo tiene una representación con signo.|  
|[is\_specialized](../Topic/numeric_limits::is_specialized.md)|Comprueba si un tipo tiene una especialización explícita definida en la clase de plantilla `numeric_limits`.|  
|[lowest](../Topic/numeric_limits::lowest.md)|Devuelve el mayor valor finito negativo.|  
|[max](../Topic/numeric_limits::max.md)|Devuelve el valor finito máximo para un tipo.|  
|[max\_digits10](../Topic/numeric_limits::max_digits10.md)|Devuelve el número de dígitos decimales necesarios para asegurarse de que dos valores distintos del tipo tengan distintas representaciones decimales.|  
|[max\_exponent](../Topic/numeric_limits::max_exponent.md)|Devuelve el exponente integral positivo máximo que el tipo de punto flotante puede representar como valor finito cuando se eleva una base de base a esa potencia.|  
|[max\_exponent10](../Topic/numeric_limits::max_exponent10.md)|Devuelve el exponente integral positivo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.|  
|[min](../Topic/numeric_limits::min.md)|Devuelve el valor normalizado mínimo para un tipo.|  
|[min\_exponent](../Topic/numeric_limits::min_exponent.md)|Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de base a esa potencia.|  
|[min\_exponent10](../Topic/numeric_limits::min_exponent10.md)|Devuelve el exponente integral negativo máximo que puede representar el tipo de punto flotante como valor finito cuando se eleva una base de diez a esa potencia.|  
|[quiet\_NaN](../Topic/numeric_limits::quiet_NaN.md)|Devuelve la representación de un NaN \(no es un número\) silencioso para el tipo.|  
|[radix](../Topic/numeric_limits::radix.md)|Devuelve la base integral, llamada base, usada para la representación de un tipo.|  
|[round\_error](../Topic/numeric_limits::round_error.md)|Devuelve el error de redondeo máximo para el tipo.|  
|[round\_style](../Topic/numeric_limits::round_style.md)|Devuelve un valor que describe los diversos métodos que una implementación puede elegir para redondear un valor de punto flotante a un valor entero.|  
|[signaling\_NaN](../Topic/numeric_limits::signaling_NaN.md)|Devuelve la representación de un NaN \(no es un número\) de señalización para el tipo.|  
|[tinyness\_before](../Topic/numeric_limits::tinyness_before.md)|Comprueba si un tipo puede determinar que un valor es demasiado pequeño para representarse como un valor normalizado antes de redondearlo.|  
|[traps](../Topic/numeric_limits::traps.md)|Comprueba si la captura que informa sobre excepciones aritméticas está implementada para un tipo.|  
  
## Requisitos  
 **Encabezado:** \<limits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)