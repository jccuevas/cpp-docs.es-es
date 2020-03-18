---
title: Concurrency::precise_math (Funciones del espacio de nombres)
ms.date: 11/04/2016
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
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: 53ebaf8d9cc1bca53b1fe51464668d6df8e08424
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424930"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math (Funciones del espacio de nombres)

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
|[cospi (](#cospi)|[cospif (](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv (](#erfcinv)|
|[erfcinvf (](#erfcinvf)|[erff](#erff)|[erfinv (](#erfinv)|
|[erfinvf (](#erfinvf)|[exp](#exp)|[exp10 (](#exp10)|
|[exp10f (](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf (](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isFinite (](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf (](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[su](#phi)|[phif](#phif)|
|[pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt (](#rcbrt)|[rcbrtf (](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|
|[rsqrt (](#rsqrt)|[rsqrtf (](#rsqrtf)|[scalb (](#scalb)|
|[scalbf (](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf (](#signbitf)|[sin](#sin)|
|[sincos (](#sincos)|[sincosf (](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[SINPI (](#sinpi)|
|[sinpif (](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi (](#tanpi)|[tanpif (](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a>  acos

Calcula el arcocoseno del argumento.

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcocoseno del argumento.

## <a name="acosf"></a>acosf

Calcula el arcocoseno del argumento.

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcocoseno del argumento.

## <a name="acosh"></a>acosh

Calcula el coseno hiperbólico inverso del argumento.

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico inverso del argumento.

## <a name="acoshf"></a>acoshf (

Calcula el coseno hiperbólico inverso del argumento.

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico inverso del argumento.

## <a name="asin"></a>  asin

Calcula el arcoseno del argumento.

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcoseno del argumento.

## <a name="asinf"></a>asinf (

Calcula el arcoseno del argumento.

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcoseno del argumento.

## <a name="asinh"></a>Asinh

Calcula el seno hiperbólico inverso del argumento.

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico inverso del argumento.

## <a name="asinhf"></a>asinhf (

Calcula el seno hiperbólico inverso del argumento.

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico inverso del argumento.

## <a name="atan"></a>  atan

Calcula el arcotangente del argumento.

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arcotangente del argumento.

## <a name="atan2"></a>  atan2

Calcula el arcotangente de _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Y*<br/>
Valor de punto flotante

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arcotangente de _Y/_X

## <a name="atan2f"></a>atan2f (

Calcula el arcotangente de _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Y*<br/>
Valor de punto flotante

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arcotangente de _Y/_X

## <a name="atanf"></a>atanf (

Calcula el arcotangente del argumento.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arcotangente del argumento.

## <a name="atanh"></a>atanh

Calcula la tangente hiperbólica inversa del argumento.

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica inversa del argumento.

## <a name="atanhf"></a>atanhf (

Calcula la tangente hiperbólica inversa del argumento.

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica inversa del argumento.

## <a name="cbrt"></a>cbrt (

Calcula la raíz del cubo real del argumento.

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz del cubo real del argumento.

## <a name="cbrtf"></a>cbrtf (

Calcula la raíz del cubo real del argumento.

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz del cubo real del argumento.

## <a name="ceil"></a>Ceil (

Calcula el límite superior del argumento.

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior del argumento.

## <a name="ceilf"></a>ceilf (

Calcula el límite superior del argumento.

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior del argumento.

## <a name="copysign"></a>copysign

Genera un valor con la magnitud de _X y el signo de _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor con la magnitud de _X y el signo de _Y

## <a name="copysignf"></a>copysignf

Genera un valor con la magnitud de _X y el signo de _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor con la magnitud de _X y el signo de _Y

## <a name="cos"></a>  cos

Calcula el coseno del argumento.

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno del argumento.

## <a name="cosf"></a>cosf (

Calcula el coseno del argumento.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno del argumento.

## <a name="cosh"></a>  cosh

Calcula el valor del coseno hiperbólico del argumento.

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico del argumento.

## <a name="coshf"></a>coshf (

Calcula el valor del coseno hiperbólico del argumento.

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico del argumento.

## <a name="cospi"></a>cospi (

Calcula el valor de coseno de PI \* _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno de PI \* _X

## <a name="cospif"></a>cospif (

Calcula el valor de coseno de PI \* _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno de PI \* _X

## <a name="erf"></a>Fun

Calcula la función de error de _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error de _X

## <a name="erfc"></a>erfc

Calcula la función de error complementaria de _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error complementaria de _X

## <a name="erfcf"></a>erfcf (

Calcula la función de error complementaria de _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error complementaria de _X

## <a name="erfcinv"></a>erfcinv (

Calcula la función de error complementario inversa de _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error complementario inversa de _X

## <a name="erfcinvf"></a>erfcinvf (

Calcula la función de error complementario inversa de _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error complementario inversa de _X

## <a name="erff"></a>erff (

Calcula la función de error de _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error de _X

## <a name="erfinv"></a>erfinv (

Calcula la función de error inversa de _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error inversa de _X

## <a name="erfinvf"></a>erfinvf (

Calcula la función de error inversa de _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de error inversa de _X

## <a name="exp10"></a>exp10 (

Calcula el valor exponencial de base 10 del argumento.

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 10 del argumento.

## <a name="exp10f"></a>exp10f (

Calcula el valor exponencial de base 10 del argumento.

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 10 del argumento.

## <a name="expm1"></a>expm1 (

Calcula la base e exponencial del argumento, menos 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*exponente*<br/>
El término exponencial *n* de la expresión matemática `e`<sup>n</sup>, donde `e` es la base del logaritmo natural.

### <a name="return-value"></a>Valor devuelto

Devuelve la base e exponencial del argumento, menos 1

## <a name="expm1f"></a>expm1f (

Calcula la base e exponencial del argumento, menos 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*exponente*<br/>
El término exponencial *n* de la expresión matemática `e`<sup>n</sup>, donde `e` es la base del logaritmo natural.

### <a name="return-value"></a>Valor devuelto

Devuelve la base e exponencial del argumento, menos 1

## <a name="exp"></a>  exp

Calcula el valor exponencial de base e del argumento.

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base e del argumento.

## <a name="expf"></a>EXPF (

Calcula el valor exponencial de base e del argumento.

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base e del argumento.

## <a name="exp2"></a>exp2

Calcula el valor exponencial de base 2 del argumento.

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 2 del argumento.

## <a name="exp2f"></a>exp2f (

Calcula el valor exponencial de base 2 del argumento.

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 2 del argumento.

## <a name="fabs"></a>FABS

Devuelve el valor absoluto del argumento.

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

## <a name="fabsf"></a>fabsf

Devuelve el valor absoluto del argumento.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

## <a name="fdim"></a>FDIM (

Calcula la diferencia positiva entre los argumentos.

```cpp
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

*_X*<br/>
*_Y* de valor de punto flotante<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

La diferencia entre _X y _Y si _X es mayor que _Y; de lo contrario, + 0.

## <a name="fdimf"></a>fdimf (

Calcula la diferencia positiva entre los argumentos.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
*_Y* de valor de punto flotante<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

La diferencia entre _X y _Y si _X es mayor que _Y; de lo contrario, + 0.

## <a name="floor"></a>palabra

Calcula el piso del argumento.

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el piso del argumento.

## <a name="floorf"></a>floorf (

Calcula el piso del argumento.

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el piso del argumento.

## <a name="a-namefma-fma"></a><a name="fma"> FMA

Calcula el producto del primer y segundo argumento especificado y, a continuación, agrega el tercer argumento especificado al resultado; el cálculo completo se realiza como una sola operación.

```cpp
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

*_X*<br/>
Primer argumento de punto flotante.
*_Y*<br/>
Segundo argumento de punto flotante.
*_Z*<br/>
Tercer argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto

El resultado de la expresión (_X \* _Y) + _Z. El cálculo completo se realiza como una sola operación; es decir, las subexpresiones se calculan como precisión infinita y solo se redondea el resultado final.

## <a name="fmaf"></a>fmaf (

Calcula el producto del primer y segundo argumento especificado y, a continuación, agrega el tercer argumento especificado al resultado; el cálculo completo se realiza como una sola operación.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Primer argumento de punto flotante.
*_Y*<br/>
Segundo argumento de punto flotante.
*_Z*<br/>
Tercer argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto

El resultado de la expresión (_X \* _Y) + _Z. El cálculo completo se realiza como una sola operación; es decir, las subexpresiones se calculan como precisión infinita y solo se redondea el resultado final.

## <a name="fmax"></a>fMax

Determinar el valor numérico máximo de los argumentos

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor numérico máximo de los argumentos.

## <a name="fmaxf"></a>fmaxf

Determinar el valor numérico máximo de los argumentos

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor numérico máximo de los argumentos.

## <a name="fmin"></a>fMin (

Determinar el valor numérico mínimo de los argumentos

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor numérico mínimo de los argumentos.

## <a name="fminf"></a>fminf (

Determinar el valor numérico mínimo de los argumentos

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor numérico mínimo de los argumentos.

## <a name="fmod"></a>Función FMOD (C++ amp)

Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Primer argumento de punto flotante.

*_Y*<br/>
Segundo argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto

Resto de `_X` dividida por `_Y`; es decir, el valor de `_X` - `_Y`*n*, donde *n* es un entero de modo que la magnitud de `_X` - `_Y`*n* es menor que la magnitud de `_Y`.

## <a name="fmodf"></a>fmodf (

Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Primer argumento de punto flotante.

*_Y*<br/>
Segundo argumento de punto flotante.

### <a name="return-value"></a>Valor devuelto

Resto de `_X` dividida por `_Y`; es decir, el valor de `_X` - `_Y`*n*, donde *n* es un entero de modo que la magnitud de `_X` - `_Y`*n* es menor que la magnitud de `_Y`.

## <a name="fpclassify"></a>fpclassify (

Clasifica el valor del argumento como NaN, infinito, normal, subnormal, cero.

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la macro de clasificación de número correspondiente al valor del argumento.

## <a name="frexp"></a>frexp (

Obtiene la mantisa y el exponente de _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Exp*<br/>
Devuelve el exponente entero de _X en el valor de punto flotante.

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

## <a name="frexpf"></a>frexpf (

Obtiene la mantisa y el exponente de _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Exp*<br/>
Devuelve el exponente entero de _X en el valor de punto flotante.

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

## <a name="hypot"></a>hypot

Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz cuadrada de la suma de los cuadrados de _X y _Y

## <a name="hypotf"></a>hypotf

Calcula la raíz cuadrada de la suma de los cuadrados de _X y _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz cuadrada de la suma de los cuadrados de _X y _Y

## <a name="ilogb"></a>ilogb (

Extraer el exponente de _X como un valor int con signo

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponente de _X como valor int con signo.

## <a name="ilogbf"></a>ilogbf (

Extraer el exponente de _X como un valor int con signo

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponente de _X como valor int con signo.

## <a name="isfinite"></a>isFinite (

Determina si el argumento tiene un valor finito.

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor finito.

## <a name="isinf"></a>isinf (

Determina si el argumento es infinito.

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor infinito.

## <a name="isnan"></a>isNaN

Determina si el argumento es un NaN.

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor NaN.

## <a name="isnormal"></a>isnormal (

Determina si el argumento es normal.

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor normal.

## <a name="ldexp"></a>ldexp

Calcula un número real a partir de la mantisa y el exponente especificados.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mantisa

*_Exp*<br/>
Valor entero, exponente

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf (

Calcula un número real a partir de la mantisa y el exponente especificados.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mantisa

*_Exp*<br/>
Valor entero, exponente

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* 2 ^ _Exp

## <a name="lgamma"></a>lgamma (

Calcula el logaritmo natural del valor absoluto de gamma del argumento.

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Sign*<br/>
Devuelve el signo

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo natural del valor absoluto de gamma del argumento.

## <a name="lgammaf"></a>lgammaf (

Calcula el logaritmo natural del valor absoluto de gamma del argumento.

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Sign*<br/>
Devuelve el signo

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo natural del valor absoluto de gamma del argumento.

## <a name="log"></a>  log

Calcula el logaritmo en base e del argumento.

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e del argumento.

## <a name="log10"></a>  log10

Calcula el logaritmo en base 10 del argumento.

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

## <a name="log10f"></a>log10f (

Calcula el logaritmo en base 10 del argumento.

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

## <a name="log1p"></a>log1p (

Calcula el logaritmo en base e de 1 más el argumento.

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e de 1 más el argumento.

## <a name="log1pf"></a>log1pf (

Calcula el logaritmo en base e de 1 más el argumento.

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e de 1 más el argumento.

## <a name="log2"></a>LOG2

Calcula el logaritmo en base 2 del argumento.

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

## <a name="log2f"></a>log2f (

Calcula el logaritmo en base 2 del argumento.

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

## <a name="logb"></a>logb

Extrae el exponente de _X, como un valor entero con signo en formato de punto flotante.

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponente firmado de _X

## <a name="logbf"></a>logbf

Extrae el exponente de _X, como un valor entero con signo en formato de punto flotante.

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponente firmado de _X

## <a name="logf"></a>LOGF (

Calcula el logaritmo en base e del argumento.

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e del argumento.

## <a name="modf"></a>MODF (

Divide el argumento especificado en partes fraccionarias y enteras.

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Iptr*<br/>
enuncia Parte entera de `_X`, como un valor de punto flotante.

### <a name="return-value"></a>Valor devuelto

Parte fraccionaria con signo de `_X`.

## <a name="modff"></a>modff (

Divide el argumento especificado en partes fraccionarias y enteras.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Iptr*<br/>
Parte entera de `_X`, como un valor de punto flotante.

### <a name="return-value"></a>Valor devuelto

Devuelve la parte fraccionaria con signo de `_X`.

## <a name="nan"></a>nError

Devuelve un NaN silencioso

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve un NaN silencioso, si está disponible, con el contenido indicado en _X

## <a name="nanf"></a>nanf (

Devuelve un NaN silencioso

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve un NaN silencioso, si está disponible, con el contenido indicado en _X

## <a name="nearbyint"></a>nearbyint (

Redondea el argumento a un valor entero en formato de punto flotante, usando la dirección de redondeo actual.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor entero redondeado.

## <a name="nearbyintf"></a>nearbyintf (

Redondea el argumento a un valor entero en formato de punto flotante, usando la dirección de redondeo actual.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor entero redondeado.

## <a name="nextafter"></a>nextafter

Determine el siguiente valor que se va a representar, en el tipo de la función, después de _X en la dirección de _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el siguiente valor que se va a representar, en el tipo de la función, después de _X en la dirección de _Y

## <a name="nextafterf"></a>nextafterf

Determine el siguiente valor que se va a representar, en el tipo de la función, después de _X en la dirección de _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el siguiente valor que se va a representar, en el tipo de la función, después de _X en la dirección de _Y

## <a name="phi"></a>su

Devuelve la función de distribución acumulativa del argumento.

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de distribución acumulativa del argumento.

## <a name="phif"></a>phif

Devuelve la función de distribución acumulativa del argumento.

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de distribución acumulativa del argumento.

## <a name="pow"></a>  pow

Calcula _X elevado a la potencia de _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, base

*_Y*<br/>
Valor de punto flotante, exponente

### <a name="return-value"></a>Valor devuelto

## <a name="powf"></a>powf (

Calcula _X elevado a la potencia de _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, base

*_Y*<br/>
Valor de punto flotante, exponente

### <a name="return-value"></a>Valor devuelto

## <a name="probit"></a>probit

Devuelve la función de distribución acumulativa inversa del argumento.

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de distribución acumulativa inversa del argumento.

## <a name="probitf"></a>probitf

Devuelve la función de distribución acumulativa inversa del argumento.

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la función de distribución acumulativa inversa del argumento.

## <a name="rcbrt"></a>rcbrt (

Devuelve el recíproco de la raíz del cubo del argumento.

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz del cubo del argumento.

## <a name="rcbrtf"></a>rcbrtf (

Devuelve el recíproco de la raíz del cubo del argumento.

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz del cubo del argumento.

## <a name="remainder"></a>recorda

Calcula el resto: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X REM _Y

## <a name="remainderf"></a>remainderf (

Calcula el resto: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X REM _Y

## <a name="remquo"></a>remquo (

Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado. También calcula el cociente de la significación del primer argumento especificado dividido por el significado del segundo argumento especificado y devuelve el cociente utilizando la ubicación especificada en el tercer argumento.

```cpp
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

*_X*<br/>
Primer argumento de punto flotante.

*_Y*<br/>
Segundo argumento de punto flotante.

*_Quo*<br/>
enuncia Dirección de un entero que se usa para devolver el cociente de los bits fraccionarios de `_X` dividido entre los bits fraccionarios de `_Y`.

### <a name="return-value"></a>Valor devuelto

Devuelve el resto de `_X` dividida por `_Y`.

## <a name="remquof"></a>remquof (

Calcula el resto del primer argumento especificado dividido por el segundo argumento especificado. También calcula el cociente de la significación del primer argumento especificado dividido por el significado del segundo argumento especificado y devuelve el cociente utilizando la ubicación especificada en el tercer argumento.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Primer argumento de punto flotante.

*_Y*<br/>
Segundo argumento de punto flotante.

*_Quo*<br/>
enuncia Dirección de un entero que se usa para devolver el cociente de los bits fraccionarios de `_X` dividido entre los bits fraccionarios de `_Y`.

### <a name="return-value"></a>Valor devuelto

Devuelve el resto de `_X` dividida por `_Y`.

## <a name="round"></a>retorno

Redondea _X al entero más cercano

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero más próximo de _X

## <a name="roundf"></a>roundf

Redondea _X al entero más cercano

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero más próximo de _X

## <a name="rsqrt"></a>rsqrt (

Devuelve el recíproco de la raíz cuadrada del argumento.

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz cuadrada del argumento.

## <a name="rsqrtf"></a>rsqrtf (

Devuelve el recíproco de la raíz cuadrada del argumento.

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz cuadrada del argumento.

## <a name="scalb"></a>scalb (

Multiplica _X por FLT_RADIX a la potencia _Y

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* (FLT_RADIX ^ _Y)

## <a name="scalbf"></a>scalbf (

Multiplica _X por FLT_RADIX a la potencia _Y

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* (FLT_RADIX ^ _Y)

## <a name="scalbn"></a>scalbn (

Multiplica _X por FLT_RADIX a la potencia _Y

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* (FLT_RADIX ^ _Y)

## <a name="scalbnf"></a>scalbnf (

Multiplica _X por FLT_RADIX a la potencia _Y

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* (FLT_RADIX ^ _Y)

## <a name="signbit"></a>signbit (

Determina si el signo de _X es negativo.

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el signo de _X es negativo.

## <a name="signbitf"></a>signbitf (

Determina si el signo de _X es negativo.

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el signo de _X es negativo.

## <a name="sin"></a>  sin

Calcula el valor del seno del argumento.

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno del argumento.

## <a name="sinf"></a>sinf

Calcula el valor del seno del argumento.

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno del argumento.

## <a name="sincos"></a>sincos (

Calcula el valor de seno y coseno de _X

```cpp
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

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor de seno de _X

*_C*<br/>
Devuelve el valor de coseno de _X

## <a name="sincosf"></a>sincosf (

Calcula el valor de seno y coseno de _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor de seno de _X

*_C*<br/>
Devuelve el valor de coseno de _X

## <a name="sinh"></a>  sinh

Calcula el valor del seno hiperbólico del argumento.

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento.

## <a name="sinhf"></a>sinhf

Calcula el valor del seno hiperbólico del argumento.

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento.

## <a name="sinpi"></a>SINPI (

Calcula el valor de seno de PI \* _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de seno de PI \* _X

## <a name="sinpif"></a>sinpif (

Calcula el valor de seno de PI \* _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de seno de PI \* _X

## <a name="sqrt"></a>  sqrt

Calcula la raíz squre del argumento.

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz squre del argumento.

## <a name="sqrtf"></a>sqrtf (

Calcula la raíz squre del argumento.

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz squre del argumento.

## <a name="tan"></a>  tan

Calcula el valor de tangente del argumento.

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente del argumento.

## <a name="tanf"></a>TANF (

Calcula el valor de tangente del argumento.

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente del argumento.

## <a name="tanh"></a>  tanh

Calcula el valor de tangente hiperbólica del argumento.

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica del argumento.

## <a name="tanhf"></a>tanhf (

Calcula el valor de tangente hiperbólica del argumento.

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica del argumento.

## <a name="tanpi"></a>tanpi (

Calcula el valor de tangente de PI \* _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente de PI \* _X

## <a name="tanpif"></a>tanpif (

Calcula el valor de tangente de PI \* _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente de PI \* _X

## <a name="tgamma"></a>tgamma

Calcula la función gamma de _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de la función gamma de _X

## <a name="tgammaf"></a>tgammaf (

Calcula la función gamma de _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el resultado de la función gamma de _X

## <a name="trunc"></a>trunc

Trunca el argumento para el componente entero

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente entero del argumento.

## <a name="truncf"></a>truncf (

Trunca el argumento para el componente entero

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente entero del argumento.

## <a name="see-also"></a>Consulte también

[Concurrency::precise_math (espacio de nombres)](concurrency-precise-math-namespace.md)
