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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c103d28dc111af4736bdc299b498b98eccb3af60
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916695"
---
# <a name="floating-point-primitives"></a>Tipos primitivos de punto flotante

Funciones primitivas específicas de Microsoft que se usan para implementar algunas funciones de punto flotante estándar de la biblioteca en tiempo de ejecución de C (CRT). Se documentan aquí por integridad, pero no se recomienda su uso. Algunas de estas funciones se indican como no utilizadas, ya que se sabe que tienen problemas de precisión, control de excepciones y cumplimiento del comportamiento IEEE-754. Solo existen en la biblioteca para mantener la compatibilidad con versiones anteriores. Para un comportamiento correcto, la portabilidad y el cumplimiento de los estándares, es preferible utilizar las funciones de punto flotante estándar en estas funciones.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de la función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan las versiones de C de la macro de CRT [fpclassify (](fpclassify.md) para los tipos de punto flotante. La clasificación del argumento *x* se devuelve como una de estas constantes, definidas en Math. h:

|Value|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Valor de subnormalización positivo o negativo (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener detalles adicionales, puede usar las funciones de [_fpclassf de _fpclass](fpclass-fpclassf.md) específicas de Microsoft. Use la macro o la función [fpclassify (](fpclassify.md) para la portabilidad.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de la función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan la macro o la función [signbit (](signbit.md) en CRT. Devuelven un valor distinto de cero si el bit de signo se establece en el significado (mantisa) del argumento *x*y 0 si no se establece el bit de signo.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Sintaxis

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Argumentos de la función de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante toman dos argumentos, *x* e y, y devuelven un valor que muestra su relación de ordenación, expresada como la operación OR *bit a bit*de estas constantes, definidas en Math. h:

| Value | Descripción |
|------------|-----------------|
| **_FP_LT** | *x* se puede considerar menor que *y* |
| **_FP_EQ** | *x* se puede considerar igual a *y* |
| **_FP_GT** | *x* se puede considerar mayor que *y* |

Estos primitivos implementan las macros y funciones [isgreater, isgreaterequal, isless, islessequal, islessgreater y isunordered](floating-point-ordering.md) en CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parámetros

*píxeles*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante implementan las versiones de C++ de la función de CRT [fpclassify (](fpclassify.md) para los tipos de punto flotante. El argumento *x* se evalúa y la clasificación se devuelve como una de estas constantes, definidas en Math. h:

|Value|Descripción|
|-----------|-----------------|
| **FP_NAN** | NaN reservado, de señalización o indeterminado |
| **FP_INFINITE** | Infinito positivo o negativo |
| **FP_NORMAL** | Valor positivo o negativo normalizado distinto de cero |
| **FP_SUBNORMAL** | Valor de subnormalización positivo o negativo (desnormalizado) |
| **FP_ZERO** | Valor cero positivo o negativo |

Para obtener detalles adicionales, puede usar las funciones de [_fpclassf de _fpclass](fpclass-fpclassf.md) específicas de Microsoft. Utilice la función [fpclassify (](fpclassify.md) para la portabilidad.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parámetros

*píxeles*<br/>
Puntero a un argumento de punto flotante.

*consumo*<br/>
Exponente como un tipo entero.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante toman un puntero a un valor de punto flotante *PX* y un valor de exponente *exp*, y quitan la parte fraccionaria del valor de punto flotante situado debajo del exponente dado, si es posible. El valor devuelto es el resultado de **fpclassify (** en el valor de entrada en *PX* si es un Nan o infinito, y en el valor de salida en *PX* en caso contrario.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parámetros

*píxeles*<br/>
Puntero a un argumento de punto flotante.

*consumo*<br/>
Exponente como un tipo entero.

### <a name="remarks"></a>Observaciones

Estas primitivas de punto flotante toman un puntero a un valor de punto flotante *PX* y un valor de exponente *exp*, y escalan el valor en *PX* por 2<sup>*exp*</sup>, si es posible. El valor devuelto es el resultado de **fpclassify (** en el valor de entrada en *PX* si es un Nan o infinito, y en el valor de salida en *PX* en caso contrario. Para portabilidad, prefiere las funciones [ldexp, ldexpf (y ldexpl](ldexp.md) .

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parámetros

*pexp*<br/>
Un puntero a un exponente como un tipo entero.

*píxeles*<br/>
Puntero a un argumento de punto flotante.

### <a name="remarks"></a>Observaciones

Estas primitivas de punto flotante dividen el valor de punto flotante señalado por *PX* en un significado (mantisa) y un exponente, si es posible. El significado se escala de forma que el valor absoluto sea mayor o igual que 0,5 y menor que 1,0. El exponente es el valor *n*, donde el valor de punto flotante original es igual que el tamaño de escalado de 2<sup>*n*</sup>. Este exponente entero *n* se almacena en la ubicación a la que señala *pexp*. El valor devuelto es el resultado de **fpclassify (** en el valor de entrada en *PX* si es un Nan o infinito, y en el valor de salida de lo contrario. Para portabilidad, prefiere las funciones [frexp (, frexpf (, frexpl](frexp.md) .

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parámetros

*sí*<br/>
Argumento de la función de punto flotante.

*píxeles*<br/>
Puntero a un argumento de punto flotante.

*consumo*<br/>
Exponente como un tipo entero.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante construyen un valor de punto flotante en la ubicación a la que apunta en *PX* igual a *y* * 2<sup>*exp*</sup>. El valor devuelto es el resultado de **fpclassify (** en el valor de entrada en *y* si es un Nan o infinito y en el valor de salida en *PX* en caso contrario. Para portabilidad, prefiere las funciones [ldexp, ldexpf (y ldexpl](ldexp.md) .

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Sintaxis

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parámetros

*PS*<br/>
Puntero a la representación bit a bit de un valor de punto flotante expresado como una matriz de **Short** **sin signo** .

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante normalizan la parte fraccionaria de un valor de punto flotante subdesbordamiento y ajustan la *característica*, o exponente sesgada, para que coincidan. El valor se pasa como la representación bit a bit del tipo de punto flotante convertido en una matriz de **Short** **sin signo** a través `_double_val`de `_ldouble_val`, o `_float_val` el tipo punning Union declarado en Math. h. El valor devuelto es el resultado de **fpclassify (** en el valor de punto flotante de entrada si es un Nan o infinito y en el valor de salida de lo contrario.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de la función de punto flotante.

*table*<br/>
Puntero a una tabla de coeficientes constantes de un polinomio.

*n*<br/>
Orden del polinomio que se va a evaluar.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven la evaluación de *x* en el polinomio de orden *n* cuyos coeficientes se representan mediante los valores constantes correspondientes de la *tabla*. Por ejemplo, si la *tabla*\[0] = 3,0, *tabla*\[1] = 4,0 *, tabla*\[2] = 5,0 y *n* = 2, representa el polinómico 5,0 x<sup>2</sup> + 4.0 x + 3,0. Si este polinomio se evalúa para *x* de 2,0, el resultado es 31,0. Estas funciones no se usan internamente.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de la función de punto flotante.

*base_flag*<br/>
Marca que controla la base que se va a usar, 0 para base *e* y distinto de cero para base 10.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven el registro natural de *x*, LN (*x*) o log<sub>*e*</sub>(*x*), cuando *base_flag* es 0. Devuelven la base logarítmica 10 de *x*o log<sub>10</sub>(*x*), cuando *base_flag* es distinto de cero. Estas funciones no se usan internamente. Para portabilidad, prefiere las funciones [log, LOGF (, logl, log10, log10f (y log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Sintaxis

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Argumento de la función de punto flotante.

*fases*<br/>
Desplazamiento del cuadrante de 0, 1, 2 o 3 que se va `sin`a `cos`usar `-sin`para generar `-cos` los resultados de,, y.

### <a name="remarks"></a>Observaciones

Estos primitivos de punto flotante devuelven el seno del desplazamiento *x* por el módulo de *cuadrante* 4. De hecho, devuelven el seno, el coseno, el seno y el coseno de *x* cuando el módulo de *cuadrante* 4 es 0, 1, 2 o 3, respectivamente. Estas funciones no se usan internamente. Para portabilidad, prefiere las funciones [sin, sinf, Sinl](sin-sinf-sinl.md), [cos, cosf (y COSL](cos-cosf-cosl.md) .

## <a name="requirements"></a>Requisitos

Encabezado: \<Math. h>

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Compatibilidad de punto flotante](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf (](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf (y ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
