---
title: Tipos primitivos de punto flotante
ms.date: 01/31/2019
apiname:
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
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703481"
---
# <a name="floating-point-primitives"></a>Tipos primitivos de punto flotante

Funciones primitivas específicas de Microsoft que se usan para implementar algunas funciones punto flotante de C runtime library (CRT) estándares. Estos se documentan aquí por integridad, pero no se recomiendan para su uso. Algunas de estas funciones son indican como no usados, porque se conocen a tener problemas de conformidad con respecto al comportamiento de IEEE-754, control de excepciones y precisión. Existen en la biblioteca sólo para compatibilidad con versiones anteriores. Para el comportamiento correcto, portabilidad y cumplimiento de estándares, prefieren las funciones de punto flotante estándar a través de estas funciones.

## <a name="dclass-ldclass-fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de función de punto flotante.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante implementan las versiones de C de la macro de CRT [fpclassify](fpclassify.md) para tipos de punto flotante. La clasificación del argumento *x* se devuelve como una de estas constantes, definidas en math.h:

|Valor|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Valor positivo o negativo subnormal (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener detalles adicionales, puede usar el específico de Microsoft [_fpclass, _fpclassf](fpclass-fpclassf.md) funciones. Use la [fpclassify](fpclassify.md) macro o función para la portabilidad.

## <a name="dsign-ldsign-fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de función de punto flotante.

### <a name="remarks"></a>Comentarios

Implementan estas primitivas de punto flotante del [signbit](signbit.md) macro o función de CRT. Devuelven un valor distinto de cero si el bit de signo se establece en el significado (mantisa) del argumento *x*y 0 si no se establece el bit de signo.

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Argumentos de función de punto flotante.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante toman dos argumentos, *x* y *y*y devuelve un valor que indica su relación de ordenación, expresada como el bit a bit o de estas constantes, definidas en math.h:

| Valor | Descripción |
|------------|-----------------|
| **_FP_LT** | *x* puede considerarse menor *y* |
| **_FP_EQ** | *x* pueden considerarse iguales a *y* |
| **_FP_GT** | *x* puede considerarse mayor *y* |

Implementan estas primitivas el [isgreater, isgreaterequal, isless, islessequal, islessgreater y isunordered](floating-point-ordering.md) macros y funciones de CRT.

## <a name="dtest-ldtest-fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parámetros

*px*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante implementan las versiones de C++ de la función de CRT [fpclassify](fpclassify.md) para tipos de punto flotante. El argumento *x* se evalúa y se devuelve la clasificación como una de estas constantes, definidas en math.h:

|Valor|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Valor positivo o negativo subnormal (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener detalles adicionales, puede usar el específico de Microsoft [_fpclass, _fpclassf](fpclass-fpclassf.md) funciones. Use la [fpclassify](fpclassify.md) función para la portabilidad.

## <a name="dint-ldint-fdint"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parámetros

*px*<br/>
Puntero a un argumento de punto flotante.

*exp*<br/>
Un exponente como un tipo entero.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante tienen un puntero a un valor de punto flotante *px* y un valor de exponente *exp*y quitar la parte fraccionaria del valor de punto flotante a continuación el exponente determinado, si es posible . El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito y en el valor de salida en *px* en caso contrario.

## <a name="dscale-ldscale-fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parámetros

*px*<br/>
Puntero a un argumento de punto flotante.

*exp*<br/>
Un exponente como un tipo entero.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante tienen un puntero a un valor de punto flotante *px* y un valor de exponente *exp*, y el valor de escala *px* 2<sup> *exp*</sup>, si es posible. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito y en el valor de salida en *px* en caso contrario. Para la portabilidad, prefiere la [ldexp, ldexpf y ldexpl](ldexp.md) funciones.

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parámetros

*pexp*<br/>
Un puntero a un exponente como un tipo entero.

*px*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante desglosar el valor de punto flotante al que apunta *px* en una mantisa (mantisa) y un exponente, si es posible. La mantisa se escala de forma que el valor absoluto es mayor o igual a 0,5 y menor que 1,0. El exponente es el valor *n*, donde el valor de punto flotante original es igual a la mantisa escalada veces 2<sup>*n*</sup>. Este exponente de entero *n* se almacena en la ubicación señalada por *pexp*. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *px* si es un NaN o infinito y en el valor de salida en caso contrario. Para la portabilidad, prefiere la [frexp, frexpf, frexpl](frexp.md) funciones.

## <a name="dexp-ldexp-fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parámetros

*y*<br/>
Argumento de función de punto flotante.

*px*<br/>
Puntero a un argumento de punto flotante.

*exp*<br/>
Un exponente como un tipo entero.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante construcción un valor de punto flotante en la ubicación apuntado a *px* igual a *y* * 2<sup>*exp*</sup>. El valor devuelto es el resultado de **fpclassify** en el valor de entrada en *y* si es un NaN o infinito y en el valor de salida en *px* en caso contrario. Para la portabilidad, prefiere la [ldexp, ldexpf y ldexpl](ldexp.md) funciones.

## <a name="dnorm-fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parámetros

*ps*<br/>
Puntero a la representación de bit a bit de un valor de punto flotante expresado como una matriz de **sin signo** **corto**.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante normalizar la parte fraccionaria de un valor de punto flotante underflowed y ajustar el *característica*, o exponente sesgado, para hacer coincidir. El valor se pasa como la representación del tipo de punto flotante se convierte en una matriz de bit a bit **sin signo** **corto** a través de la `_double_val`, `_ldouble_val`, o `_float_val` tipo Unión punning declarado en math.h. El valor devuelto es el resultado de **fpclassify** en el valor de punto flotante de entrada si es un NaN o infinito y en el valor de salida en caso contrario.

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de función de punto flotante.

*table*<br/>
Puntero a una tabla de coeficientes constantes para un polinómico.

*n*<br/>
Orden del polinomio para evaluar.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante devuelven la evaluación de *x* en polinomio de orden *n* cuyos coeficientes están representados por los valores constantes correspondientes en *tabla*. Por ejemplo, si *tabla*\[0] = 3.0, *tabla*\[1] = 4.0, *tabla*\[2] = 5.0, y *n* = 2, representa la x 5.0 polinómica<sup>2</sup> + 4.0 x + 3.0. Si se evalúa este polinómica para *x* de 2.0, el resultado es 31.0. Estas funciones no se usan internamente.

## <a name="dlog-dlog-dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de función de punto flotante.

*base_flag*<br/>
Marca que controla la base que se usará, 0 para base *e* y distinto de cero para la base 10.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante devuelven el logaritmo natural de *x*, ln (*x*) o de registro<sub>*e*</sub>(*x*), Cuando *base_flag* es 0. Devuelven el registro de base 10 de *x*, o de registro<sub>10</sub>(*x*), cuando *base_flag* es distinto de cero. Estas funciones no se usan internamente. Para la portabilidad, prefiere las funciones [logf, registro, logl, log10, log10f y log10l](log-logf-log10-log10f.md).

## <a name="dsin-ldsin-fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de función de punto flotante.

*quadrant*<br/>
Desplazamiento de cuadrante de 0, 1, 2 o 3 para utilizar para generar `sin`, `cos`, `-sin`, y `-cos` resultados.

### <a name="remarks"></a>Comentarios

Estas primitivas de punto flotante devuelven el seno de *x* desplazamiento por el *cuadrante* módulo 4. De hecho, devuelven el seno, coseno, seno y - coseno de *x* cuando *cuadrante* módulo 4 es 0, 1, 2 o 3, respectivamente. Estas funciones no se usan internamente. Para la portabilidad, prefiere la [sin, sinf, sinl](sin-sinf-sinl.md), [cos, cosf y cosl](cos-cosf-cosl.md) funciones.

## <a name="requirements"></a>Requisitos

Encabezado: \<math.h >

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad de punto flotante](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf y ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
