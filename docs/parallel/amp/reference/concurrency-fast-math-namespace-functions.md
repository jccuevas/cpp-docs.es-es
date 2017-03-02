---
title: Funciones del espacio de nombres fast_math | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4a01f48a7d087281ab1e9222d1077e92ab8b0d6c
ms.openlocfilehash: 0545a57c492f5c1872c71c04c99b54f86b644102
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyfastmath-namespace-functions"></a>Funciones del espacio de nombres fast_math
||||  
|-|-|-|  
|[ACOS (función)](#acos)|[acosf (función)](#acosf)|[ASIN (función)](#asin)|  
|[asinf (función)](#asinf)|[ATAN (función)](#atan)|[ATAN2 (función)](#atan2)|  
|[atan2f (función)](#atan2f)|[atanf (función)](#atanf)|[ceil (función)](#ceil)|  
|[ceilf (función)](#ceilf)|[COS (función)](#cos)|[cosf (función)](#cosf)|  
|[COSH (función)](#cosh)|[coshf (función)](#coshf)|[EXP (función)](#exp)|  
|[Exp2 (función)](#exp2)|[exp2f (función)](#exp2f)|[expf (función)](#expf)|  
|[fabs (función)](#fabs)|[fabsf (función)](#fabsf)|[Floor (función)](#floor)|  
|[floorf (función)](#floorf)|[Fmax (función)](#fmax)|[fmaxf (función)](#fmaxf)|  
|[Fmin (función)](#fmin)|[fminf (función)](#fminf)|[fmod (Función)](#fmod)|  
|[fmodf (función)](#fmodf)|[frexp (función)](#frexp)|[frexpf (función)](#frexpf)|  
|[isFinite (función)](#isfinite)|[isinf (función)](#isinf)|[isNaN (función)](#isnan)|  
|[ldexp (función)](#ldexp)|[ldexpf (función)](#ldexpf)|[log (función)](#log)|  
|[LOG10 (función)](#log10)|[log10f (función)](#log10f)|[LOG2 (función)](#log2)|  
|[log2f (función)](#log2f)|[logf (función)](#logf)|[modf (función)](#modf)|  
|[modff (función)](#modff)|[Pow (función)](#pow)|[powf (función)](#powf)|  
|[Round (función)](#round)|[roundf (función)](#roundf)|[rsqrt (función)](#rsqrt)|  
|[rsqrtf (función)](#rsqrtf)|[signbit (función)](#signbit)|[signbitf (función)](#signbitf)|  
|[sin (función)](#sin)|[sincos (función)](#sincos)|[sincosf (función)](#sincosf)|  
|[sinf (función)](#sinf)|[SINH (función)](#sinh)|[sinhf (función)](#sinhf)|  
|[SQRT (función)](#sqrt)|[sqrtf (función)](#sqrtf)|[tan (función)](#tan)|  
|[tanf (función)](#tanf)|[TANH (función)](#tanh)|[tanhf (función)](#tanhf)|  
|[TRUNC (función)](#trunc)|[truncf (función)](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>ACOS (función)  
 Calcula el arco coseno del argumento  
  
```  
inline float acos(float _X) restrict(amp);
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
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>ASIN (función)  
 Calcula el arco seno del argumento  
  
```  
inline float asin(float _X) restrict(amp);
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
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>ATAN (función)  
 Calcula el arco tangente del argumento  
  
```  
inline float atan(float _X) restrict(amp);
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
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil (función)  
 Calcula el límite superior del argumento  
  
```  
inline float ceil(float _X) restrict(amp);
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
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>COS (función)   
 Calcula el coseno del argumento  
  
```  
inline float cos(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de coseno hiperbólico del argumento  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>EXP (función)  
 Calcula la base e exponencial del argumento  
  
```  
inline float exp(float _X) restrict(amp);
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
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs (función)  
 Devuelve el valor absoluto del argumento  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
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
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>Floor (función)  
 Calcula el límite inferior del argumento  
  
```  
inline float floor(float _X) restrict(amp);
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
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>Fmax (función)  
 Determinar el valor numérico máximo de los argumentos  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
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
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
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
  
##  <a name="a-namefmoda--fmod-function"></a><a name="fmod"></a>fmod (función)  
 Calcula el resto de punto flotante de _X/_Y  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resto de punto flotante de _X/_Y  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf (función)  
 Calcula el resto de punto flotante de _X/_Y.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Y`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el resto de punto flotante de _X/_Y  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp (función)  
 Obtiene la mantisa y el exponente de _X  
  
```  
inline float frexp(
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
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isFinite (función)  
 Determina si el argumento tiene un valor finito  
  
```  
inline int isfinite(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si y solo si el argumento tiene un valor NaN  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp (función)  
 Calcula un número real de la mantisa y exponente  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante, mentissa  
  
 `_Exp`  
 Exponente de entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * 2 ^ _Exp  
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf (función)  
 Calcula un número real de la mantisa y exponente  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante, mentissa  
  
 `_Exp`  
 Exponente de entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X * 2 ^ _Exp  
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log (función)  
 Calcula el logaritmo en base e de argumento  
  
```  
inline float log(float _X) restrict(amp);
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
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>LOG2 (función)  
 Calcula el logaritmo en base&2; del argumento  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el logaritmo en base&2; del argumento  
  
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
 Divide _X en fracciones y partes enteras.  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Ip`  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la parte fraccionaria firmada de _X  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff (función)  
 Divide _X en fracciones y partes enteras.  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
 `_Ip`  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la parte fraccionaria firmada de _X  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>Pow (función)  
 Calcula _X elevado a la potencia de _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante de base  
  
 `_Y`  
 Valor de punto flotante de exponente  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de _X elevado a la potencia de _Y  
  
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
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>Round (función)  
 Redondea _X al entero más próximo  
  
```  
inline float round(float _X) restrict(amp);
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
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit (función)  
 Determina si el inicio de sesión de _X es negativo  
  
```  
inline int signbit(float _X) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>SQRT (función)  
 Calcula la raíz de squre del argumento  
  
```  
inline float sqrt(float _X) restrict(amp);
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
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>TRUNC (función)  
 Trunca el argumento para el componente de número entero  
  
```  
inline float trunc(float _X) restrict(amp);
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
 [Namespace fast_math](concurrency-fast-math-namespace.md)

