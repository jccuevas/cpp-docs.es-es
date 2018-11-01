---
title: Funciones del espacio de nombres fast_math | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
dev_langs:
- C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f12ccee2bf282a324fcf4258190240ca8150bb2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446757"
---
# <a name="concurrencyfastmath-namespace-functions"></a>Funciones del espacio de nombres fast_math

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[pow](#pow)|[powf](#powf)|
|[round](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[sin](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

##  <a name="acos"></a>  acos

Calcula el arco coseno del argumento.

```
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcocoseno del argumento.

##  <a name="acosf"></a>  acosf

Calcula el arco coseno del argumento.

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcocoseno del argumento.

##  <a name="asin"></a>  asin

Calcula el arcoseno del argumento.

```
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcoseno del argumento.

##  <a name="asinf"></a>  asinf

Calcula el arcoseno del argumento.

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcoseno del argumento.

##  <a name="atan"></a>  atan

Calcula el arcotangente del argumento.

```
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcotangente del argumento.

##  <a name="atan2"></a>  atan2

Calcula el arcotangente de _Y/_X.

```
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Y*<br/>
Valor de punto flotante

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcotangente de _Y/_X.

##  <a name="atan2f"></a>  atan2f

Calcula el arcotangente de _Y/_X.

```
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

Devuelve el valor del arcotangente de _Y/_X.

##  <a name="atanf"></a>  atanf

Calcula el arcotangente del argumento.

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del arcotangente del argumento.

##  <a name="ceil"></a>  ceil

Calcula el límite superior del argumento.

```
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior del argumento.

##  <a name="ceilf"></a>  ceilf

Calcula el límite superior del argumento.

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior del argumento.

##  <a name="cosf"></a>  cosf

Calcula el coseno del argumento.

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno del argumento.

##  <a name="coshf"></a>  coshf

Calcula el valor de coseno hiperbólico del argumento.

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno hiperbólico del argumento.

##  <a name="cos"></a>  cos

Calcula el coseno del argumento.

```
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno del argumento.

##  <a name="cosh"></a>  cosh

Calcula el valor de coseno hiperbólico del argumento.

```
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de coseno hiperbólico del argumento.

##  <a name="exp"></a>  exp

Calcula la base e exponencial del argumento.

```
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la base e exponencial del argumento.

##  <a name="exp2"></a>  exp2

Calcula el valor exponencial del argumento de base 2

```
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial del argumento de base 2

##  <a name="exp2f"></a>  exp2f

Calcula el valor exponencial del argumento de base 2

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial del argumento de base 2

##  <a name="expf"></a>  expf

Calcula la base e exponencial del argumento.

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la base e exponencial del argumento.

##  <a name="fabs"></a>  fabs

Devuelve el valor absoluto del argumento.

```
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

##  <a name="fabsf"></a>  fabsf

Devuelve el valor absoluto del argumento.

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

##  <a name="floor"></a>  floor

Calcula el valor inferior del argumento.

```
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior del argumento.

##  <a name="floorf"></a>  floorf

Calcula el valor inferior del argumento.

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior del argumento.

##  <a name="fmax"></a>  fmax

Determinar el valor numérico máximo de los argumentos

```
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico máximo de los argumentos

##  <a name="fmaxf"></a>  fmaxf

Determinar el valor numérico máximo de los argumentos

```
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

Devolver el valor numérico máximo de los argumentos

##  <a name="fmin"></a>  fmin

Determinar el valor numérico mínimo de los argumentos

```
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico mínimo de los argumentos

##  <a name="fminf"></a>  fminf

Determinar el valor numérico mínimo de los argumentos

```
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

Devolver el valor numérico mínimo de los argumentos

##  <a name="fmod"></a>  fmod

Calcula el resto de punto flotante de _X/_Y.

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el resto de punto flotante de _X/_Y.

##  <a name="fmodf"></a>  fmodf

Calcula el resto de punto flotante de _X/_Y.

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Y*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el resto de punto flotante de _X/_Y.

##  <a name="frexp"></a>  frexp

Obtiene la mantisa y el exponente de _X.

```
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Exp*<br/>
Devuelve al exponente de entero de _X en el valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

##  <a name="frexpf"></a>  frexpf

Obtiene la mantisa y el exponente de _X.

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Exp*<br/>
Devuelve al exponente de entero de _X en el valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

##  <a name="isfinite"></a>  isfinite

Determina si el argumento tiene un valor finito

```
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor finito

##  <a name="isinf"></a>  isinf

Determina si el argumento es infinito

```
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor infinito

##  <a name="isnan"></a>  isNaN)

Determina si el argumento es un NaN

```
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor NaN

##  <a name="ldexp"></a>  ldexp

Calcula un número real de la mantisa y exponente

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mentissa

*_Exp*<br/>
Exponente de entero

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* 2 ^ _Exp

##  <a name="ldexpf"></a>  ldexpf

Calcula un número real de la mantisa y exponente

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mentissa

*_Exp*<br/>
Exponente de entero

### <a name="return-value"></a>Valor devuelto

Devuelve _X \* 2 ^ _Exp

##  <a name="log"></a>  log

Calcula el logaritmo en base e del argumento.

```
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e del argumento.

##  <a name="log10"></a>  log10

Calcula el logaritmo en base 10 del argumento.

```
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

##  <a name="log10f"></a>  log10f

Calcula el logaritmo en base 10 del argumento.

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

##  <a name="log2"></a>  log2

Calcula el logaritmo en base 2 del argumento.

```
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 2 del argumento.

##  <a name="log2f"></a>  log2f

Calcula el logaritmo en base 2 del argumento.

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base 10 del argumento.

##  <a name="logf"></a>  logf

Calcula el logaritmo en base e del argumento.

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logaritmo en base e del argumento.

##  <a name="modf"></a>  modf

Divide _X en fracciones y partes de enteros.

```
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Ip*<br/>
Recibe la parte entera del valor

### <a name="return-value"></a>Valor devuelto

Devuelve la parte fraccionaria con signo de _X

##  <a name="modff"></a>  modff

Divide _X en fracciones y partes de enteros.

```
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Ip*<br/>
Recibe la parte entera del valor

### <a name="return-value"></a>Valor devuelto

Devuelve la parte fraccionaria con signo de _X

##  <a name="pow"></a>  pow

Calcula _X elevado a la potencia de _Y

```
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, base

*_Y*<br/>
Valor de punto flotante, exponente

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de _X elevado a la potencia de _Y

##  <a name="powf"></a>  powf

Calcula _X elevado a la potencia de _Y

```
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

##  <a name="round"></a>  redondear

Redondea _X al entero más próximo

```
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero más cercano de _X.

##  <a name="roundf"></a>  roundf

Redondea _X al entero más próximo

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero más cercano de _X.

##  <a name="rsqrt"></a>  rsqrt

Devuelve el recíproco de la raíz cuadrada del argumento.

```
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz cuadrada del argumento.

##  <a name="rsqrtf"></a>  rsqrtf

Devuelve el recíproco de la raíz cuadrada del argumento.

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el recíproco de la raíz cuadrada del argumento.

##  <a name="signbit"></a>  signbit

Determina si el inicio de sesión de _X es negativo

```
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el inicio de sesión de _X es negativo

##  <a name="signbitf"></a>  signbitf

Determina si el inicio de sesión de _X es negativo

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el inicio de sesión de _X es negativo

##  <a name="sin"></a>  sin

Calcula el valor del seno del argumento.

```
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno del argumento.

##  <a name="sinf"></a>  sinf

Calcula el valor del seno del argumento.

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno del argumento.

##  <a name="sincos"></a>  sincos

Calcula el valor de seno y coseno de _X.

```
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor de seno de _X.

*_E*<br/>
Devuelve el valor de coseno de _X.

##  <a name="sincosf"></a>  sincosf

Calcula el valor de seno y coseno de _X.

```
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor de seno de _X.

*_E*<br/>
Devuelve el valor de coseno de _X.

##  <a name="sinh"></a>  sinh

Calcula el valor del seno hiperbólico del argumento.

```
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento.

##  <a name="sinhf"></a>  sinhf

Calcula el valor del seno hiperbólico del argumento.

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento.

##  <a name="sqrt"></a>  sqrt

Calcula la raíz de squre del argumento.

```
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz de squre del argumento.

##  <a name="sqrtf"></a>  sqrtf

Calcula la raíz de squre del argumento.

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz de squre del argumento.

##  <a name="tan"></a>  tan

Calcula el valor de tangente del argumento.

```
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente del argumento.

##  <a name="tanf"></a>  tanf

Calcula el valor de tangente del argumento.

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente del argumento.

##  <a name="tanh"></a>  tanh

Calcula el valor de tangente hiperbólico del argumento.

```
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólico del argumento.

##  <a name="tanhf"></a>  tanhf

Calcula el valor de tangente hiperbólico del argumento.

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólico del argumento.

##  <a name="trunc"></a>  trunc

Trunca el argumento para el componente entero

```
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente de número entero del argumento.

##  <a name="truncf"></a>  truncf

Trunca el argumento para el componente entero

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente de número entero del argumento.

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_math.h **Namespace:** fast_math

## <a name="see-also"></a>Vea también

[Concurrency::fast_math (espacio de nombres)](concurrency-fast-math-namespace.md)
