---
title: Concurrency::fast_math (Espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 5ca81d056ddf431b502f868f8a76959381b26260
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455983"
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math (Espacio de nombres)

Las funciones de la `fast_math` espacio de nombres tienen precisión inferior, admite sólo de precisión simple (`float`) y llamar a las funciones intrínsecas de DirectX. Hay dos versiones de cada función, por ejemplo `cos` y `cosf`. Ambas versiones toman y devuelven un `float`, pero cada uno de ellos llama a la misma forma a DirectX intrínseco.

## <a name="syntax"></a>Sintaxis

```
namespace fast_math;
```

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

|Name|Descripción|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula el arco coseno del argumento.|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula el arco coseno del argumento.|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|Calcula el arcoseno del argumento.|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|Calcula el arcoseno del argumento.|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Calcula el arcotangente del argumento.|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Calcula el arcotangente de _Y/_X.|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Calcula el arcotangente de _Y/_X.|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Calcula el arcotangente del argumento.|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Calcula el límite superior del argumento.|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Calcula el límite superior del argumento.|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula el coseno del argumento.|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula el coseno del argumento.|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Calcula el valor de coseno hiperbólico del argumento.|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Calcula el valor de coseno hiperbólico del argumento.|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Calcula la base e exponencial del argumento.|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Calcula el valor exponencial del argumento de base 2|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Calcula el valor exponencial del argumento de base 2|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Calcula la base e exponencial del argumento.|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Devuelve el valor absoluto del argumento.|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|Devuelve el valor absoluto del argumento.|
|[floor](concurrency-fast-math-namespace-functions.md#floor)|Calcula el valor inferior del argumento.|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Calcula el valor inferior del argumento.|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Determinar el valor numérico máximo de los argumentos|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Determinar el valor numérico máximo de los argumentos|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Determinar el valor numérico mínimo de los argumentos|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|Determinar el valor numérico mínimo de los argumentos|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Calcula el resto de punto flotante de _X/_Y.|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Calcula el resto de punto flotante de _X/_Y.|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Obtiene la mantisa y el exponente de _X.|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Obtiene la mantisa y el exponente de _X.|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Determina si el argumento tiene un valor finito|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Determina si el argumento es infinito|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|Determina si el argumento es un NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Calcula un número real de la mantisa y exponente|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Calcula un número real de la mantisa y exponente|
|[log](concurrency-fast-math-namespace-functions.md#log)|Calcula el logaritmo en base e del argumento.|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Calcula el logaritmo en base 10 del argumento.|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Calcula el logaritmo en base 10 del argumento.|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Calcula el logaritmo en base 2 del argumento.|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Calcula el logaritmo en base 2 del argumento.|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Calcula el logaritmo en base e del argumento.|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Divide _X en fracciones y partes de enteros.|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Divide _X en fracciones y partes de enteros.|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|Calcula _X elevado a la potencia de _Y|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Calcula _X elevado a la potencia de _Y|
|[round](concurrency-fast-math-namespace-functions.md#round)|Redondea _X al entero más próximo|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Redondea _X al entero más próximo|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Devuelve el recíproco de la raíz cuadrada del argumento.|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Devuelve el recíproco de la raíz cuadrada del argumento.|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Devuelve el signo del argumento.|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Devuelve el signo del argumento.|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|Calcula el valor del seno del argumento.|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|Calcula el valor de seno y coseno de _X.|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Calcula el valor de seno y coseno de _X.|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Calcula el valor del seno del argumento.|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|Calcula el valor del seno hiperbólico del argumento.|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Calcula el valor del seno hiperbólico del argumento.|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Calcula la raíz cuadrada del argumento.|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Calcula la raíz cuadrada del argumento.|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Calcula el valor de tangente del argumento.|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|Calcula el valor de tangente del argumento.|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|Calcula el valor de tangente hiperbólico del argumento.|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Calcula el valor de tangente hiperbólico del argumento.|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Trunca el argumento para el componente entero|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Trunca el argumento para el componente entero|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_math.h

**Namespace:** fast_math

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
