---
title: fpclassify
ms.date: 04/05/2018
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: a25897a110d96923a45695d61f923dc7818c7e3a
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518365"
---
# <a name="fpclassify"></a>fpclassify

Devuelve la clasificación de punto flotante del argumento.

## <a name="syntax"></a>Sintaxis

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Valor de punto flotante que se va a probar.

## <a name="return-value"></a>Valor devuelto

**fpclassify** devuelve un valor entero que indica la clase de punto flotante del argumento *x*. Esta tabla muestran los posibles valores devueltos por **fpclassify**, definido en \<math.h >.

|Valor|Descripción|
|-----------|-----------------|
|**FP_NAN**|NaN reservado, de señalización o indeterminado|
|**FP_INFINITE**|Infinito positivo o negativo|
|**FP_NORMAL**|Valor positivo o negativo normalizado distinto de cero|
|**FP_SUBNORMAL**|Valor positivo o negativo no normalizado|
|**FP_ZERO**|Valor cero positivo o negativo|

## <a name="remarks"></a>Comentarios

En C, **fpclassify** es una macro; en C++, **fpclassify** es una función sobrecargada con tipos de argumento de **float**, **doble**, o **largo** **doble**. En cualquier caso, el valor devuelto depende del tipo efectivo de la expresión de argumento y no de alguna representación intermedia. Por ejemplo, un normal **doble** o **largo** **doble** valor puede ser infinito, desnormalizado o cero el valor cuando se convierte en un **float**.

## <a name="requirements"></a>Requisitos

|Función o macro|Encabezado necesario (C)|Encabezado necesario (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> o \<cmath>|

El **fpclassify** macro y **fpclassify** funciones se ajustan a ISO C99 y C ++ 11 especificaciones. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
