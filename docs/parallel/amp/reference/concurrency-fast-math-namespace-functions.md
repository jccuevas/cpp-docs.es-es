---
title: Concurrency::fast_math (Funciones del espacio de nombres)
ms.date: 11/04/2016
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
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376396"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math (Funciones del espacio de nombres)

||||
|-|-|-|
|[Acos](#acos)|[acosf](#acosf)|[Asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[Ceil](#ceil)|
|[ceilf](#ceilf)|[Porque](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[Exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[Piso](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinita](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[Pow](#pow)|[powf](#powf)|
|[Redondo](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[Pecado](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[Sqrt](#sqrt)|[sqrtf](#sqrtf)|[bronceado](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[Trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Calcula la arccosina del argumento

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arccosina del argumento

## <a name="acosf"></a><a name="acosf"></a>acosf

Calcula la arccosina del argumento

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de arccosina del argumento

## <a name="asin"></a><a name="asin"></a>Asin

Calcula el arcoseno del argumento

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor arcsine del argumento

## <a name="asinf"></a><a name="asinf"></a>asinf

Calcula el arcoseno del argumento

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor arcsine del argumento

## <a name="atan"></a><a name="atan"></a>atan

Calcula el arcotangente del argumento.

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor arctangent del argumento

## <a name="atan2"></a><a name="atan2"></a>atan2

Calcula el arco tangente de _Y/_X

```cpp
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

Devuelve el valor arctangente de _Y/_X

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

Calcula el arco tangente de _Y/_X

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

Devuelve el valor arctangente de _Y/_X

## <a name="atanf"></a><a name="atanf"></a>atanf

Calcula el arcotangente del argumento.

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor arctangent del argumento

## <a name="ceil"></a><a name="ceil"></a>Ceil

Calcula el límite máximo del argumento

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite máximo del argumento

## <a name="ceilf"></a><a name="ceilf"></a>ceilf

Calcula el límite máximo del argumento

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el límite máximo del argumento

## <a name="cosf"></a><a name="cosf"></a>cosf

Calcula el coseno del argumento.

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor coseno del argumento

## <a name="coshf"></a><a name="coshf"></a>coshf

Calcula el valor del coseno hiperbólico del argumento

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico del argumento

## <a name="cos"></a><a name="cos"></a>Porque

Calcula el coseno del argumento.

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor coseno del argumento

## <a name="cosh"></a><a name="cosh"></a>Cosh

Calcula el valor del coseno hiperbólico del argumento

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del coseno hiperbólico del argumento

## <a name="exp"></a><a name="exp"></a>Exp

Calcula la exponencial base-e del argumento

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponencial base-e del argumento

## <a name="exp2"></a><a name="exp2"></a>exp2

Calcula el exponencial base-2 del argumento

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 2 del argumento.

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

Calcula el exponencial base-2 del argumento

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor exponencial de base 2 del argumento.

## <a name="expf"></a><a name="expf"></a>expf

Calcula la exponencial base-e del argumento

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el exponencial base-e del argumento

## <a name="fabs"></a><a name="fabs"></a>fabs

Devuelve el valor absoluto del argumento

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento

## <a name="fabsf"></a><a name="fabsf"></a>fabsf

Devuelve el valor absoluto del argumento

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento

## <a name="floor"></a><a name="floor"></a>Piso

Calcula el suelo del argumento

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el suelo del argumento

## <a name="floorf"></a><a name="floorf"></a>floorf

Calcula el suelo del argumento

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el suelo del argumento

## <a name="fmax"></a><a name="fmax"></a>Fmax

Determinar el valor numérico máximo de los argumentos

```cpp
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

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf

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

Devolver el valor numérico máximo de los argumentos

## <a name="fmin"></a><a name="fmin"></a>Fmin

Determinar el valor numérico mínimo de los argumentos

```cpp
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

## <a name="fminf"></a><a name="fminf"></a>fminf

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

Devolver el valor numérico mínimo de los argumentos

## <a name="fmod"></a><a name="fmod"></a>Fmod

Calcula el resto de punto flotante de _X/_Y

```cpp
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

Devuelve el resto de punto flotante de _X/_Y

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

Calcula el resto de punto flotante de _X/_Y.

```cpp
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

Devuelve el resto de punto flotante de _X/_Y

## <a name="frexp"></a><a name="frexp"></a>frexp

Obtiene la mantisa y el exponente de _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Exp*<br/>
Devuelve el exponente entero de _X en valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

## <a name="frexpf"></a><a name="frexpf"></a>frexpf

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
Devuelve el exponente entero de _X en valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la mantisa _X

## <a name="isfinite"></a><a name="isfinite"></a>isfinita

Determina si el argumento tiene un valor finito

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor finito

## <a name="isinf"></a><a name="isinf"></a>isinf

Determina si el argumento es un infinito

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor infinito

## <a name="isnan"></a><a name="isnan"></a>isnan

Determina si el argumento es un NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el argumento tiene un valor NaN

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Calcula un número real de la mantisa y el exponente

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mentissa

*_Exp*<br/>
Exponente entero

### <a name="return-value"></a>Valor devuelto

Devuelve \* _X 2_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf

Calcula un número real de la mantisa y el exponente

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante, mentissa

*_Exp*<br/>
Exponente entero

### <a name="return-value"></a>Valor devuelto

Devuelve \* _X 2_Exp

## <a name="log"></a><a name="log"></a>Registro

Calcula el logarritmo base-e del argumento

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarritmo base-e del argumento

## <a name="log10"></a><a name="log10"></a>log10

Calcula el ritmo base-10 del argumento

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarmritmo base-10 del argumento

## <a name="log10f"></a><a name="log10f"></a>log10f

Calcula el ritmo base-10 del argumento

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarmritmo base-10 del argumento

## <a name="log2"></a><a name="log2"></a>log2

Calcula el logarritmo base-2 del argumento

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarithm base-2 del argumento

## <a name="log2f"></a><a name="log2f"></a>log2f

Calcula el logarritmo base-2 del argumento

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarmritmo base-10 del argumento

## <a name="logf"></a><a name="logf"></a>logf

Calcula el logarritmo base-e del argumento

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el logarritmo base-e del argumento

## <a name="modf"></a><a name="modf"></a>modf

Divide _X en partes fraccionarias y enteras.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Ip*<br/>
Recibe una parte entera del valor

### <a name="return-value"></a>Valor devuelto

Devuelve la parte fraccionaria firmada de _X

## <a name="modff"></a><a name="modff"></a>modff

Divide _X en partes fraccionarias y enteras.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_Ip*<br/>
Recibe una parte entera del valor

### <a name="return-value"></a>Valor devuelto

Devuelve la parte fraccionaria firmada de _X

## <a name="pow"></a><a name="pow"></a>Pow

Calcula _X elevado a la potencia de _Y

```cpp
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

## <a name="powf"></a><a name="powf"></a>powf

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

## <a name="round"></a><a name="round"></a>Redondo

Redondea _X al entero más cercano

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero de _X

## <a name="roundf"></a><a name="roundf"></a>roundf

Redondea _X al entero más cercano

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el entero de _X

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

Devuelve la reciprocidad de la raíz cuadrada del argumento

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la reciprocidad de la raíz cuadrada del argumento

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

Devuelve la reciprocidad de la raíz cuadrada del argumento

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la reciprocidad de la raíz cuadrada del argumento

## <a name="signbit"></a><a name="signbit"></a>signbit

Determina si el signo de _X es negativo

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el signo de _X es negativo

## <a name="signbitf"></a><a name="signbitf"></a>signbitf

Determina si el signo de _X es negativo

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si y solo si el signo de _X es negativo

## <a name="sin"></a><a name="sin"></a>Pecado

Calcula el valor sinusoito del argumento

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor sinusoito del argumento

## <a name="sinf"></a><a name="sinf"></a>sinf

Calcula el valor sinusoito del argumento

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor sinusoito del argumento

## <a name="sincos"></a><a name="sincos"></a>sincos

Calcula el valor de seno y coseno de _X

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor sinusoito de _X

*_C*<br/>
Devuelve el valor del coseno de _X

## <a name="sincosf"></a><a name="sincosf"></a>sincosf

Calcula el valor de seno y coseno de _X

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

*_S*<br/>
Devuelve el valor sinusoito de _X

*_C*<br/>
Devuelve el valor del coseno de _X

## <a name="sinh"></a><a name="sinh"></a>Sinh

Calcula el valor del seno hiperbólico del argumento

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento

## <a name="sinhf"></a><a name="sinhf"></a>sinhf

Calcula el valor del seno hiperbólico del argumento

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor del seno hiperbólico del argumento

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Calcula la raíz del argumento

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz squre del argumento

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf

Calcula la raíz del argumento

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve la raíz squre del argumento

## <a name="tan"></a><a name="tan"></a>bronceado

Calcula el valor tangente del argumento

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor tangente del argumento

## <a name="tanf"></a><a name="tanf"></a>Tanf

Calcula el valor tangente del argumento

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor tangente del argumento

## <a name="tanh"></a><a name="tanh"></a>Tanh

Calcula el valor de tangente hiperbólico del argumento

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica del argumento

## <a name="tanhf"></a><a name="tanhf"></a>tanhf

Calcula el valor de tangente hiperbólico del argumento

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de tangente hiperbólica del argumento

## <a name="trunc"></a><a name="trunc"></a>Trunc

Trunca el argumento al componente entero

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente entero del argumento

## <a name="truncf"></a><a name="truncf"></a>truncf

Trunca el argumento al componente entero

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve el componente entero del argumento

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_math.h **Espacio de nombres:** Concurrency::fast_math

## <a name="see-also"></a>Consulte también

[Concurrency::fast_math (Espacio de nombres)](concurrency-fast-math-namespace.md)
