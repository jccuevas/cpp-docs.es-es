---
title: Compatibilidad con cálculos matemáticos y el punto flotante
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: a0ee21378a6feb7ada39dc00f0e181672470e231
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821517"
---
# <a name="math-and-floating-point-support"></a>Compatibilidad con cálculos matemáticos y el punto flotante

La biblioteca en tiempo de ejecución Universal C (UCRT) ofrece muchas funciones de la biblioteca matemática de punto flotante e integrales, incluidas todas las necesarias en ISO C99. Las funciones de punto flotante se implementan para equilibrar el rendimiento con exactitud. Dado que es posible que producir el resultado redondeado correctamente sea excesivamente costoso, estas funciones están diseñadas para generar con eficacia una buena aproximación al resultado redondeado correctamente. En la mayoría de los casos, el resultado producido se encuentra dentro de +/-1 ulp del resultado redondeado correctamente, aunque puede haber casos en los que la falta de precisión sea mayor.

Muchas de las funciones de la biblioteca matemática de punto flotante tienen implementaciones diferentes para distintas arquitecturas de CPU. Por ejemplo, puede que el CRT x86 de 32 bits tenga una implementación distinta que el CRT x64 de 64 bits. Además, algunas de las funciones pueden tener varias implementaciones para una determinada arquitectura de CPU. La implementación más eficaz se selecciona dinámicamente en tiempo de ejecución en función de los conjuntos de instrucciones compatibles con la CPU. Por ejemplo, en el CRT x86 de 32 bits, algunas funciones tienen una implementación x87 y una implementación SSE2. Cuando se ejecuta en una CPU que admite SSE2, se usa la implementación SSE2 más rápida. Cuando se ejecuta en una CPU que no admite SSE2, se usa la implementación x87 más lenta. Dado que es posible que diferentes implementaciones de las funciones de la biblioteca matemática usen distintas instrucciones de CPU y distintos algoritmos para generar sus resultados, puede que las funciones generen diferentes resultados en las CPU. En la mayoría de los casos, los resultados se encuentran dentro de +/-1 ulp del resultado redondeado correctamente, pero los resultados reales pueden variar de una CPU a otra.

Las versiones anteriores de 16 bits de Microsoft C/C++ y Microsoft Visual C++ admiten el tipo **long double** como tipo de datos de punto flotante de precisión de 80 bits. En versiones posteriores de Visual C++, el tipo de datos **long double** es un tipo de datos de punto flotante de precisión de 64 bits idéntico al tipo **double**. El compilador trata **long double** y **double** como tipos distintos, pero las funciones **long double** son idénticas a sus equivalentes **double**. El CRT ofrece versiones de **long double** de las funciones matemáticas para la compatibilidad con código fuente ISO C99, pero tenga en cuenta que la representación binaria puede diferir de otros compiladores.

## <a name="supported-math-and-floating-point-routines"></a>Rutinas admitidas de cálculos matemáticos y punto flotante

