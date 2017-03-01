---
title: Namespace precise_math | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::precise_math
dev_langs:
- C++
ms.assetid: ba653308-dc28-4384-b2fd-6cd718a72f91
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b64bd3e3702701ae2685d6688d88988dd91dc5d0
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace"></a>Concurrency::precise_math (Espacio de nombres)
Las funciones del espacio de nombres `precise_math` cumplen el estándar C99. Precisión de una sola y se incluyen versiones de doble precisión de cada función. Por ejemplo, `acos` es la versión de doble precisión y `acosf` es la versión de precisión sencilla. Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador. Puede usar el [accelerator::supports_double_precision miembro de datos](accelerator-class.md#supports_double_precision) para determinar si puede ejecutar estas funciones en un acelerador específico. 

  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
namespace precise_math;  
```  
  
#### <a name="parameters"></a>Parámetros  
  
## <a name="members"></a>Miembros  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[ACOS (función)](concurrency-precise-math-namespace-functions.md#acos)|Sobrecargado. Calcula el arco coseno del argumento|  
|[acosf (función)](concurrency-precise-math-namespace-functions.md#acosf)|Calcula el arco coseno del argumento|  
|[ACOSH (función)](concurrency-precise-math-namespace-functions.md#acosh)|Sobrecargado. Calcula el coseno hiperbólico inverso del argumento|  
|[acoshf (función)](concurrency-precise-math-namespace-functions.md#acoshf)|Calcula el coseno hiperbólico inverso del argumento|  
|[ASIN (función)](concurrency-precise-math-namespace-functions.md#asin)|Sobrecargado. Calcula el arco seno del argumento|  
|[asinf (función)](concurrency-precise-math-namespace-functions.md#asinf)|Calcula el arco seno del argumento|  
|[Asinh (función)](concurrency-precise-math-namespace-functions.md#asinh)|Sobrecargado. Calcula el seno hiperbólico inverso del argumento|  
|[asinhf (función)](concurrency-precise-math-namespace-functions.md#asinhf)|Calcula el seno hiperbólico inverso del argumento|  
|[ATAN (función)](concurrency-precise-math-namespace-functions.md#atan)|Sobrecargado. Calcula el arco tangente del argumento|  
|[ATAN2 (función)](concurrency-precise-math-namespace-functions.md#atan2)|Sobrecargado. Calcula el arco tangente de _Y/_X|  
|[atan2f (función)](concurrency-precise-math-namespace-functions.md#atan2f)|Calcula el arco tangente de _Y/_X|  
|[atanf (función)](concurrency-precise-math-namespace-functions.md#atanf)|Calcula el arco tangente del argumento|  
|[ATANH (función)](concurrency-precise-math-namespace-functions.md#atanh)|Sobrecargado. Calcula la tangente hiperbólica inversa del argumento|  
|[atanhf (función)](concurrency-precise-math-namespace-functions.md#atanhf)|Calcula la tangente hiperbólica inversa del argumento|  
|[cbrt (función)](concurrency-precise-math-namespace-functions.md#cbrt)|Sobrecargado. Calcula la raíz cúbica real del argumento|  
|[cbrtf (función)](concurrency-precise-math-namespace-functions.md#cbrtf)|Calcula la raíz cúbica real del argumento|  
|[ceil (función)](concurrency-precise-math-namespace-functions.md#ceil)|Sobrecargado. Calcula el límite superior del argumento|  
|[ceilf (función)](concurrency-precise-math-namespace-functions.md#ceilf)|Calcula el límite superior del argumento|  
|[copysign (función)](concurrency-precise-math-namespace-functions.md#copysign)|Sobrecargado. Genera un valor con la magnitud de _X y el signo de _Y|  
|[copysignf (función)](concurrency-precise-math-namespace-functions.md#copysignf)|Genera un valor con la magnitud de _X y el signo de _Y|  
|[COS (función)](concurrency-precise-math-namespace-functions.md#cos)|Sobrecargado. Calcula el coseno del argumento|  
|[cosf (función)](concurrency-precise-math-namespace-functions.md#cosf)|Calcula el coseno del argumento|  
|[COSH (función)](concurrency-precise-math-namespace-functions.md#cosh)|Sobrecargado. Calcula el valor de coseno hiperbólico del argumento|  
|[coshf (función)](concurrency-precise-math-namespace-functions.md#coshf)|Calcula el valor de coseno hiperbólico del argumento|  
|[cospi (función)](concurrency-precise-math-namespace-functions.md#cospi)|Sobrecargado. Calcula el valor de coseno de pi * _X|  
|[cospif (función)](concurrency-precise-math-namespace-functions.md#cospif)|Calcula el valor de coseno de pi * _X|  
|[ERF (función)](concurrency-precise-math-namespace-functions.md#erf)|Sobrecargado. Calcula la función error de _X|  
|[ERFC (función)](concurrency-precise-math-namespace-functions.md#erfc)|Sobrecargado. Calcula la función de error complementaria de _X|  
|[erfcf (función)](concurrency-precise-math-namespace-functions.md#erfcf)|Calcula la función de error complementaria de _X|  
|[erfcinv (función)](concurrency-precise-math-namespace-functions.md#erfcinv)|Sobrecargado. Calcula la función de error complementaria inverso de _X|  
|[erfcinvf (función)](concurrency-precise-math-namespace-functions.md#erfcinvf)|Calcula la función de error complementaria inverso de _X|  
|[erff (función)](concurrency-precise-math-namespace-functions.md#erff)|Calcula la función error de _X|  
|[erfinv (función)](concurrency-precise-math-namespace-functions.md#erfinv)|Sobrecargado. Calcula la función error inverso de _X|  
|[erfinvf (función)](concurrency-precise-math-namespace-functions.md#erfinvf)|Calcula la función error inverso de _X|  
|[EXP (función)](concurrency-precise-math-namespace-functions.md#exp)|Sobrecargado. Calcula la base e exponencial del argumento|  
|[EXP10 (función)](concurrency-precise-math-namespace-functions.md#exp10)|Sobrecargado. Calcula el valor exponencial del argumento de base&10;|  
|[exp10f (función)](concurrency-precise-math-namespace-functions.md#exp10f)|Calcula el valor exponencial del argumento de base&10;|  
|[Exp2 (función)](concurrency-precise-math-namespace-functions.md#exp2)|Sobrecargado. Calcula el valor exponencial del argumento de base&2;|  
|[exp2f (función)](concurrency-precise-math-namespace-functions.md#exp2f)|Calcula el valor exponencial del argumento de base&2;|  
|[expf (función)](concurrency-precise-math-namespace-functions.md#expf)|Calcula la base e exponencial del argumento|  
|[expm1 (función)](concurrency-precise-math-namespace-functions.md#expm1)|Sobrecargado. Calcula la base e exponencial del argumento, menos 1|  
|[expm1f (función)](concurrency-precise-math-namespace-functions.md#expm1f)|Calcula la base e exponencial del argumento, menos 1|  
|[fabs (función)](concurrency-precise-math-namespace-functions.md#fabs)|Sobrecargado. Devuelve el valor absoluto del argumento|  
|[fabsf (función)](concurrency-precise-math-namespace-functions.md#fabsf)|Devuelve el valor absoluto del argumento|  
|[fdim (función)](concurrency-precise-math-namespace-functions.md#fdim)|Sobrecargado. Determina la diferencia positiva entre los argumentos|  
|[fdimf (función)](concurrency-precise-math-namespace-functions.md#fdimf)|Determina la diferencia positiva entre los argumentos|  
|[Floor (función)](concurrency-precise-math-namespace-functions.md#floor)|Sobrecargado. Calcula el límite inferior del argumento|  
|[floorf (función)](concurrency-precise-math-namespace-functions.md#floorf)|Calcula el límite inferior del argumento|  
|[FMA (función)](concurrency-precise-math-namespace-functions.md#fma)|Sobrecargado. Proceso (_X * _Y) + _Z, redondeado tal y como una sola operación ternaria|  
|[fmaf (función)](concurrency-precise-math-namespace-functions.md#fmaf)|Proceso (_X * _Y) + _Z, redondeado tal y como una sola operación ternaria|  
|[Fmax (función)](concurrency-precise-math-namespace-functions.md#fmax)|Sobrecargado. Determinar el valor numérico máximo de los argumentos|  
|[fmaxf (función)](concurrency-precise-math-namespace-functions.md#fmaxf)|Determinar el valor numérico máximo de los argumentos|  
|[Fmin (función)](concurrency-precise-math-namespace-functions.md#fmin)|Sobrecargado. Determinar el valor numérico mínimo de los argumentos|  
|[fminf (función)](concurrency-precise-math-namespace-functions.md#fminf)|Determinar el valor numérico mínimo de los argumentos|  
|[fmod (función) (C++ AMP)](concurrency-precise-math-namespace-functions.md#fmod)|Sobrecargado. Calcula el resto de punto flotante de _X/_Y|  
|[fmodf (función)](concurrency-precise-math-namespace-functions.md#fmodf)|Calcula el resto de punto flotante de _X/_Y|  
|[fpclassify (función)](concurrency-precise-math-namespace-functions.md#fpclassify)|Sobrecargado. Clasifica el valor del argumento como cero normal infinito, NaN, subnormal,|  
|[frexp (función)](concurrency-precise-math-namespace-functions.md#frexp)|Sobrecargado. Obtiene la mantisa y el exponente de _X|  
|[frexpf (función)](concurrency-precise-math-namespace-functions.md#frexpf)|Obtiene la mantisa y el exponente de _X|  
|[hypot (función)](concurrency-precise-math-namespace-functions.md#hypot)|Sobrecargado. Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y|  
|[hypotf (función)](concurrency-precise-math-namespace-functions.md#hypotf)|Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y|  
|[ilogb (función)](concurrency-precise-math-namespace-functions.md#ilogb)|Sobrecargado. Extraiga al exponente de _X como un valor int con signo|  
|[ilogbf (función)](concurrency-precise-math-namespace-functions.md#ilogbf)|Extraiga al exponente de _X como un valor int con signo|  
|[isFinite (función)](concurrency-precise-math-namespace-functions.md#isfinite)|Sobrecargado. Determina si el argumento tiene un valor finito|  
|[isinf (función)](concurrency-precise-math-namespace-functions.md#isinf)|Sobrecargado. Determina si el argumento es un infinito|  
|[isNaN (función)](concurrency-precise-math-namespace-functions.md#isnan)|Sobrecargado. Determina si el argumento es un NaN|  
|[isnormal (función)](concurrency-precise-math-namespace-functions.md#isnormal)|Sobrecargado. Determina si el argumento es normal|  
|[ldexp (función)](concurrency-precise-math-namespace-functions.md#ldexp)|Sobrecargado. Calcula un número real de la mantisa y exponente|  
|[ldexpf (función)](concurrency-precise-math-namespace-functions.md#ldexpf)|Calcula un número real de la mantisa y exponente|  
|[lgamma (función)](concurrency-precise-math-namespace-functions.md#lgamma)|Sobrecargado. Calcula el logaritmo natural del valor absoluto de gamma del argumento|  
|[lgammaf (función)](concurrency-precise-math-namespace-functions.md#lgammaf)|Calcula el logaritmo natural del valor absoluto de gamma del argumento|  
|[log (función)](concurrency-precise-math-namespace-functions.md#log)|Sobrecargado. Calcula el logaritmo en base e de argumento|  
|[LOG10 (función)](concurrency-precise-math-namespace-functions.md#log10)|Sobrecargado. Calcula el logaritmo en base&10; del argumento|  
|[log10f (función)](concurrency-precise-math-namespace-functions.md#log10f)|Calcula el logaritmo en base&10; del argumento|  
|[log1p (función)](concurrency-precise-math-namespace-functions.md#log1p)|Sobrecargado. Calcula el logaritmo en base e de 1 y el argumento|  
|[log1pf (función)](concurrency-precise-math-namespace-functions.md#log1pf)|Calcula el logaritmo en base e de 1 y el argumento|  
|[LOG2 (función)](concurrency-precise-math-namespace-functions.md#log2)|Sobrecargado. Calcula el logaritmo en base&2; del argumento|  
|[log2f (función)](concurrency-precise-math-namespace-functions.md#log2f)|Calcula el logaritmo en base&2; del argumento|  
|[logb (función)](concurrency-precise-math-namespace-functions.md#logb)|Sobrecargado. Extrae al exponente de _X, como un valor entero con signo en formato de punto flotante|  
|[logbf (función)](concurrency-precise-math-namespace-functions.md#logbf)|Extrae al exponente de _X, como un valor entero con signo en formato de punto flotante|  
|[logf (función)](concurrency-precise-math-namespace-functions.md#logf)|Calcula el logaritmo en base e de argumento|  
|[modf (función)](concurrency-precise-math-namespace-functions.md#modf)|Sobrecargado. Divide _X en fracciones y partes enteras.|  
|[modff (función)](concurrency-precise-math-namespace-functions.md#modff)|Divide _X en fracciones y partes enteras.|  
|[NaN (función)](concurrency-precise-math-namespace-functions.md#nan)|Devuelve un valor NaN quiet|  
|[nanf (función)](concurrency-precise-math-namespace-functions.md#nanf)|Devuelve un valor NaN quiet|  
|[nearbyint (función)](concurrency-precise-math-namespace-functions.md#nearbyint)|Sobrecargado. Redondea el argumento en un valor entero en formato de punto flotante, utilizando la dirección de redondeo actual.|  
|[nearbyintf (función)](concurrency-precise-math-namespace-functions.md#nearbyintf)|Redondea el argumento en un valor entero en formato de punto flotante, utilizando la dirección de redondeo actual.|  
|[nextafter (función)](concurrency-precise-math-namespace-functions.md#nextafter)|Sobrecargado. Determinar el siguiente valor representable, en el tipo de la función, tras _X en la dirección de _Y|  
|[nextafterf (función)](concurrency-precise-math-namespace-functions.md#nextafterf)|Determinar el siguiente valor representable, en el tipo de la función, tras _X en la dirección de _Y|  
|[PHI (función)](concurrency-precise-math-namespace-functions.md#phi)|Sobrecargado. Devuelve la función de distribución acumulativa del argumento|  
|[phif (función)](concurrency-precise-math-namespace-functions.md#phif)|Devuelve la función de distribución acumulativa del argumento|  
|[Pow (función)](concurrency-precise-math-namespace-functions.md#pow)|Sobrecargado. Calcula _X elevado a la potencia de _Y|  
|[powf (función)](concurrency-precise-math-namespace-functions.md#powf)|Calcula _X elevado a la potencia de _Y|  
|[probit (función)](concurrency-precise-math-namespace-functions.md#probit)|Sobrecargado. Devuelve la función de distribución acumulativa inversa del argumento|  
|[probitf (función)](concurrency-precise-math-namespace-functions.md#probitf)|Devuelve la función de distribución acumulativa inversa del argumento|  
|[rcbrt (función)](concurrency-precise-math-namespace-functions.md#rcbrt)|Sobrecargado. Devuelve el inverso de la raíz cúbica del argumento|  
|[rcbrtf (función)](concurrency-precise-math-namespace-functions.md#rcbrtf)|Devuelve el inverso de la raíz cúbica del argumento|  
|[Remainder (función)](concurrency-precise-math-namespace-functions.md#remainder)|Sobrecargado. Calcula el resto: _X REM _Y|  
|[remainderf (función)](concurrency-precise-math-namespace-functions.md#remainderf)|Calcula el resto: _X REM _Y|  
|[remquo (función)](concurrency-precise-math-namespace-functions.md#remquo)|Sobrecargado. Calcula el resto de la mismo como _X REM _Y. También calcula el 23 bits inferiores del cociente entero _X/_Y y proporciona el mismo signo que _X/_Y de ese valor. Almacena este valor con signo en el entero que se señala _Quo.|  
|[remquof (función)](concurrency-precise-math-namespace-functions.md#remquof)|Calcula el resto de la mismo como _X REM _Y. También calcula el 23 bits inferiores del cociente entero _X/_Y y proporciona el mismo signo que _X/_Y de ese valor. Almacena este valor con signo en el entero que se señala _Quo.|  
|[Round (función)](concurrency-precise-math-namespace-functions.md#round)|Sobrecargado. Redondea _X al entero más próximo|  
|[roundf (función)](concurrency-precise-math-namespace-functions.md#roundf)|Redondea _X al entero más próximo|  
|[rsqrt (función)](concurrency-precise-math-namespace-functions.md#rsqrt)|Sobrecargado. Devuelve el inverso de la raíz cuadrada del argumento|  
|[rsqrtf (función)](concurrency-precise-math-namespace-functions.md#rsqrtf)|Devuelve el inverso de la raíz cuadrada del argumento|  
|[scalb (función)](concurrency-precise-math-namespace-functions.md#scalb)|Sobrecargado. Multiplica _X por FLT_RADIX en el _Y de energía|  
|[scalbf (función)](concurrency-precise-math-namespace-functions.md#scalbf)|Multiplica _X por FLT_RADIX en el _Y de energía|  
|[scalbn (función)](concurrency-precise-math-namespace-functions.md#scalbn)|Sobrecargado. Multiplica _X por FLT_RADIX en el _Y de energía|  
|[scalbnf (función)](concurrency-precise-math-namespace-functions.md#scalbnf)|Multiplica _X por FLT_RADIX en el _Y de energía|  
|[signbit (función)](concurrency-precise-math-namespace-functions.md#signbit)|Sobrecargado. Determina si el inicio de sesión de _X es negativo|  
|[signbitf (función)](concurrency-precise-math-namespace-functions.md#signbitf)|Determina si el inicio de sesión de _X es negativo|  
|[sin (función)](concurrency-precise-math-namespace-functions.md#sin)|Sobrecargado. Calcula el valor del seno del argumento|  
|[sincos (función)](concurrency-precise-math-namespace-functions.md#sincos)|Sobrecargado. Calcula el seno y coseno el valor de _X|  
|[sincosf (función)](concurrency-precise-math-namespace-functions.md#sincosf)|Calcula el seno y coseno el valor de _X|  
|[sinf (función)](concurrency-precise-math-namespace-functions.md#sinf)|Calcula el valor del seno del argumento|  
|[SINH (función)](concurrency-precise-math-namespace-functions.md#sinh)|Sobrecargado. Calcula el valor del seno hiperbólico del argumento|  
|[sinhf (función)](concurrency-precise-math-namespace-functions.md#sinhf)|Calcula el valor del seno hiperbólico del argumento|  
|[sinpi (función)](concurrency-precise-math-namespace-functions.md#sinpi)|Sobrecargado. Calcula el valor del seno de pi * _X|  
|[sinpif (función)](concurrency-precise-math-namespace-functions.md#sinpif)|Calcula el valor del seno de pi * _X|  
|[SQRT (función)](concurrency-precise-math-namespace-functions.md#sqrt)|Sobrecargado. Calcula la raíz de squre del argumento|  
|[sqrtf (función)](concurrency-precise-math-namespace-functions.md#sqrtf)|Calcula la raíz de squre del argumento|  
|[tan (función)](concurrency-precise-math-namespace-functions.md#tan)|Sobrecargado. Calcula el valor del argumento de tangente|  
|[tanf (función)](concurrency-precise-math-namespace-functions.md#tanf)|Calcula el valor del argumento de tangente|  
|[TANH (función)](concurrency-precise-math-namespace-functions.md#tanh)|Sobrecargado. Calcula el valor de la tangente hiperbólico del argumento|  
|[tanhf (función)](concurrency-precise-math-namespace-functions.md#tanhf)|Calcula el valor de la tangente hiperbólico del argumento|  
|[tanpi (función)](concurrency-precise-math-namespace-functions.md#tanpi)|Sobrecargado. Calcula el valor de tangente de pi * _X|  
|[tanpif (función)](concurrency-precise-math-namespace-functions.md#tanpif)|Calcula el valor de tangente de pi * _X|  
|[tgamma (función)](concurrency-precise-math-namespace-functions.md#tgamma)|Sobrecargado. Calcula la función gamma de _X|  
|[tgammaf (función)](concurrency-precise-math-namespace-functions.md#tgammaf)|Calcula la función gamma de _X|  
|[TRUNC (función)](concurrency-precise-math-namespace-functions.md#trunc)|Sobrecargado. Trunca el argumento para el componente de número entero|  
|[truncf (función)](concurrency-precise-math-namespace-functions.md#truncf)|Trunca el argumento para el componente de número entero|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_math.h  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

