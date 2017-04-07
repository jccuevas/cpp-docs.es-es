---
title: Funciones del espacio de nombres precise_math | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
dev_langs:
- C++
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 727bbabf3c3b016e7c2666e3f77cf15b7e36d2a8
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencyprecisemath-namespace-functions"></a>Funciones del espacio de nombres precise_math
||||  
|-|-|-|  
|[acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|  
|[acoshf](#acoshf)|[asin](#asin)|[asinf](#asinf)|  
|[asinh](#asinh)|[asinhf](#asinhf)|[atan](#atan)|  
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|  
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|  
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|  
|[copysign](#copysign)|[copysignf](#copysignf)|[cos](#cos)|  
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|  
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|  
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|  
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|  
|[erfinvf](#erfinvf)|[exp](#exp)|[EXP10](#exp10)|  
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|  
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|  
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)| 
|[fdim](#fdim)|[fdimf](#fdimf)|| 
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)|| 
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|  
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|  
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|  
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isFinite](#isfinite)|  
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|  
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|  
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|  
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|  
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|  
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|  
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|  
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|  
|[nextafterf](#nextafterf)|[PHI](#phi)|[phif)](#phif)|  
|[pow](#pow)|[powf](#powf)|[probit](#probit)|  
|[probitf)](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|  
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|  
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|  
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|  
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|  
|[signbit](#signbit)|[signbitf](#signbitf)|[sin](#sin)|  
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|  
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|  
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|  
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|  
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|  
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|  
|[truncf](#truncf)|  
  
##  <a name="acos"></a>  acos  
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
  
##  <a name="acosf"></a>acosf  
 Calcula el arco coseno del argumento  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcocoseno de argumento  
  
##  <a name="acosh"></a>ACOSH  
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
  
##  <a name="acoshf"></a>acoshf  
 Calcula el coseno hiperbólico inverso del argumento  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico inverso del argumento  
  
##  <a name="asin"></a>  asin  
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
  
##  <a name="asinf"></a>asinf  
 Calcula el arco seno del argumento  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcoseno del argumento  
  
##  <a name="asinh"></a>Asinh)  
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
  
##  <a name="asinhf"></a>asinhf  
 Calcula el seno hiperbólico inverso del argumento  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico inverso del argumento  
  
##  <a name="atan"></a>  atan  
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
  
##  <a name="atan2"></a>  atan2  
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
  
##  <a name="atan2f"></a>atan2f  
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
  
##  <a name="atanf"></a>atanf  
 Calcula el arco tangente del argumento  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del arcotangente del argumento  
  
##  <a name="atanh"></a>ATANH  
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
  
##  <a name="atanhf"></a>atanhf  
 Calcula la tangente hiperbólica inversa del argumento  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico inverso del argumento  
  
##  <a name="cbrt"></a>cbrt  
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
  
##  <a name="cbrtf"></a>cbrtf  
 Calcula la raíz cúbica real del argumento  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz cúbica real del argumento  
  
##  <a name="ceil"></a>ceil)  
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
  
##  <a name="ceilf"></a>ceilf  
 Calcula el límite superior del argumento  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior del argumento  
  
##  <a name="copysign"></a>copysign  
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
  
##  <a name="copysignf"></a>copysignf  
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
  
##  <a name="cos"></a>  cos  
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
  
##  <a name="cosf"></a>cosf  
 Calcula el coseno del argumento  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno del argumento  
  
##  <a name="cosh"></a>  cosh  
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
  
##  <a name="coshf"></a>coshf  
 Calcula el valor de coseno hiperbólico del argumento  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico del argumento  
  
##  <a name="cospi"></a>cospi  
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
  
##  <a name="cospif"></a>cospif  
 Calcula el valor de coseno de pi * _X  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno de pi * _X  
  
##  <a name="erf"></a>ERF  
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
  
##  <a name="erfc"></a>ERFC)  
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
  
##  <a name="erfcf"></a>erfcf  
 Calcula la función de error complementaria de _X  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria de _X  
  
##  <a name="erfcinv"></a>erfcinv  
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
  
##  <a name="erfcinvf"></a>erfcinvf  
 Calcula la función de error complementaria inverso de _X  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error complementaria inverso de _X  
  
##  <a name="erff"></a>erff  
 Calcula la función error de _X  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de error de _X  
  
##  <a name="erfinv"></a>erfinv  
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
  
##  <a name="erfinvf"></a>erfinvf  
 Calcula la función error inverso de _X  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función inversa de error de _X  
  
##  <a name="exp10"></a>EXP10  
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
  
##  <a name="exp10f"></a>exp10f  
 Calcula el valor exponencial del argumento de base&10;  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&10;  
  
##  <a name="expm1"></a>expm1  
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
  
##  <a name="expm1f"></a>expm1f  
 Calcula la base e exponencial del argumento, menos 1  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `exponent`  
 El término exponencial *n* de la expresión matemática `e` <sup>n</sup>, donde `e` es la base del logaritmo natural.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento, menos 1  
  
##  <a name="exp"></a>  exp  
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
  
##  <a name="expf"></a>expf  
 Calcula la base e exponencial del argumento  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la base e exponencial del argumento  
  
##  <a name="exp2"></a>Exp2  
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
  
##  <a name="exp2f"></a>exp2f  
 Calcula el valor exponencial del argumento de base&2;  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor exponencial del argumento de base&2;  
  
##  <a name="fabs"></a>fabs  
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
  
##  <a name="fabsf"></a>fabsf  
 Devuelve el valor absoluto del argumento  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor absoluto del argumento  

## <a name="fdim"></a>fdim  
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
 
## <a name="fdimf"></a>fdimf  
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
  
##  <a name="floor"></a>Floor  
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
  
##  <a name="floorf"></a>floorf  
 Calcula el límite inferior del argumento  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior del argumento  

## <a name="a-namefma-fma"></a><a name="fma">FMA  
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

## <a name="fmaf"></a>fmaf  
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
  
##  <a name="fmax"></a>Fmax  
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
  
##  <a name="fmaxf"></a>fmaxf  
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
  
##  <a name="fmin"></a>Fmin  
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
  
##  <a name="fminf"></a>fminf  
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
  
##  <a name="fmod"></a>fmod (función) (C++ AMP)  
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
  
##  <a name="fmodf"></a>fmodf  
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
  
##  <a name="fpclassify"></a>fpclassify  
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
  
##  <a name="frexp"></a>frexp  
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
  
##  <a name="frexpf"></a>frexpf  
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
  
##  <a name="hypot"></a>hypot  
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
  
##  <a name="hypotf"></a>hypotf  
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
  
##  <a name="ilogb"></a>ilogb  
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
  
##  <a name="ilogbf"></a>ilogbf  
 Extraiga al exponente de _X como un valor int con signo  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X como un valor int con signo  
  
##  <a name="isfinite"></a>isFinite  
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
  
##  <a name="isinf"></a>isinf  
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
  
##  <a name="isnan"></a>isNaN  
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
  
##  <a name="isnormal"></a>isnormal  
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
  
##  <a name="ldexp"></a>ldexp  
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
  
##  <a name="ldexpf"></a>ldexpf  
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
  
##  <a name="lgamma"></a>lgamma  
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
  
##  <a name="lgammaf"></a>lgammaf  
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
  
##  <a name="log"></a>  log  
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
  
##  <a name="log10"></a>  log10  
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
  
##  <a name="log10f"></a>log10f  
 Calcula el logaritmo en base&10; del argumento  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="log1p"></a>log1p  
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
  
##  <a name="log1pf"></a>log1pf  
 Calcula el logaritmo en base e de 1 y el argumento  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de 1 y el argumento  
  
##  <a name="log2"></a>LOG2  
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
  
##  <a name="log2f"></a>log2f  
 Calcula el logaritmo en base&2; del argumento  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&10; del argumento  
  
##  <a name="logb"></a>logb  
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
  
##  <a name="logbf"></a>logbf  
 Extrae al exponente de _X, como un valor entero con signo en formato de punto flotante  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve al exponente de _X firmado  
  
##  <a name="logf"></a>logf  
 Calcula el logaritmo en base e de argumento  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base e de argumento  
  
##  <a name="modf"></a>modf  
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
  
##  <a name="modff"></a>modff  
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
  
##  <a name="nan"></a>NaN  
 Devuelve un valor NaN quiet  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor NaN reservado, si está disponible, con el contenido indicado en _X  
  
##  <a name="nanf"></a>nanf  
 Devuelve un valor NaN quiet  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor NaN reservado, si está disponible, con el contenido indicado en _X  
  
##  <a name="nearbyint"></a>nearbyint  
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
  
##  <a name="nearbyintf"></a>nearbyintf  
 Redondea el argumento en un valor entero en formato de punto flotante, utilizando la dirección de redondeo actual.  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor entero redondeado.  
  
##  <a name="nextafter"></a>nextafter  
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
  
##  <a name="nextafterf"></a>nextafterf  
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
  
##  <a name="phi"></a>PHI  
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
  
##  <a name="phif"></a>phif)  
 Devuelve la función de distribución acumulativa del argumento  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa del argumento  
  
##  <a name="pow"></a>  pow  
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
  
##  <a name="powf"></a>powf  
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
  
##  <a name="probit"></a>probit  
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
  
##  <a name="probitf"></a>probitf)  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función de distribución acumulativa inversa del argumento  
  
##  <a name="rcbrt"></a>rcbrt  
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
  
##  <a name="rcbrtf"></a>rcbrtf  
 Devuelve el inverso de la raíz cúbica del argumento  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cúbica del argumento  
  
##  <a name="remainder"></a>resto  
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
  
##  <a name="remainderf"></a>remainderf  
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
  
##  <a name="remquo"></a>remquo  
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
  
##  <a name="remquof"></a>remquof  
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
  
##  <a name="round"></a>redondear  
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
  
##  <a name="roundf"></a>roundf  
 Redondea _X al entero más próximo  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el entero más cercano de _X  
  
##  <a name="rsqrt"></a>rsqrt  
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
  
##  <a name="rsqrtf"></a>rsqrtf  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el inverso de la raíz cuadrada del argumento  
  
##  <a name="scalb"></a>scalb  
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
  
##  <a name="scalbf"></a>scalbf  
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
  
##  <a name="scalbn"></a>scalbn  
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
  
##  <a name="scalbnf"></a>scalbnf  
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
  
##  <a name="signbit"></a>signbit  
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
  
##  <a name="signbitf"></a>signbitf  
 Determina si el inicio de sesión de _X es negativo  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el inicio de sesión de _X es negativo  
  
##  <a name="sin"></a>  sin  
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
  
##  <a name="sinf"></a>sinf  
 Calcula el valor del seno del argumento  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno del argumento  
  
##  <a name="sincos"></a>sincos  
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
  
##  <a name="sincosf"></a>sincosf  
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
  
##  <a name="sinh"></a>  sinh  
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
  
##  <a name="sinhf"></a>sinhf  
 Calcula el valor del seno hiperbólico del argumento  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno hiperbólico del argumento  
  
##  <a name="sinpi"></a>sinpi  
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
  
##  <a name="sinpif"></a>sinpif  
 Calcula el valor del seno de pi * _X  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del seno de pi * _X  
  
##  <a name="sqrt"></a>  sqrt  
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
  
##  <a name="sqrtf"></a>sqrtf  
 Calcula la raíz de squre del argumento  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la raíz de squre del argumento  
  
##  <a name="tan"></a>  tan  
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
  
##  <a name="tanf"></a>tanf  
 Calcula el valor del argumento de tangente  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del argumento de tangente  
  
##  <a name="tanh"></a>  tanh  
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
  
##  <a name="tanhf"></a>tanhf  
 Calcula el valor de la tangente hiperbólico del argumento  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la tangente hiperbólico del argumento  
  
##  <a name="tanpi"></a>tanpi  
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
  
##  <a name="tanpif"></a>tanpif  
 Calcula el valor de tangente de pi * _X  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de tangente de pi * _X  
  
##  <a name="tgamma"></a>tgamma  
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
  
##  <a name="tgammaf"></a>tgammaf)  
 Calcula la función gamma de _X  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resultado de la función gamma de _X  
  
##  <a name="trunc"></a>trunc  
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
  
##  <a name="truncf"></a>truncf  
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
 [Concurrency::precise_math (espacio de nombres)](concurrency-precise-math-namespace.md)

