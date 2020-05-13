---
title: log1p, log1pf, log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
ms.openlocfilehash: 21bba72b204f975b806e43cdc6d36d8efa173b9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911427"
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
|Desnormalizados|Igual que la entrada|DESBORDAMIENTO||
|± 0|Igual que la entrada|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|± SNaN|Igual que la entrada|INVALID||
|± QNaN, indefinido|Igual que la entrada|||

El valor **errno** se establece en ERANGE si *x* =-1. El valor **errno** se establece en **EDOM** si *x* <-1.

## <a name="remarks"></a>Observaciones

Las funciones **log1p (** pueden ser más precisas que `log(x + 1)` cuando *x* está cerca de 0.

Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de **log1p (** que toman y devuelven los tipos **float** y **Long** **Double** . En un programa de C, **log1p (** siempre toma y devuelve un **valor Double**.

Si *x* es un número natural, esta función devuelve el logaritmo del factorial de (*x* -1).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log1p (**, **log1pf (**, **log1pl**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
