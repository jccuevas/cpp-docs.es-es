---
title: isdigit, iswdigit, _isdigit_l, _iswdigit_l
ms.date: 4/2/2020
api_name:
- _isdigit_l
- iswdigit
- _iswdigit_l
- isdigit
- _o_isdigit
- _o_iswdigit
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswdigit_l
- _isdigit_l
- iswdigit
- isdigit
- _istdigit
- _istdigit_l
helpviewer_keywords:
- iswdigit function
- iswdigit_l function
- _iswdigit_l function
- _istdigit_l function
- _istdigit function
- istdigit function
- isdigit function
- isdigit_l function
- _ismbcdigit_l function
- _isdigit_l function
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
ms.openlocfilehash: 70a370068ca05c430845a8eba83a73498384b067
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917588"
---
# <a name="isdigit-iswdigit-_isdigit_l-_iswdigit_l"></a>isdigit, iswdigit, _isdigit_l, _iswdigit_l

Determina si un entero representa un carácter de dígito decimal.

## <a name="syntax"></a>Sintaxis

```C
int isdigit(
   int c
);
int iswdigit(
   wint_t c
);
int _isdigit_l(
   int c,
   _locale_t locale
);
int _iswdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de un carácter de dígito decimal. **isdigit** devuelve un valor distinto de cero si *c* es un dígito decimal (0-9). **iswdigit** devuelve un valor distinto de cero si *c* es un carácter ancho que corresponde a un carácter de dígito decimal. Cada una de estas rutinas devuelve 0 si *c* no cumple la condición de prueba.

Las versiones de estas funciones que tienen el sufijo **_L** usan la configuración regional que se pasa en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **isdigit** y **_isdigit_l** es undefined si *c* no es EOF o en el intervalo comprendido entre 0 y 0xFF, ambos incluidos. Cuando se usa una biblioteca CRT de depuración y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istdigit**|**isdigit**|[_ismbcdigit](ismbcalnum-functions.md)|**iswdigit**|
|**_istdigit_l**|**_isdigit_l**|[_ismbcdigit_l](ismbcalnum-functions.md)|**_iswdigit_l**|

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isdigit**|\<ctype.h>|
|**iswdigit**|\<ctype.h> o \<wchar.h>|
|**_isdigit_l**|\<ctype.h>|
|**_iswdigit_l**|\<ctype.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