|Rutina|Usar|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Calcula el valor absoluto de un tipo de entero
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Calcula el arcocoseno
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Calcula el arcocoseno hiperbólico
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Calcula el arcoseno
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Calcula el arcoseno hiperbólico
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Calcula el arco tangente
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Calcula el arco tangente hiperbólico
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convierte una cadena específica de la configuración regional en un **double**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte una cadena en un **double**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convierte una cadena específica de la configuración regional en un **float** o **long double**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Calcula la raíz cúbica
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Calcula el límite superior
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Calcula el inverso aditivo
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Obtiene y borra el registro de estado de punto flotante
[_control87, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Obtiene y establece la palabra de control de punto flotante
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Versión segura de **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Devuelve un valor que tiene la magnitud de un argumento y el signo de otro
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|Calcula el seno
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Calcula el seno hiperbólico
[div, ldiv, lldiv](../c-runtime-library/reference/div.md)|Calcula el cociente y el resto de dos valores enteros
[_ecvt](../c-runtime-library/reference/ecvt.md), [ecvt](../c-runtime-library/reference/posix-ecvt.md)|Convierte un **double** en una cadena
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Versión segura de **_ecvt**
[erf, erff, erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Calcula la función de error
[erfc, erfcf, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Calcula la función de error complementaria
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Calcula el valor exponencial de *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Calcula el valor exponencial de 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Calcula *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Calcula el valor absoluto de un tipo de punto flotante
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|Convertir un número de punto flotante en una cadena
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Versión segura de **_fcvt**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Determina la diferencia positiva entre dos valores
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Borra las excepciones de punto flotante especificadas
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Almacena el entorno actual de punto flotante
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Obtiene el estado de las excepciones de punto flotante especificadas
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Obtiene el modo de redondeo de punto flotante
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Establece el modo sin interrupción de excepción de punto flotante
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Genera las excepciones de punto flotante especificadas
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Establece el entorno actual de punto flotante
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Establece las marcas de estado de punto flotante especificadas
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Establece el modo de redondeo de punto flotante especificado
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Determina las marcas de estado de excepción de punto flotante que se establecen
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Restaura un entorno de punto flotante y después genera excepciones anteriores
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Calcula el límite inferior
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Calcula una multiplicación y suma fusionadas
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Calcula el máximo de los argumentos
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Calcula el mínimo de los argumentos.
[fmod, fmodf, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Calcula el resto de punto flotante
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Devuelve la clasificación de un valor de punto flotante
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Devuelve la clasificación de un valor de punto flotante
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Establece un controlador de excepciones de punto flotante
[_fpreset](../c-runtime-library/reference/fpreset.md)|Restablece el entorno de punto flotante
[frexp, frexpf, frexpl](../c-runtime-library/reference/frexp.md)|Obtiene la mantisa y el exponente de un número de punto flotante
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|Convertir un número de punto flotante en una cadena
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Versión segura de **_gcvt**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Obtiene o establece una marca para el uso de instrucciones de FMA3 en x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Calcula la hipotenusa
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Calcula el exponente en base 2 del entero
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Calcula el valor absoluto de un tipo de entero
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Calcula el cociente y el resto de dos valores enteros
[isfinite, _finite y _finitef](../c-runtime-library/reference/finite-finitef.md)|Determina si un valor es finito
[isgreater, isgreaterequal, isless, islessequal, islessgreater y isunordered](../c-runtime-library/reference/floating-point-ordering.md)|Compara el orden de dos valores de punto flotante
[isinf](../c-runtime-library/reference/isinf.md)|Determina si un valor de punto flotante es infinito
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Prueba un valor de punto flotante para NaN
[isnormal](../c-runtime-library/reference/isnormal.md)|Prueba si un valor de punto flotante es finito y no es subnormal
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Calcula la función Bessel
[ldexp, ldexpf, ldexpl](../c-runtime-library/reference/ldexp.md)|Calcula x*2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Calcula el logaritmo natural del valor absoluto de la función gamma
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Redondea un valor de punto flotante al valor **long long** más cercano
[llround, llroundf, llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Redondea un valor de punto flotante al valor **long long** más cercano
[log, logf, logl, log10, log10f, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Calcula el logaritmo natural o en base 10
[log1p, log1pf, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Calcula el logaritmo natural de 1+x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Calcula el logaritmo en base 2
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Devuelve el exponente de un valor de punto flotante
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Redondea un valor de punto flotante al valor **long** más cercano
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Gira un valor entero a la izquierda o derecha
[lround, lroundf, lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Redondea un valor de punto flotante al valor **long** más cercano
[_matherr](../c-runtime-library/reference/matherr.md)|Controlador de errores matemáticos predeterminado
[__max](../c-runtime-library/reference/max.md)|Macro que devuelve el mayor de dos valores
[__min](../c-runtime-library/reference/min.md)|Macro que devuelve el menor de dos valores
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Divide un valor de punto flotante en partes fraccionarias y enteras
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Devuelve un valor NaN reservado
[nearbyint, nearbyintf, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Devuelve el valor redondeado
[nextafter, nextafterf, nextafterl, _nextafter, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Devuelve el siguiente valor de punto flotante que se pueda representar
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Devuelve el siguiente valor de punto flotante que se pueda representar
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Devuelve el valor de *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Calcula el resto del cociente de dos valores de punto flotante
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Calcula el resto de dos valores enteros
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Redondea un valor de punto flotante
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Gira bits en tipos enteros
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Redondea un valor de punto flotante
[_scalb, _scalbf](../c-runtime-library/reference/scalb.md)|Escala el argumento por una potencia de 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Multiplica un número de punto flotante por una potencia integral de **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Establece la palabra de control de punto flotante
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Habilita o deshabilita las instrucciones de SSE2
[signbit](../c-runtime-library/reference/signbit.md)|Prueba el bit de signo de un valor de punto flotante
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Calcula el seno
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Calcula el seno hiperbólico
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Calcula la raíz cuadrada
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Obtiene la palabra de estado de punto flotante
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Convierte una cadena en un **float**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Convierte una cadena en un **Long** **Double** .
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Calcula la tangente
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Calcula la tangente hiperbólica
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Calcula la función gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Trunca la parte fraccionaria
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte una cadena de caracteres anchos en un **double**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Calcula la función Bessel

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Tipos primitivos de punto flotante](../c-runtime-library/reference/floating-point-primitives.md)<br/>
