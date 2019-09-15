---
title: log1p, log1pf, log1pl2
ms.date: 04/05/2018
api_name:
- log1p
- log1pf
- log1pl
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: aad6675a832e1715c505026fe11ffe77f1f6d275
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953215"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Calcula el logaritmo natural de 1 más el valor especificado.

## <a name="syntax"></a>Sintaxis

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
El argumento de punto flotante.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el logaritmo natural (base*e*) de (*x* + 1).

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Entrada|Resultado|Excepción SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Desnormalizados|Igual que la entrada|UNDERFLOW||
|±0|Igual que la entrada|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|± SNaN|Igual que la entrada|INVALID||
|± QNaN, indefinido|Igual que la entrada|||

El valor **errno** se establece en ERANGE si *x* =-1. El valor **errno** se establece en **EDOM** si *x* <-1.

## <a name="remarks"></a>Comentarios

Las funciones **log1p (** pueden ser más precisas que `log(x + 1)` cuando *x* está cerca de 0.

Dado C++ que permite las sobrecargas, puede llamar a las sobrecargas de **log1p (** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **log1p (** siempre toma y devuelve un **valor Double**.

Si *x* es un número natural, esta función devuelve el logaritmo del factorial de (*x* -1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
