---
title: "Concurrency::precise_math (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_math/Concurrency::precise_math"
dev_langs: 
  - "C++"
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Concurrency::precise_math (Espacio de nombres)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Las funciones del espacio de nombres `precise_math` cumplen el estándar C99.  Las versiones de simple precisión y de doble precisión de cada función están incluidas.  Por ejemplo, `acos` es la versión de doble precisión y `acosf` es la versión de precisión sencilla.  Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de precisión doble extendida en el acelerador.  Se puede utilizar [accelerator::supports\_double\_precision \(Miembro de datos\)](../Topic/accelerator::supports_double_precision%20Data%20Member.md) para determinar si estas funciones se pueden ejecutar en un acelerador específico.  
  
## Sintaxis  
  
```vb  
namespace precise_math;  
```  
  
#### Parámetros  
  
## Miembros  
  
### Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[acos \(Función\)](../Topic/acos%20Function.md)|Sobrecargado.  Calcula el arcocoseno del argumento.|  
|[acosf \(Función\)](../Topic/acosf%20Function.md)|Calcula el arcocoseno del argumento.|  
|[acosh \(Función\)](../Topic/acosh%20Function.md)|Sobrecargado.  Calcula el coseno hiperbólico inverso de argumento|  
|[acoshf \(Función\)](../Topic/acoshf%20Function.md)|Calcula el coseno hiperbólico inverso de argumento|  
|[asin \(Función\)](../Topic/asin%20Function.md)|Sobrecargado.  Calcula el arcoseno del argumento.|  
|[asinf \(Función\)](../Topic/asinf%20Function.md)|Calcula el arcoseno del argumento.|  
|[asinh \(Función\)](../Topic/asinh%20Function.md)|Sobrecargado.  Calcula el seno hiperbólico inverso del argumento|  
|[asinhf \(Función\)](../Topic/asinhf%20Function.md)|Calcula el seno hiperbólico inverso del argumento|  
|[atan \(Función\)](../Topic/atan%20Function.md)|Sobrecargado.  Calcula el arcotangente del argumento.|  
|[atan2 \(Función\)](../Topic/atan2%20Function.md)|Sobrecargado.  Calcula el arcotangente de \_Y\/\_X.|  
|[atan2f \(Función\)](../Topic/atan2f%20Function.md)|Calcula el arcotangente de \_Y\/\_X.|  
|[atanf \(Función\)](../Topic/atanf%20Function.md)|Calcula el arcotangente del argumento.|  
|[atanh \(Función\)](../Topic/atanh%20Function.md)|Sobrecargado.  Calcula la tangente hiperbólica inversa del argumento|  
|[atanhf \(Función\)](../Topic/atanhf%20Function.md)|Calcula la tangente hiperbólica inversa del argumento|  
|[cbrt \(Función\)](../Topic/cbrt%20Function.md)|Sobrecargado.  Calcula la raíz cúbica real del argumento|  
|[cbrtf \(Función\)](../Topic/cbrtf%20Function.md)|Calcula la raíz cúbica real del argumento|  
|[ceil \(Función\)](../Topic/ceil%20Function.md)|Sobrecargado.  Calcula el múltiplo superior del argumento.|  
|[ceilf \(Función\)](../Topic/ceilf%20Function.md)|Calcula el múltiplo superior del argumento.|  
|[copysign \(Función\)](../Topic/copysign%20Function.md)|Sobrecargado.  Produce un valor con la magnitud de \_X y el signo de \_Y|  
|[copysignf \(Función\)](../Topic/copysignf%20Function.md)|Produce un valor con la magnitud de \_X y el signo de \_Y|  
|[cos \(Función\)](../Topic/cos%20Function.md)|Sobrecargado.  Calcula el coseno del argumento.|  
|[cosf \(Función\)](../Topic/cosf%20Function.md)|Calcula el coseno del argumento.|  
|[cosh \(Función\)](../Topic/cosh%20Function.md)|Sobrecargado.  Calcula el valor del coseno hiperbólico del argumento.|  
|[coshf \(Función\)](../Topic/coshf%20Function.md)|Calcula el valor del coseno hiperbólico del argumento.|  
|[cospi \(Función\)](../Topic/cospi%20Function.md)|Sobrecargado.  Calcula el valor del coseno de pi \* \_X|  
|[cospif \(Función\)](../Topic/cospif%20Function.md)|Calcula el valor del coseno de pi \* \_X|  
|[erf \(Función\)](../Topic/erf%20Function.md)|Sobrecargado.  Calcula la función error de \_X|  
|[erfc \(Función\)](../Topic/erfc%20Function.md)|Sobrecargado.  Calcula la función de error complementaria de \_X|  
|[erfcf \(Función\)](../Topic/erfcf%20Function.md)|Calcula la función de error complementaria de \_X|  
|[erfcinv \(Función\)](../Topic/erfcinv%20Function.md)|Sobrecargado.  Calcula el error de la función inversa complementaria de \_X|  
|[erfcinvf \(Función\)](../Topic/erfcinvf%20Function.md)|Calcula el error de la función inversa complementaria de \_X|  
|[erff \(Función\)](../Topic/erff%20Function.md)|Calcula la función error de \_X|  
|[erfinv \(Función\)](../Topic/erfinv%20Function.md)|Sobrecargado.  Calcula el error de la función inversa de \_X|  
|[erfinvf \(Función\)](../Topic/erfinvf%20Function.md)|Calcula el error de la función inversa de \_X|  
|[exp \(Función\)](../Topic/exp%20Function.md)|Sobrecargado.  Calcula la base e exponencial del argumento.|  
|[exp10 \(Función\)](../Topic/exp10%20Function.md)|Sobrecargado.  Calcula la exponencial en base 10 del argumento.|  
|[exp10f \(Función\)](../Topic/exp10f%20Function.md)|Calcula la exponencial en base 10 del argumento.|  
|[exp2 \(Función\)](../Topic/exp2%20Function.md)|Sobrecargado.  Calcula la exponencial en base 2 del argumento.|  
|[exp2f \(Función\)](../Topic/exp2f%20Function.md)|Calcula la exponencial en base 2 del argumento.|  
|[expf \(Función\)](../Topic/expf%20Function.md)|Calcula la base e exponencial del argumento.|  
|[expm1 \(Función\)](../Topic/expm1%20Function.md)|Sobrecargado.  Calcula la exponencial en base e del argumento, menos 1|  
|[expm1f \(Función\)](../Topic/expm1f%20Function.md)|Calcula la exponencial en base e del argumento, menos 1|  
|[fabs \(Función\)](../Topic/fabs%20Function.md)|Sobrecargado.  Devuelve el valor absoluto del argumento|  
|[fabsf \(Función\)](../Topic/fabsf%20Function.md)|Devuelve el valor absoluto del argumento|  
|[fdim \(Función\)](../Topic/fdim%20Function.md)|Sobrecargado.  Determina la diferencia positiva entre los argumentos|  
|[fdimf \(Función\)](../Topic/fdimf%20Function.md)|Determina la diferencia positiva entre los argumentos|  
|[floor \(Función\)](../Topic/floor%20Function.md)|Sobrecargado.  Calcula el valor inferior del argumento.|  
|[floorf \(Función\)](../Topic/floorf%20Function.md)|Calcula el valor inferior del argumento.|  
|[fma \(Función\)](../Topic/fma%20Function.md)|Sobrecargado.  Cálculo \(\_X \* \_Y\) \+ \_Z, redondeados como una operación ternaria|  
|[fmaf \(Función\)](../Topic/fmaf%20Function.md)|Cálculo \(\_X \* \_Y\) \+ \_Z, redondeados como una operación ternaria|  
|[fmax \(Función\)](../Topic/fmax%20Function.md)|Sobrecargado.  Determina el máximo valor numérico de los argumentos|  
|[fmaxf \(Función\)](../Topic/fmaxf%20Function.md)|Determina el máximo valor numérico de los argumentos|  
|[fmin \(Función\)](../Topic/fmin%20Function.md)|Sobrecargado.  Determina el mínimo valor numérico de los argumentos|  
|[fminf \(Función\)](../Topic/fminf%20Function.md)|Determina el mínimo valor numérico de los argumentos|  
|[fmod \(Función\) \(C\+\+ AMP\)](../Topic/fmod%20Function%20\(C++%20AMP\).md)|Sobrecargado.  Calcula el residuo del punto flotante de \_X\/\_Y.|  
|[fmodf \(Función\)](../Topic/fmodf%20Function.md)|Calcula el residuo del punto flotante de \_X\/\_Y.|  
|[fpclassify \(Función\)](../Topic/fpclassify%20Function.md)|Sobrecargado.  Clasifica el valor del argumento como NaN, infinito, normal, subnormal, cero|  
|[frexp \(Función\)](../Topic/frexp%20Function.md)|Sobrecargado.  Obtiene la mantisa y el exponente de \_X.|  
|[frexpf \(Función\)](../Topic/frexpf%20Function.md)|Obtiene la mantisa y el exponente de \_X.|  
|[hypot \(Función\)](../Topic/hypot%20Function.md)|Sobrecargado.  Calcula la raíz cuadrada de la suma de los cuadrados de \_X y \_Y|  
|[hypotf \(Función\)](../Topic/hypotf%20Function.md)|Calcula la raíz cuadrada de la suma de los cuadrados de \_X y \_Y|  
|[ilogb \(Función\)](../Topic/ilogb%20Function.md)|Sobrecargado.  Extrae el exponente de \_X como valor entero con signo|  
|[ilogbf \(Función\)](../Topic/ilogbf%20Function.md)|Extrae el exponente de \_X como valor entero con signo|  
|[isfinite \(Función\)](../Topic/isfinite%20Function.md)|Sobrecargado.  Determina si el argumento tiene un valor finito|  
|[isinf \(Función\)](../Topic/isinf%20Function.md)|Sobrecargado.  Determina si el argumento es infinito|  
|[isnan \(Función\)](../Topic/isnan%20Function.md)|Sobrecargado.  Determina si el argumento es NaN|  
|[isnormal \(Función\)](../Topic/isnormal%20Function.md)|Sobrecargado.  Determina si el argumento es normal|  
|[ldexp \(Función\)](../Topic/ldexp%20Function.md)|Sobrecargado.  Calcula un número real a partir de la mantisa y el exponente.|  
|[ldexpf \(Función\)](../Topic/ldexpf%20Function.md)|Calcula un número real a partir de la mantisa y el exponente.|  
|[lgamma \(Función\)](../Topic/lgamma%20Function.md)|Sobrecargado.  Calcula el logaritmo natural del valor absoluto de gamma del argumento|  
|[lgammaf \(Función\)](../Topic/lgammaf%20Function.md)|Calcula el logaritmo natural del valor absoluto de gamma del argumento|  
|[log \(Función\)](../Topic/log%20Function.md)|Sobrecargado.  Calcula el logaritmo en base e del argumento.|  
|[log10 \(Función\)](../Topic/log10%20Function.md)|Sobrecargado.  Calcula el logaritmo en base 10 del argumento.|  
|[log10f \(Función\)](../Topic/log10f%20Function.md)|Calcula el logaritmo en base 10 del argumento.|  
|[log1p \(Función\)](../Topic/log1p%20Function.md)|Sobrecargado.  Calcula el logaritmo en base e de 1 más el argumento|  
|[log1pf \(Función\)](../Topic/log1pf%20Function.md)|Calcula el logaritmo en base e de 1 más el argumento|  
|[log2 \(Función\)](../Topic/log2%20Function.md)|Sobrecargado.  Calcula el logaritmo en base 2 del argumento.|  
|[log2f \(Función\)](../Topic/log2f%20Function.md)|Calcula el logaritmo en base 2 del argumento.|  
|[logb \(Función\)](../Topic/logb%20Function.md)|Sobrecargado.  Extrae el exponente de \_X, como un valor entero con signo en formato en coma flotante|  
|[logbf \(Función\)](../Topic/logbf%20Function.md)|Extrae el exponente de \_X, como un valor entero con signo en formato en coma flotante|  
|[logf \(Función\)](../Topic/logf%20Function.md)|Calcula el logaritmo en base e del argumento.|  
|[modf \(Función\)](../Topic/modf%20Function.md)|Sobrecargado.  Divide \_X en fracciones y enteros.|  
|[modff \(Función\)](../Topic/modff%20Function.md)|Divide \_X en fracciones y enteros.|  
|[nan \(Función\)](../Topic/nan%20Function.md)|Devuelve un NaN reservado|  
|[nanf \(Función\)](../Topic/nanf%20Function.md)|Devuelve un NaN reservado|  
|[nearbyint \(Función\)](../Topic/nearbyint%20Function.md)|Sobrecargado.  Redondea el argumento en un valor entero en formato flotante, utilizando la dirección de redondeo actual.|  
|[nearbyintf \(Función\)](../Topic/nearbyintf%20Function.md)|Redondea el argumento en un valor entero en formato flotante, utilizando la dirección de redondeo actual.|  
|[nextafter \(Función\)](../Topic/nextafter%20Function.md)|Sobrecargado.  Determine el valor siguiente que se puede representar, en el tipo de función, después de \_X en la dirección de \_Y|  
|[nextafterf \(Función\)](../Topic/nextafterf%20Function.md)|Determine el valor siguiente que se puede representar, en el tipo de función, después de \_X en la dirección de \_Y|  
|[phi \(Función\)](../Topic/phi%20Function.md)|Sobrecargado.  Devuelve la función de distribución acumulativa del argumento|  
|[phif \(Función\)](../Topic/phif%20Function.md)|Devuelve la función de distribución acumulativa del argumento|  
|[pow \(Función\)](../Topic/pow%20Function.md)|Sobrecargado.  Calcula el valor de \_X elevado a la potencia \_Y|  
|[powf \(Función\)](../Topic/powf%20Function.md)|Calcula el valor de \_X elevado a la potencia \_Y|  
|[probit \(Función\)](../Topic/probit%20Function.md)|Sobrecargado.  Devuelve la función de distribución acumulativa inversa del argumento|  
|[probitf \(Función\)](../Topic/probitf%20Function.md)|Devuelve la función de distribución acumulativa inversa del argumento|  
|[rcbrt \(Función\)](../Topic/rcbrt%20Function.md)|Sobrecargado.  Devuelve el recíproco de la raíz cúbica del argumento|  
|[rcbrtf \(Función\)](../Topic/rcbrtf%20Function.md)|Devuelve el recíproco de la raíz cúbica del argumento|  
|[remainder \(Función\)](../Topic/remainder%20Function.md)|Sobrecargado.  Calcula el residuo: \_X REM \_Y|  
|[remainderf \(Función\)](../Topic/remainderf%20Function.md)|Calcula el residuo: \_X REM \_Y|  
|[remquo \(Función\)](../Topic/remquo%20Function.md)|Sobrecargado.  Calcula el mismo residuo que \_Y REM antes de \_X.  También calcula los 23 bits inferiores de cociente entero \_X\/\_Y, y da a ese valor el mismo signo que a \_X\/\_Y.  Almacena el valor con signo en el entero designado por \_Quo.|  
|[remquof \(Función\)](../Topic/remquof%20Function.md)|Calcula el mismo residuo que \_Y REM antes de \_X.  También calcula los 23 bits inferiores de cociente entero \_X\/\_Y, y da a ese valor el mismo signo que a \_X\/\_Y.  Almacena el valor con signo en el entero designado por \_Quo.|  
|[round \(Función\)](../Topic/round%20Function.md)|Sobrecargado.  Redondea \_X al entero más cercano|  
|[roundf \(Función\)](../Topic/roundf%20Function.md)|Redondea \_X al entero más cercano|  
|[rsqrt \(Función\)](../Topic/rsqrt%20Function.md)|Sobrecargado.  Devuelve el valor recíproco de la raíz cuadrada del argumento|  
|[rsqrtf \(Función\)](../Topic/rsqrtf%20Function.md)|Devuelve el valor recíproco de la raíz cuadrada del argumento|  
|[scalb \(Función\)](../Topic/scalb%20Function.md)|Sobrecargado.  Multiplica el \_X por FLT\_RADIX a la potencia \_Y|  
|[scalbf \(Función\)](../Topic/scalbf%20Function.md)|Multiplica el \_X por FLT\_RADIX a la potencia \_Y|  
|[scalbn \(Función\)](../Topic/scalbn%20Function.md)|Sobrecargado.  Multiplica el \_X por FLT\_RADIX a la potencia \_Y|  
|[scalbnf \(Función\)](../Topic/scalbnf%20Function.md)|Multiplica el \_X por FLT\_RADIX a la potencia \_Y|  
|[signbit \(Función\)](../Topic/signbit%20Function.md)|Sobrecargado.  Determina si el signo de \_X es negativo|  
|[signbitf \(Función\)](../Topic/signbitf%20Function.md)|Determina si el signo de \_X es negativo|  
|[sin \(Función\)](../Topic/sin%20Function.md)|Sobrecargado.  Calcula el valor del seno del argumento.|  
|[sincos \(Función\)](../Topic/sincos%20Function.md)|Sobrecargado.  Calcula el valor del seno y el coseno de \_X|  
|[sincosf \(Función\)](../Topic/sincosf%20Function.md)|Calcula el valor del seno y el coseno de \_X|  
|[sinf \(Función\)](../Topic/sinf%20Function.md)|Calcula el valor del seno del argumento.|  
|[sinh \(Función\)](../Topic/sinh%20Function.md)|Sobrecargado.  Calcula el valor hiperbólico del seno del argumento.|  
|[sinhf \(Función\)](../Topic/sinhf%20Function.md)|Calcula el valor hiperbólico del seno del argumento.|  
|[sinpi \(Función\)](../Topic/sinpi%20Function.md)|Sobrecargado.  Calcula el valor del seno de pi \* \_X|  
|[sinpif \(Función\)](../Topic/sinpif%20Function.md)|Calcula el valor del seno de pi \* \_X|  
|[sqrt \(Función\)](../Topic/sqrt%20Function.md)|Sobrecargado.  Calcula la raíz cuadrada del argumento|  
|[sqrtf \(Función\)](../Topic/sqrtf%20Function.md)|Calcula la raíz cuadrada del argumento|  
|[tan \(Función\)](../Topic/tan%20Function.md)|Sobrecargado.  Calcula el valor de la tangente del argumento.|  
|[tanf \(Función\)](../Topic/tanf%20Function.md)|Calcula el valor de la tangente del argumento.|  
|[tanh \(Función\)](../Topic/tanh%20Function.md)|Sobrecargado.  Calcula el valor de la tangente hiperbólica del argumento.|  
|[tanhf \(Función\)](../Topic/tanhf%20Function.md)|Calcula el valor de la tangente hiperbólica del argumento.|  
|[tanpi \(Función\)](../Topic/tanpi%20Function.md)|Sobrecargado.  Calcula el valor de la tangente de pi \* \_X|  
|[tanpif \(Función\)](../Topic/tanpif%20Function.md)|Calcula el valor de la tangente de pi \* \_X|  
|[tgamma \(Función\)](../Topic/tgamma%20Function.md)|Sobrecargado.  Calcula la función gamma de \_X|  
|[tgammaf \(Función\)](../Topic/tgammaf%20Function.md)|Calcula la función gamma de \_X|  
|[trunc \(Función\)](../Topic/trunc%20Function.md)|Sobrecargado.  Trunca el argumento del componente entero|  
|[truncf \(Función\)](../Topic/truncf%20Function.md)|Trunca el argumento del componente entero|  
  
## Requisitos  
 **Encabezado:** amp\_math.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)