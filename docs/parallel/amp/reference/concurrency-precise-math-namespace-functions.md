---
title: Funciones del espacio de nombres precise_math | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 73273a58f73860c77810a6ab59def560962f9539
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace-functions"></a>Funciones del espacio de nombres precise_math
||||  
|-|-|-|  
|[ACOS (función)](#acos)|[acosf (función)](#acosf)|[ACOSH (función)](#acosh)|  
|[acoshf (función)](#acoshf)|[ASIN (función)](#asin)|[asinf (función)](#asinf)|  
|[Asinh (función)](#asinh)|[asinhf (función)](#asinhf)|[ATAN (función)](#atan)|  
|[ATAN2 (función)](#atan2)|[atan2f (función)](#atan2f)|[atanf (función)](#atanf)|  
|[ATANH (función)](#atanh)|[atanhf (función)](#atanhf)|[cbrt (función)](#cbrt)|  
|[cbrtf (función)](#cbrtf)|[ceil (función)](#ceil)|[ceilf (función)](#ceilf)|  
|[copysign (función)](#copysign)|[copysignf (función)](#copysignf)|[COS (función)](#cos)|  
|[cosf (función)](#cosf)|[COSH (función)](#cosh)|[coshf (función)](#coshf)|  
|[cospi (función)](#cospi)|[cospif (función)](#cospif)|[ERF (función)](#erf)|  
|[ERFC (función)](#erfc)|[erfcf (función)](#erfcf)|[erfcinv (función)](#erfcinv)|  
|[erfcinvf (función)](#erfcinvf)|[erff (función)](#erff)|[erfinv (función)](#erfinv)|  
|[erfinvf (función)](#erfinvf)|[EXP (función)](#exp)|[EXP10 (función)](#exp10)|  
|[exp10f (función)](#exp10f)|[Exp2 (función)](#exp2)|[exp2f (función)](#exp2f)|  
|[expf (función)](#expf)|[expm1 (función)](#expm1)|[expm1f (función)](#expm1f)|  
|[fabs (función)](#fabs)|[fabsf (función)](#fabsf)|[Floor (función)](#floor)| 
|[fdim (función)](#fdim)|[fdimf (función)](#fdimf)|| 
|[floorf (función)](#floorf)|[FMA (función)](#fma)|[fmaf (función)](#fmaf)|
[Fmax (función)](#fmax)|[fmaxf (función)](#fmaxf)|| 
|[Fmin (función)](#fmin)|[fminf (función)](#fminf)|[fmod (Función)](#fmod)|  
|[fmodf (función)](#fmodf)|[fpclassify (función)](#fpclassify)|[frexp (función)](#frexp)|  
|[frexpf (función)](#frexpf)|[hypot (función)](#hypot)|[hypotf (función)](#hypotf)|  
|[ilogb (función)](#ilogb)|[ilogbf (función)](#ilogbf)|[isFinite (función)](#isfinite)|  
|[isinf (función)](#isinf)|[isNaN (función)](#isnan)|[isnormal (función)](#isnormal)|  
|[ldexp (función)](#ldexp)|[ldexpf (función)](#ldexpf)|[lgamma (función)](#lgamma)|  
|[lgammaf (función)](#lgammaf)|[log (función)](#log)|[LOG10 (función)](#log10)|  
|[log10f (función)](#log10f)|[log1p (función)](#log1p)|[log1pf (función)](#log1pf)|  
|[LOG2 (función)](#log2)|[log2f (función)](#log2f)|[logb (función)](#logb)|  
|[logbf (función)](#logbf)|[logf (función)](#logf)|[modf (función)](#modf)|  
|[modff (función)](#modff)|[NaN (función)](#nan)|[nanf (función)](#nanf)|  
|[nearbyint (función)](#nearbyint)|[nearbyintf (función)](#nearbyintf)|[nextafter (función)](#nextafter)|  
|[nextafterf (función)](#nextafterf)|[PHI (función)](#phi)|[phif (función)](#phif)|  
|[Pow (función)](#pow)|[powf (función)](#powf)|[probit (función)](#probit)|  
|[probitf (función)](#probitf)|[rcbrt (función)](#rcbrt)|[rcbrtf (función)](#rcbrtf)|  
|[Remainder (función)](#remainder)|[remainderf (función)](#remainderf)|[remquo (función)](#remquo)|  
|[remquof (función)](#remquof)|[Round (función)](#round)|[roundf (función)](#roundf)|  
|[rsqrt (función)](#rsqrt)|[rsqrtf (función)](#rsqrtf)|[scalb (función)](#scalb)|  
|[scalbf (función)](#scalbf)|[scalbn (función)](#scalbn)|[scalbnf (función)](#scalbnf)|  
|[signbit (función)](#signbit)|[signbitf (función)](#signbitf)|[sin (función)](#sin)|  
|[sincos (función)](#sincos)|[sincosf (función)](#sincosf)|[sinf (función)](#sinf)|  
|[SINH (función)](#sinh)|[sinhf (función)](#sinhf)|[sinpi (función)](#sinpi)|  
|[sinpif (función)](#sinpif)|[SQRT (función)](#sqrt)|[sqrtf (función)](#sqrtf)|  
|[tan (función)](#tan)|[tanf (función)](#tanf)|[TANH (función)](#tanh)|  
|[tanhf (función)](#tanhf)|[tanpi (función)](#tanpi)|[tanpif (función)](#tanpif)|  
|[tgamma (función)](#tgamma)|[tgammaf (función)](#tgammaf)|[TRUNC (función)](#trunc)|  
|[truncf (función)](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>ACOS (función)  
 Calcula el arco coseno del argumento  
  
```  
inline float acos(float _X) restrict(amp);

 
inline double acos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcocoseno de argumento  
  
##  <a name="a-nameacosfa--acosf-function"></a><a name="acosf"></a>acosf (función)  
 Calcula el arco coseno del argumento  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcocoseno de argumento  
  
##  <a name="a-nameacosha--acosh-function"></a><a name="acosh"></a>ACOSH (función)  
 Calcula el coseno hiperbólico inverso del argumento  
  
```  
inline float acosh(float _X) restrict(amp);

 
inline double acosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico inverso del argumento  
  
##  <a name="a-nameacoshfa--acoshf-function"></a><a name="acoshf"></a>acoshf (función)  
 Calcula el coseno hiperbólico inverso del argumento  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico inverso del argumento  
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>ASIN (función)  
 Calcula el arco seno del argumento  
  
```  
inline float asin(float _X) restrict(amp);

 
inline double asin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcoseno del argumento  
  
##  <a name="a-nameasinfa--asinf-function"></a><a name="asinf"></a>asinf (función)  
 Calcula el arco seno del argumento  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcoseno del argumento  
  
##  <a name="a-nameasinha--asinh-function"></a><a name="asinh"></a>Asinh (función)  
 Calcula el seno hiperbólico inverso del argumento  
  
```  
inline float asinh(float _X) restrict(amp);

 
inline double asinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico inverso del argumento  
  
##  <a name="a-nameasinhfa--asinhf-function"></a><a name="asinhf"></a>asinhf (función)  
 Calcula el seno hiperbólico inverso del argumento  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico inverso del argumento  
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>ATAN (función)  
 Calcula el arco tangente del argumento  
  
```  
inline float atan(float _X) restrict(amp);

 
inline double atan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcotangente del argumento  
  
##  <a name="a-nameatan2a--atan2-function"></a><a name="atan2"></a>ATAN2 (función)  
 Calcula el arco tangente de _Y/_X  
  
```  
inline float atan2(
    float _Y,  
    float _X) restrict(amp);

 
inline double atan2(
    double _Y,  
    double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Y`  
 Valor de punto flotante  
  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcotangente de _Y/_X  
  
##  <a name="a-nameatan2fa--atan2f-function"></a><a name="atan2f"></a>atan2f (función)  
 Calcula el arco tangente de _Y/_X  
  
```  
inline float atan2f(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Y`  
 Valor de punto flotante  
  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcotangente de _Y/_X  
  
##  <a name="a-nameatanfa--atanf-function"></a><a name="atanf"></a>atanf (función)  
 Calcula el arco tangente del argumento  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcotangente del argumento  
  
##  <a name="a-nameatanha--atanh-function"></a><a name="atanh"></a>ATANH (función)  
 Calcula la tangente hiperbólica inversa del argumento  
  
```  
inline float atanh(float _X) restrict(amp);

 
inline double atanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico inverso del argumento  
  
##  <a name="a-nameatanhfa--atanhf-function"></a><a name="atanhf"></a>atanhf (función)  
 Calcula la tangente hiperbólica inversa del argumento  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico inverso del argumento  
  
##  <a name="a-namecbrta--cbrt-function"></a><a name="cbrt"></a>cbrt (función)  
 Calcula la raíz cúbica real del argumento  
  
```  
inline float cbrt(float _X) restrict(amp);

 
inline double cbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz cúbica real del argumento  
  
##  <a name="a-namecbrtfa--cbrtf-function"></a><a name="cbrtf"></a>cbrtf (función)  
 Calcula la raíz cúbica real del argumento  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz cúbica real del argumento  
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil (función)  
 Calcula el límite superior del argumento  
  
```  
inline float ceil(float _X) restrict(amp);

 
inline double ceil(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior del argumento  
  
##  <a name="a-nameceilfa--ceilf-function"></a><a name="ceilf"></a>ceilf (función)  
 Calcula el límite superior del argumento  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior del argumento  
  
##  <a name="a-namecopysigna--copysign-function"></a><a name="copysign"></a>copysign (función)  
 Genera un valor con la magnitud de _X y el signo de _Y  
  
```  
inline float copysign(
    float _X,  
    float _Y) restrict(amp);

 
inline double copysign(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor con la magnitud de _X y el signo de _Y  
  
##  <a name="a-namecopysignfa--copysignf-function"></a><a name="copysignf"></a>copysignf (función)  
 Genera un valor con la magnitud de _X y el signo de _Y  
  
```  
inline float copysignf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor con la magnitud de _X y el signo de _Y  
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>COS (función)  
 Calcula el coseno del argumento  
  
```  
inline float cos(float _X) restrict(amp);

 
inline double cos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno del argumento  
  
##  <a name="a-namecosfa--cosf-function"></a><a name="cosf"></a>cosf (función)  
 Calcula el coseno del argumento  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno del argumento  
  
##  <a name="a-namecosha--cosh-function"></a><a name="cosh"></a>COSH (función)  
 Calcula el valor de coseno hiperbólico del argumento  
  
```  
inline float cosh(float _X) restrict(amp);

 
inline double cosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico del argumento  
  
##  <a name="a-namecoshfa--coshf-function"></a><a name="coshf"></a>coshf (función)  
 Calcula el valor de coseno hiperbólico del argumento  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico del argumento  
  
##  <a name="a-namecospia--cospi-function"></a><a name="cospi"></a>cospi (función)  
 Calcula el valor de coseno de pi * _X  
  
```  
inline float cospi(float _X) restrict(amp);

 
inline double cospi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno de pi * _X  
  
##  <a name="a-namecospifa--cospif-function"></a><a name="cospif"></a>cospif (función)  
 Calcula el valor de coseno de pi * _X  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno de pi * _X  
  
##  <a name="a-nameerfa--erf-function"></a><a name="erf"></a>ERF (función)  
 Calcula la función error de _X  
  
```  
inline float erf(float _X) restrict(amp);

 
inline double erf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error de _X  
  
##  <a name="a-nameerfca--erfc-function"></a><a name="erfc"></a>ERFC (función)  
 Calcula la función de error complementaria de _X  
  
```  
inline float erfc(float _X) restrict(amp);

 
inline double erfc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria de _X  
  
##  <a name="a-nameerfcfa--erfcf-function"></a><a name="erfcf"></a>erfcf (función)  
 Calcula la función de error complementaria de _X  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria de _X  
  
##  <a name="a-nameerfcinva--erfcinv-function"></a><a name="erfcinv"></a>erfcinv (función)  
 Calcula la función de error complementaria inverso de _X  
  
```  
inline float erfcinv(float _X) restrict(amp);

 
inline double erfcinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria inverso de _X  
  
##  <a name="a-nameerfcinvfa--erfcinvf-function"></a><a name="erfcinvf"></a>erfcinvf (función)  
 Calcula la función de error complementaria inverso de _X  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria inverso de _X  
  
##  <a name="a-nameerffa--erff-function"></a><a name="erff"></a>erff (función)  
 Calcula la función error de _X  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error de _X  
  
##  <a name="a-nameerfinva--erfinv-function"></a><a name="erfinv"></a>erfinv (función)  
 Calcula la función error inverso de _X  
  
```  
inline float erfinv(float _X) restrict(amp);

 
inline double erfinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función inversa de error de _X  
  
##  <a name="a-nameerfinvfa--erfinvf-function"></a><a name="erfinvf"></a>erfinvf (función)  
 Calcula la función error inverso de _X  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función inversa de error de _X  
  
##  <a name="a-nameexp10a--exp10-function"></a><a name="exp10"></a>EXP10 (función)  
 Calcula el valor exponencial del argumento de base&10;  
  
```  
inline float exp10(float _X) restrict(amp);

 
inline double exp10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&10;  
  
##  <a name="a-nameexp10fa--exp10f-function"></a><a name="exp10f"></a>exp10f (función)  
 Calcula el valor exponencial del argumento de base&10;  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&10;  
  
##  <a name="a-nameexpm1a--expm1-function"></a><a name="expm1"></a>expm1 (función)  
 Calcula la base e exponencial del argumento, menos 1  
  
```  
inline float expm1(float exponent) restrict(amp);

 
inline double expm1(double exponent) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `exponent`  
 El término exponencial *n* de la expresión matemática `e` <sup>n</sup>, donde `e` es la base del logaritmo natural.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento, menos 1  
  
##  <a name="a-nameexpm1fa--expm1f-function"></a><a name="expm1f"></a>expm1f (función)  
 Calcula la base e exponencial del argumento, menos 1  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `exponent`  
 El término exponencial *n* de la expresión matemática `e` <sup>n</sup>, donde `e` es la base del logaritmo natural.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento, menos 1  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>EXP (función)  
 Calcula la base e exponencial del argumento  
  
```  
inline float exp(float _X) restrict(amp);

 
inline double exp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento  
  
##  <a name="a-nameexpfa--expf-function"></a><a name="expf"></a>expf (función)  
 Calcula la base e exponencial del argumento  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento  
  
##  <a name="a-nameexp2a--exp2-function"></a><a name="exp2"></a>Exp2 (función)  
 Calcula el valor exponencial del argumento de base&2;  
  
```  
inline float exp2(float _X) restrict(amp);

 
inline double exp2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&2;  
  
##  <a name="a-nameexp2fa--exp2f-function"></a><a name="exp2f"></a>exp2f (función)  
 Calcula el valor exponencial del argumento de base&2;  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&2;  
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs (función)  
 Devuelve el valor absoluto del argumento  
  
```  
inline float fabs(float _X) restrict(amp);

 
inline double fabs(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor absoluto del argumento  
  
##  <a name="a-namefabsfa--fabsf-function"></a><a name="fabsf"></a>fabsf (función)  
 Devuelve el valor absoluto del argumento  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor absoluto del argumento  

## <a name="a-namefdima-fdim-function"></a><a name="fdim"></a>fdim (función)  
Calcula la diferencia positiva entre los argumentos.
```  
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
``` 
### <a name="parameters"></a>Parámetros
`_X`Valor de punto flotante `_Y` valor de punto flotante


### <a name="return-value"></a>Valor devuelto
La diferencia entre _X y _Y si _X es mayor que _Y; en caso contrario, +&0;.
 
## <a name="a-namefdimfa-fdimf-function"></a><a name="fdimf"></a>fdimf (función)
Calcula la diferencia positiva entre los argumentos.
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>Parámetros
`_X`Valor de punto flotante `_Y` valor de punto flotante

### <a name="return-value"></a>Valor devuelto
La diferencia entre _X y _Y si _X es mayor que _Y; en caso contrario, +&0;. 
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>Floor (función)  
 Calcula el límite inferior del argumento  
  
```  
inline float floor(float _X) restrict(amp);

 
inline double floor(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior del argumento  
  
##  <a name="a-namefloorfa--floorf-function"></a><a name="floorf"></a>floorf (función)  
 Calcula el límite inferior del argumento  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior del argumento  

## <a name="a-namefma-fma-function"></a><a name="fma">FMA (función)  
Calcula el producto de los argumentos primeros y segundo especificados, a continuación, agrega el tercer argumento especificado al resultado; se realiza el cálculo completo como una sola operación.
```
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```
### <a name="parameters"></a>Parámetros
`_X`El primer argumento de punto flotante.
`_Y`El segundo argumento de punto flotante.
`_Z`El tercer argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto
El resultado de la expresión (_X * _Y) + _Z. Se realiza el cálculo completo como una sola operación. es decir, las subexpresiones se calcularán con una precisión infinita y se redondea el resultado final. 

## <a name="a-namefmafa-fmaf-function"></a><a name="fmaf"></a>fmaf (función)  
Calcula el producto de los argumentos primeros y segundo especificados, a continuación, agrega el tercer argumento especificado al resultado; se realiza el cálculo completo como una sola operación.
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```  
### <a name="parameters"></a>Parámetros
`_X`El primer argumento de punto flotante.
`_Y`El segundo argumento de punto flotante.
`_Z`El tercer argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto
El resultado de la expresión (_X * _Y) + _Z. Se realiza el cálculo completo como una sola operación. es decir, las subexpresiones se calcularán con una precisión infinita y se redondea el resultado final.
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>Fmax (función)  
 Determinar el valor numérico máximo de los argumentos  
  
```  
inline float fmax(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmax(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico máximo de los argumentos  
  
##  <a name="a-namefmaxfa--fmaxf-function"></a><a name="fmaxf"></a>fmaxf (función)  
 Determinar el valor numérico máximo de los argumentos  
  
```  
inline float fmaxf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico máximo de los argumentos  
  
##  <a name="a-namefmina--fmin-function"></a><a name="fmin"></a>Fmin (función)  
 Determinar el valor numérico mínimo de los argumentos  
  
```  
inline float fmin(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmin(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico mínimo de los argumentos  
  
##  <a name="a-namefminfa--fminf-function"></a><a name="fminf"></a>fminf (función)  
 Determinar el valor numérico mínimo de los argumentos  
  
```  
inline float fminf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico mínimo de los argumentos  
  
##  <a name="a-namefmoda--fmod-function-c-amp"></a><a name="fmod"></a>fmod (función) (C++ AMP)  
 Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado.  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmod(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 El primer argumento de punto flotante.  
  
 `_Y`  
 El segundo argumento de punto flotante.  
  
### <a name="return-value"></a>Valor devuelto  
 El resto de `_X` dividido por `_Y`; es decir, el valor de `_X`  -  `_Y` *n*, donde *n* es un número entero que la magnitud de `_X`  -  `_Y` *n* es menor que la magnitud de `_Y`.  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf (función)  
 Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 El primer argumento de punto flotante.  
  
 `_Y`  
 El segundo argumento de punto flotante.  
  
### <a name="return-value"></a>Valor devuelto  
 El resto de `_X` dividido por `_Y`; es decir, el valor de `_X`  -  `_Y` *n*, donde *n* es un número entero que la magnitud de `_X`  -  `_Y` *n* es menor que la magnitud de `_Y`.  
  
##  <a name="a-namefpclassifya--fpclassify-function"></a><a name="fpclassify"></a>fpclassify (función)  
 Clasifica el valor del argumento como cero normal infinito, NaN, subnormal,  
  
```  
inline int fpclassify(float _X) restrict(amp);

 
inline int fpclassify(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la macro de clasificación número correspondiente al valor del argumento.  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp (función)  
 Obtiene la mantisa y el exponente de _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);

 
inline double frexp(
    double _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Exp`  
 Devuelve al exponente de entero de _X en el valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el _X mantisa  
  
##  <a name="a-namefrexpfa--frexpf-function"></a><a name="frexpf"></a>frexpf (función)  
 Obtiene la mantisa y el exponente de _X  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Exp`  
 Devuelve al exponente de entero de _X en el valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el _X mantisa  
  
##  <a name="a-namehypota--hypot-function"></a><a name="hypot"></a>hypot (función)  
 Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y  
  
```  
inline float hypot(
    float _X,  
    float _Y) restrict(amp);

 
inline double hypot(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz cuadrada de la suma de los cuadrados de _X y _Y  
  
##  <a name="a-namehypotfa--hypotf-function"></a><a name="hypotf"></a>hypotf (función)  
 Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y  
  
```  
inline float hypotf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz cuadrada de la suma de los cuadrados de _X y _Y  
  
##  <a name="a-nameilogba--ilogb-function"></a><a name="ilogb"></a>ilogb (función)  
 Extraiga al exponente de _X como un valor int con signo  
  
```  
inline int ilogb(float _X) restrict(amp);

 
inline int ilogb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X como un valor int con signo  
  
##  <a name="a-nameilogbfa--ilogbf-function"></a><a name="ilogbf"></a>ilogbf (función)  
 Extraiga al exponente de _X como un valor int con signo  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X como un valor int con signo  
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isFinite (función)  
 Determina si el argumento tiene un valor finito  
  
```  
inline int isfinite(float _X) restrict(amp);

 
inline int isfinite(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el argumento tiene un valor finito  
  
##  <a name="a-nameisinfa--isinf-function"></a><a name="isinf"></a>isinf (función)  
 Determina si el argumento es un infinito  
  
```  
inline int isinf(float _X) restrict(amp);

 
inline int isinf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el argumento tiene un valor infinito  
  
##  <a name="a-nameisnana--isnan-function"></a><a name="isnan"></a>isNaN (función)  
 Determina si el argumento es un NaN  
  
```  
inline int isnan(float _X) restrict(amp);

 
inline int isnan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el argumento tiene un valor NaN  
  
##  <a name="a-nameisnormala--isnormal-function"></a><a name="isnormal"></a>isnormal (función)  
 Determina si el argumento es normal  
  
```  
inline int isnormal(float _X) restrict(amp);

 
inline int isnormal(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el argumento tiene un valor normal  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp (función)  
 Calcula un número real de la mantisa especificado y el exponente.  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);

 
inline double ldexp(
    double _X,  
    double _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante, mantisa  
  
 `_Exp`  
 Valor entero, exponente  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * 2 ^ _Exp  
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf (función)  
 Calcula un número real de la mantisa especificado y el exponente.  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante, mantisa  
  
 `_Exp`  
 Valor entero, exponente  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * 2 ^ _Exp  
  
##  <a name="a-namelgammaa--lgamma-function"></a><a name="lgamma"></a>lgamma (función)  
 Calcula el logaritmo natural del valor absoluto de gamma del argumento  
  
```  
inline float lgamma(
    float _X,  
    _Out_ int* _Sign) restrict(amp);

 
inline double lgamma(
    double _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Sign`  
 Devuelve el signo  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo natural del valor absoluto de gamma del argumento  
  
##  <a name="a-namelgammafa--lgammaf-function"></a><a name="lgammaf"></a>lgammaf (función)  
 Calcula el logaritmo natural del valor absoluto de gamma del argumento  
  
```  
inline float lgammaf(
    float _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Sign`  
 Devuelve el signo  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo natural del valor absoluto de gamma del argumento  
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log (función)  
 Calcula el logaritmo en base e de argumento  
  
```  
inline float log(float _X) restrict(amp);

 
inline double log(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de argumento  
  
##  <a name="a-namelog10a--log10-function"></a><a name="log10"></a>LOG10 (función)  
 Calcula el logaritmo en base&10; del argumento  
  
```  
inline float log10(float _X) restrict(amp);

 
inline double log10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="a-namelog10fa--log10f-function"></a><a name="log10f"></a>log10f (función)  
 Calcula el logaritmo en base&10; del argumento  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="a-namelog1pa--log1p-function"></a><a name="log1p"></a>log1p (función)  
 Calcula el logaritmo en base e de 1 y el argumento  
  
```  
inline float log1p(float _X) restrict(amp);

 
inline double log1p(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de 1 y el argumento  
  
##  <a name="a-namelog1pfa--log1pf-function"></a><a name="log1pf"></a>log1pf (función)  
 Calcula el logaritmo en base e de 1 y el argumento  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de 1 y el argumento  
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>LOG2 (función)  
 Calcula el logaritmo en base&2; del argumento  
  
```  
inline float log2(float _X) restrict(amp);

 
inline double log2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="a-namelog2fa--log2f-function"></a><a name="log2f"></a>log2f (función)  
 Calcula el logaritmo en base&2; del argumento  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="a-namelogba--logb-function"></a><a name="logb"></a>logb (función)  
 Extrae al exponente de _X, como un valor entero con signo en formato de punto flotante  
  
```  
inline float logb(float _X) restrict(amp);

 
inline double logb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X firmado  
  
##  <a name="a-namelogbfa--logbf-function"></a><a name="logbf"></a>logbf (función)  
 Extrae al exponente de _X, como un valor entero con signo en formato de punto flotante  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X firmado  
  
##  <a name="a-namelogfa--logf-function"></a><a name="logf"></a>logf (función)  
 Calcula el logaritmo en base e de argumento  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de argumento  
  
##  <a name="a-namemodfa--modf-function"></a><a name="modf"></a>modf (función)  
 Divide el argumento especificado en fracciones y partes enteras.  
  
```  
inline float modf(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);

 
inline double modf(
    double _X,  
    _Out_ double* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Iptr`(parámetro de salida)  
 La parte entera de `_X`, como un valor de punto flotante.  
  
### <a name="return-value"></a>Valor devuelto  
 La parte fraccionaria firmada de `_X`.  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff (función)  
 Divide el argumento especificado en fracciones y partes enteras.  
  
```  
inline float modff(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Iptr`  
 La parte entera de `_X`, como un valor de punto flotante.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la parte fraccionaria firmada de `_X`.  
  
##  <a name="a-namenana--nan-function"></a><a name="nan"></a>NaN (función)  
 Devuelve un valor NaN quiet  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor NaN reservado, si está disponible, con el contenido indicado en _X  
  
##  <a name="a-namenanfa--nanf-function"></a><a name="nanf"></a>nanf (función)  
 Devuelve un valor NaN quiet  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor NaN reservado, si está disponible, con el contenido indicado en _X  
  
##  <a name="a-namenearbyinta--nearbyint-function"></a><a name="nearbyint"></a>nearbyint (función)  
 Redondea el argumento en un valor entero en formato de punto flotante, utilizando la dirección de redondeo actual.  
  
```  
inline float nearbyint(float _X) restrict(amp);

 
inline double nearbyint(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor entero redondeado.  
  
##  <a name="a-namenearbyintfa--nearbyintf-function"></a><a name="nearbyintf"></a>nearbyintf (función)  
 Redondea el argumento en un valor entero en formato de punto flotante, utilizando la dirección de redondeo actual.  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor entero redondeado.  
  
##  <a name="a-namenextaftera--nextafter-function"></a><a name="nextafter"></a>nextafter (función)  
 Determinar el siguiente valor representable, en el tipo de la función, tras _X en la dirección de _Y  
  
```  
inline float nextafter(
    float _X,  
    float _Y) restrict(amp);

 
inline double nextafter(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el siguiente valor representable, en el tipo de la función después _X en la dirección de _Y  
  
##  <a name="a-namenextafterfa--nextafterf-function"></a><a name="nextafterf"></a>nextafterf (función)  
 Determinar el siguiente valor representable, en el tipo de la función, tras _X en la dirección de _Y  
  
```  
inline float nextafterf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el siguiente valor representable, en el tipo de la función después _X en la dirección de _Y  
  
##  <a name="a-namephia--phi-function"></a><a name="phi"></a>PHI (función)  
 Devuelve la función de distribución acumulativa del argumento  
  
```  
inline float phi(float _X) restrict(amp);

 
inline double phi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa del argumento  
  
##  <a name="a-namephifa--phif-function"></a><a name="phif"></a>phif (función)  
 Devuelve la función de distribución acumulativa del argumento  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa del argumento  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>Pow (función)  
 Calcula _X elevado a la potencia de _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);

 
inline double pow(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante de base  
  
 `_Y`  
 Valor de punto flotante de exponente  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-namepowfa--powf-function"></a><a name="powf"></a>powf (función)  
 Calcula _X elevado a la potencia de _Y  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante de base  
  
 `_Y`  
 Valor de punto flotante de exponente  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameprobita--probit-function"></a><a name="probit"></a>probit (función)  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
```  
inline float probit(float _X) restrict(amp);

 
inline double probit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
##  <a name="a-nameprobitfa--probitf-function"></a><a name="probitf"></a>probitf (función)  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
##  <a name="a-namercbrta--rcbrt-function"></a><a name="rcbrt"></a>rcbrt (función)  
 Devuelve el inverso de la raíz cúbica del argumento  
  
```  
inline float rcbrt(float _X) restrict(amp);

 
inline double rcbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cúbica del argumento  
  
##  <a name="a-namercbrtfa--rcbrtf-function"></a><a name="rcbrtf"></a>rcbrtf (función)  
 Devuelve el inverso de la raíz cúbica del argumento  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cúbica del argumento  
  
##  <a name="a-nameremaindera--remainder-function"></a><a name="remainder"></a>Remainder (función)  
 Calcula el resto: _X REM _Y  
  
```  
inline float remainder(
    float _X,  
    float _Y) restrict(amp);

 
inline double remainder(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X REM _Y  
  
##  <a name="a-nameremainderfa--remainderf-function"></a><a name="remainderf"></a>remainderf (función)  
 Calcula el resto: _X REM _Y  
  
```  
inline float remainderf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X REM _Y  
  
##  <a name="a-nameremquoa--remquo-function"></a><a name="remquo"></a>remquo (función)  
 Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado. También calcula el cociente de la mantisa del primer argumento especificado dividido por la mantisa del segundo argumento especificado y devuelve el cociente utilizando la ubicación especificada en el tercer argumento.  
  
```  
inline float remquo(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);

 
inline double remquo(
    double _X,  
    double _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 El primer argumento de punto flotante.  
  
 `_Y`  
 El segundo argumento de punto flotante.  
  
 `_Quo`(parámetro de salida)  
 La dirección de un entero que se utiliza para devolver el cociente de los bits de fracciones de `_X` dividido por los bits de fracciones de `_Y`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resto de `_X` dividida entre `_Y`.  
  
##  <a name="a-nameremquofa--remquof-function"></a><a name="remquof"></a>remquof (función)  
 Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado. También calcula el cociente de la mantisa del primer argumento especificado dividido por la mantisa del segundo argumento especificado y devuelve el cociente utilizando la ubicación especificada en el tercer argumento.  
  
```  
inline float remquof(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 El primer argumento de punto flotante.  
  
 `_Y`  
 El segundo argumento de punto flotante.  
  
 `_Quo`(parámetro de salida)  
 La dirección de un entero que se utiliza para devolver el cociente de los bits de fracciones de `_X` dividido por los bits de fracciones de `_Y`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resto de `_X` dividida entre `_Y`.  
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>Round (función)  
 Redondea _X al entero más próximo  
  
```  
inline float round(float _X) restrict(amp);

 
inline double round(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el entero más cercano de _X  
  
##  <a name="a-nameroundfa--roundf-function"></a><a name="roundf"></a>roundf (función)  
 Redondea _X al entero más próximo  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el entero más cercano de _X  
  
##  <a name="a-namersqrta--rsqrt-function"></a><a name="rsqrt"></a>rsqrt (función)  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
```  
inline float rsqrt(float _X) restrict(amp);

 
inline double rsqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
##  <a name="a-namersqrtfa--rsqrtf-function"></a><a name="rsqrtf"></a>rsqrtf (función)  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
##  <a name="a-namescalba--scalb-function"></a><a name="scalb"></a>scalb (función)  
 Multiplica _X por FLT_RADIX en el _Y de energía  
  
```  
inline float scalb(
    float _X,  
    float _Y) restrict(amp);

 
inline double scalb(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbfa--scalbf-function"></a><a name="scalbf"></a>scalbf (función)  
 Multiplica _X por FLT_RADIX en el _Y de energía  
  
```  
inline float scalbf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbna--scalbn-function"></a><a name="scalbn"></a>scalbn (función)  
 Multiplica _X por FLT_RADIX en el _Y de energía  
  
```  
inline float scalbn(
    float _X,  
    int _Y) restrict(amp);

 
inline double scalbn(
    double _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbnfa--scalbnf-function"></a><a name="scalbnf"></a>scalbnf (función)  
 Multiplica _X por FLT_RADIX en el _Y de energía  
  
```  
inline float scalbnf(
    float _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit (función)  
 Determina si el inicio de sesión de _X es negativo  
  
```  
inline int signbit(float _X) restrict(amp);

 
inline int signbit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el inicio de sesión de _X es negativo  
  
##  <a name="a-namesignbitfa--signbitf-function"></a><a name="signbitf"></a>signbitf (función)  
 Determina si el inicio de sesión de _X es negativo  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el inicio de sesión de _X es negativo  
  
##  <a name="a-namesina--sin-function"></a><a name="sin"></a>sin (función)  
 Calcula el valor del seno del argumento  
  
```  
inline float sin(float _X) restrict(amp);

 
inline double sin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno del argumento  
  
##  <a name="a-namesinfa--sinf-function"></a><a name="sinf"></a>sinf (función)  
 Calcula el valor del seno del argumento  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno del argumento  
  
##  <a name="a-namesincosa--sincos-function"></a><a name="sincos"></a>sincos (función)  
 Calcula el seno y coseno el valor de _X  
  
```  
inline void sincos(
    float _X,  
    _Out_ float* _S,  
    _Out_ float* _C) restrict(amp);

 
inline void sincos(
    double _X,  
    _Out_ double* _S,  
    _Out_ double* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_S`  
 Devuelve el valor del seno _X  
  
 `_C`  
 Devuelve el valor de coseno de _X  
  
##  <a name="a-namesincosfa--sincosf-function"></a><a name="sincosf"></a>sincosf (función)  
 Calcula el seno y coseno el valor de _X  
  
```  
inline void sincosf(
    float _X,  
    _Out_ float* _S,  
    _Out_ float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_S`  
 Devuelve el valor del seno _X  
  
 `_C`  
 Devuelve el valor de coseno de _X  
  
##  <a name="a-namesinha--sinh-function"></a><a name="sinh"></a>SINH (función)  
 Calcula el valor del seno hiperbólico del argumento  
  
```  
inline float sinh(float _X) restrict(amp);

 
inline double sinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico del argumento  
  
##  <a name="a-namesinhfa--sinhf-function"></a><a name="sinhf"></a>sinhf (función)  
 Calcula el valor del seno hiperbólico del argumento  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico del argumento  
  
##  <a name="a-namesinpia--sinpi-function"></a><a name="sinpi"></a>sinpi (función)  
 Calcula el valor del seno de pi * _X  
  
```  
inline float sinpi(float _X) restrict(amp);

 
inline double sinpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno de pi * _X  
  
##  <a name="a-namesinpifa--sinpif-function"></a><a name="sinpif"></a>sinpif (función)  
 Calcula el valor del seno de pi * _X  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno de pi * _X  
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>SQRT (función)  
 Calcula la raíz de squre del argumento  
  
```  
inline float sqrt(float _X) restrict(amp);

 
inline double sqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz de squre del argumento  
  
##  <a name="a-namesqrtfa--sqrtf-function"></a><a name="sqrtf"></a>sqrtf (función)  
 Calcula la raíz de squre del argumento  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz de squre del argumento  
  
##  <a name="a-nametana--tan-function"></a><a name="tan"></a>tan (función)  
 Calcula el valor del argumento de tangente  
  
```  
inline float tan(float _X) restrict(amp);

 
inline double tan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del argumento de tangente  
  
##  <a name="a-nametanfa--tanf-function"></a><a name="tanf"></a>tanf (función)  
 Calcula el valor del argumento de tangente  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del argumento de tangente  
  
##  <a name="a-nametanha--tanh-function"></a><a name="tanh"></a>TANH (función)  
 Calcula el valor de la tangente hiperbólico del argumento  
  
```  
inline float tanh(float _X) restrict(amp);

 
inline double tanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico del argumento  
  
##  <a name="a-nametanhfa--tanhf-function"></a><a name="tanhf"></a>tanhf (función)  
 Calcula el valor de la tangente hiperbólico del argumento  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico del argumento  
  
##  <a name="a-nametanpia--tanpi-function"></a><a name="tanpi"></a>tanpi (función)  
 Calcula el valor de tangente de pi * _X  
  
```  
inline float tanpi(float _X) restrict(amp);

 
inline double tanpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de tangente de pi * _X  
  
##  <a name="a-nametanpifa--tanpif-function"></a><a name="tanpif"></a>tanpif (función)  
 Calcula el valor de tangente de pi * _X  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de tangente de pi * _X  
  
##  <a name="a-nametgammaa--tgamma-function"></a><a name="tgamma"></a>tgamma (función)  
 Calcula la función gamma de _X  
  
```  
inline float tgamma(float _X) restrict(amp);

 
inline double tgamma(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de la función gamma de _X  
  
##  <a name="a-nametgammafa--tgammaf-function"></a><a name="tgammaf"></a>tgammaf (función)  
 Calcula la función gamma de _X  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de la función gamma de _X  
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>TRUNC (función)  
 Trunca el argumento para el componente de número entero  
  
```  
inline float trunc(float _X) restrict(amp);

 
inline double trunc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el componente de número entero del argumento  
  
##  <a name="a-nametruncfa--truncf-function"></a><a name="truncf"></a>truncf (función)  
 Trunca el argumento para el componente de número entero  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el componente de número entero del argumento  
  
## <a name="see-also"></a>Vea también  
 [Namespace precise_math](concurrency-precise-math-namespace.md)

