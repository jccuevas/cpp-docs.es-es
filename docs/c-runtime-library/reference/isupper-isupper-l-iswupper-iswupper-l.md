---
title: isupper, _isupper_l, iswupper, _iswupper_l
ms.date: 11/04/2016
api_name:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isupper
- _istupper
- iswupper
helpviewer_keywords:
- istupper function
- iswupper function
- isupper_l function
- _isupper_l function
- iswupper_l function
- _istupper function
- _iswupper_l function
- isupper function
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
ms.openlocfilehash: 558373d845b88d8959651d0a76e24af80cb6fa5e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953617"
---
# <a name="isupper-_isupper_l-iswupper-_iswupper_l"></a>isupper, _isupper_l, iswupper, _iswupper_l

Determina si un entero representa un carácter en mayúscula.

## <a name="syntax"></a>Sintaxis

```C
int isupper(
   int c
);
int _isupper_l (
   int c,
   _locale_t locale
);
int iswupper(
   wint_t c
);
int _iwsupper_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de una letra mayúscula. **isupper** devuelve un valor distinto de cero si *c* es un carácter en mayúscula (a-Z). **iswupper** devuelve un valor distinto de cero si *c* es un carácter ancho que corresponde a una letra mayúscula, o si *c* es uno de un conjunto de caracteres anchos definido por la implementación para el que no **iswcntrl**, **iswdigit**,  **iswpunct**o **iswspace** es distinto de cero. Cada una de estas rutinas devuelve 0 si *c* no cumple la condición de prueba.

Las versiones de estas funciones que tienen el sufijo **_L** usan la configuración regional que se pasa en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **isupper** y **_isupper_l** es undefined si *c* no es EOF o en el intervalo de 0 a 0xFF, ambos incluidos. Cuando se usa una biblioteca CRT de depuración y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istupper**|**isupper**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswupper**|
|**_istupper_l**|**_isupper_l**|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isupper**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**iswupper**|\<ctype.h> o \<wchar.h>|
|**_iswupper_l**|\<ctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
