---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957060"
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

**fpclassify (** devuelve un valor entero que indica la clase de punto flotante del argumento *x*. En esta tabla se muestran los posibles valoresdevueltos por \<fpclassify (, definidos en Math. h >.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|**FP_NAN**|NaN reservado, de señalización o indeterminado|
|**FP_INFINITE**|Infinito positivo o negativo|
|**FP_NORMAL**|Valor positivo o negativo normalizado distinto de cero|
|**FP_SUBNORMAL**|Valor positivo o negativo no normalizado|
|**FP_ZERO**|Valor cero positivo o negativo|

## <a name="remarks"></a>Comentarios

En C, **fpclassify (** es una macro; en C++, **fpclassify (** es una función sobrecargada mediante los tipos de argumento **float**, **Double**o **Long** **Double**. En cualquier caso, el valor devuelto depende del tipo efectivo de la expresión de argumento y no de alguna representación intermedia. Por ejemplo, un valor **Double** o **Long** **Double** normal puede convertirse en un valor infinito, desnormalizado o cero cuando se convierte en un valor **float**.

## <a name="requirements"></a>Requisitos

|Función o macro|Encabezado necesario (C)|Encabezado necesario (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> o \<cmath>|

Las funciones **fpclassify (** y **fpclassify (** se ajustan a las especificaciones ISO C99 y c++ 11. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
