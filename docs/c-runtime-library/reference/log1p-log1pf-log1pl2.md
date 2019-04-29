---
title: log1p, log1pf, log1pl2
ms.date: 04/05/2018
apiname:
- log1p
- log1pf
- log1pl
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
ms.openlocfilehash: 2ac864d7e28823c95b0202c0a8f2454d03c64aff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285991"
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

Si es correcto, devuelve natural (base -*e*) de registro del (*x* + 1).

De lo contrario, es posible que devuelva uno de los siguientes valores:

|Entrada|Resultado|Excepción SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Desnormalizados|Igual que la entrada|UNDERFLOW||
|±0|Igual que la entrada|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|±SNaN|Igual que la entrada|INVALID||
|±QNaN, indefinite|Igual que la entrada|||

El **errno** valor se establece en ERANGE si *x* = -1. El **errno** valor se establece en **EDOM** si *x* < -1.

## <a name="remarks"></a>Comentarios

El **log1p** funciones pueden ser más precisas que el uso de `log(x + 1)` cuando *x* es próximo a 0.

Dado que C++ admite sobrecargas, puede llamar a sobrecargas de **log1p** que toman y devuelven **float** y **largo** **doble** tipos. En un programa C, **log1p** siempre toma y devuelve un **doble**.

Si *x* es un número natural, esta función devuelve el logaritmo del factorial de (*x* - 1).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
