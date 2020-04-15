---
title: Tipos primitivos de punto flotante
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346707"
---
# <a name="floating-point-primitives"></a>Tipos primitivos de punto flotante

Funciones primitivas específicas de Microsoft que se usan para implementar algunas funciones de punto flotante de la biblioteca en tiempo de ejecución de C (CRT) estándar. Se documentan aquí para su integridad, pero no se recomienda su uso. Algunas de estas funciones se señalan como no utilizadas, porque se sabe que tienen problemas de precisión, control de excepciones y conformidad con el comportamiento IEEE-754. Existen en la biblioteca solo por compatibilidad con versiones anteriores. Para un comportamiento, portabilidad y adherencia correctos a los estándares, prefiera las funciones de punto flotante estándar sobre estas funciones.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Argumento de función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan las versiones C de la macro [fpclassify](fpclassify.md) de CRT para tipos de punto flotante. La clasificación del argumento *x* se devuelve como una de estas constantes, definidas en math.h:

|Value|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Un valor subnormal positivo o negativo (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener más información, puede usar las funciones de [_fpclass, _fpclassf](fpclass-fpclassf.md) específicas de Microsoft. Utilice la macro o función [fpclassify](fpclassify.md) para la portabilidad.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Argumento de función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan la macro o función [signbit](signbit.md) en el CRT. Devuelven un valor distinto de cero si el bit de signo se establece en el significado (mantisa) del argumento *x*y 0 si no se establece el bit de signo.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Argumentos de función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante toman dos argumentos, *x* e *y*, y devuelven un valor que muestra su relación de ordenación, expresada como bit a bit o de estas constantes, definidas en math.h:

| Value | Descripción |
|------------|-----------------|
| **_FP_LT** | *x* puede considerarse menor que *y* |
| **_FP_EQ** | *x* puede considerarse igual a *y* |
| **_FP_GT** | *x* puede considerarse mayor que *y* |

Estos primitivos implementan las macros y funciones [isgreater, isgreaterequal, isless, islessequal, islessgreater y isunordered](floating-point-ordering.md) en el CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parámetros

*Px*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan las versiones C++ de la función [CRT fpclassify](fpclassify.md) para tipos de punto flotante. El argumento *x* se evalúa y la clasificación se devuelve como una de estas constantes, definida en math.h:

|Value|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Un valor subnormal positivo o negativo (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener más información, puede usar las funciones de [_fpclass, _fpclassf](fpclass-fpclassf.md) específicas de Microsoft. Utilice la función [fpclassify](fpclassify.md) para la portabilidad.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parámetros

*Px*<br/>
Puntero a un argumento de punto flotante.

*Exp*<br/>
Un exponente como tipo entero.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante toman un puntero a un valor de punto flotante *px* y un valor de exponente *exp*, y eliminan la parte fraccionaria del valor de punto flotante debajo del exponente dado, si es posible. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito, y en el valor de salida en *px* de lo contrario.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parámetros

*Px*<br/>
Puntero a un argumento de punto flotante.

*Exp*<br/>
Un exponente como tipo entero.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante toman un puntero a un valor de punto flotante *px* y un valor de exponente *exp,* y escalan el valor en *px* por 2<sup>*exp*</sup>, si es posible. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito, y en el valor de salida en *px* de lo contrario. Para la portabilidad, prefiera las funciones [ldexp, ldexpf y ldexpl.](ldexp.md)

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parámetros

*pexp*<br/>
Puntero a un exponente como tipo entero.

*Px*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante descomponen el valor de punto flotante señalado por *px* en un significado (mantisa) y un exponente, si es posible. El significado se escala de tal forma que el valor absoluto es mayor o igual que 0,5 y menor que 1,0. El exponente es el valor *n*, donde el valor de punto flotante original es igual al significado escalado por 2<sup>*n*</sup>. Este exponente entero *n* se almacena en la ubicación señalada por *pexp*. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito, y en el valor de salida de lo contrario. Para la portabilidad, prefiere las funciones [frexp, frexpf, frexpl.](frexp.md)

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parámetros

*y y*<br/>
Argumento de función de punto flotante.

*Px*<br/>
Puntero a un argumento de punto flotante.

*Exp*<br/>
Un exponente como tipo entero.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante construyen un valor de punto flotante en la ubicación señalada por *px* igual a *y* * 2<sup>*exp*</sup>. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *y* si es un NaN o infinito, y en el valor de salida en *px* en caso contrario. Para la portabilidad, prefiera las funciones [ldexp, ldexpf y ldexpl.](ldexp.md)

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parámetros

*Ps*<br/>
Puntero a la representación bit a bit de un valor de punto flotante expresado como una matriz de **short sin signo** **.**

### <a name="remarks"></a>Observaciones

Estas primitivas de punto flotante normalizan la parte fraccionaria de un valor de punto flotante subfluido y ajustan la *característica,* o exponente sesgado, para que coincida. El valor se pasa como la representación bit a bit del tipo de `_double_val` `_ldouble_val`punto `_float_val` flotante convertido en una matriz de **unsigned** **short** a través de la , , o un ión de desplazamiento de tipo declarado en math.h. El valor devuelto es el resultado de **fpclassify** en el valor de punto flotante de entrada si es un NaN o infinito, y en el valor de salida en caso contrario.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Argumento de función de punto flotante.

*table*<br/>
Puntero a una tabla de coeficientes constantes para un polinomio.

*N*<br/>
Orden del polinomio a evaluar.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven la evaluación de *x* en el polinomio de orden *n* cuyos coeficientes están representados por los valores constantes correspondientes en la *tabla*. Por ejemplo, si la *tabla*\[0] es 3.0, *tabla*\[1] a 4,0, *tabla*\[2] a 5,0 y *n* a 2, representa el polinomio 5.0x<sup>2</sup> + 4.0x + 3.0. Si este polinomio se evalúa para *x* de 2.0, el resultado es 31.0. Estas funciones no se utilizan internamente.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Argumento de función de punto flotante.

*base_flag*<br/>
Marcador que controla la base que se va a utilizar, 0 para base *e* y no cero para la base 10.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven el registro natural de *x*, ln(*x*) o log<sub>*e*</sub>(*x*), cuando *base_flag* es 0. Devuelven la base de registro 10 de *x,* o el registro<sub>10</sub>(*x*), cuando *base_flag* es distinto de cero. Estas funciones no se utilizan internamente. Para la portabilidad, prefiera las funciones [log, logf, logl, log10, log10f y log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Argumento de función de punto flotante.

*Cuadrante*<br/>
Desplazamiento del cuadrante de 0, 1, `sin` `cos`2 `-sin`o `-cos` 3 para producir , , y resultados.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven el seno de *x* offset por el módulo de *cuadrante* 4. Efectivamente, devuelven el seno, coseno, -seno, y -coseno de *x* cuando el modulo *de cuadrante* 4 es 0, 1, 2, o 3, respectivamente. Estas funciones no se utilizan internamente. Para la portabilidad, prefiere las funciones [sinf, sinf, sinl](sin-sinf-sinl.md), [cos, cosf y cosl.](cos-cosf-cosl.md)

## <a name="requirements"></a>Requisitos

Encabezado: \<math.h>

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Soporte de punto flotante](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf e ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
