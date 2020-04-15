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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341806"
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

*X*<br/>
El argumento de punto flotante.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve el registro natural (base-*e*) de (*x* + 1).

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Entrada|Resultado|Excepción SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Desnormalizados|Igual que la entrada|DESBORDAMIENTO||
|N.o 0|Igual que la entrada|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|•SNaN|Igual que la entrada|INVALID||
|QNaN, indefinido|Igual que la entrada|||

El valor **errno** se establece en ERANGE si *x* es -1. El valor **errno** se establece en **EDOM** si *x* < -1.

## <a name="remarks"></a>Observaciones

Las funciones **log1p** pueden `log(x + 1)` ser más precisas que usar cuando *x* está cerca de 0.

Dado que C++ permite la sobrecarga, puede llamar a sobrecargas de **log1p** que toman y devuelven **tipos float** y **long** **double.** En un programa C, **log1p** siempre toma y devuelve un **doble**.

Si *x* es un número natural, esta función devuelve el laquearitmo del factorial de (*x* - 1).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
