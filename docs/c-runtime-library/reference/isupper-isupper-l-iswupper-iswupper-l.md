---
title: isupper, _isupper_l, iswupper, _iswupper_l
ms.date: 4/2/2020
api_name:
- isupper
- iswupper
- _iswupper_l
- _isupper_l
- _o_isupper
- _o_iswupper
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 713689649b33873796b7a73bad6a4ac6e8acc998
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342797"
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

*C*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve distinto de cero si *c* es una representación particular de una letra mayúscula. **isupper** devuelve un valor distinto de cero si *c* es un carácter en mayúsculas (A - Z). **iswupper** devuelve un valor distinto de cero si *c* es un carácter ancho que corresponde a una letra mayúscula, o si *c* es uno de un conjunto definido por la implementación de caracteres anchos para el que ninguno de **iswcntrl**, **iswdigit**, **iswpunct**o **iswspace** es distinto de cero. Cada una de estas rutinas devuelve 0 si *c* no satisface la condición de prueba.

Las versiones de estas funciones que tienen el **_l** sufijo usan la configuración regional que se pasa en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **isupper** y **_isupper_l** es indefinido si *c* no es EOF o en el rango 0 a 0xFF, ambos inclusive. Cuando se utiliza una biblioteca CRT de depuración y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istupper**|**isupper**|[_ismbcupper](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswupper**|
|**_istupper_l**|**_isupper_l**|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_iswupper_l**|

## <a name="remarks"></a>Observaciones

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isupper**|\<ctype.h>|
|**_isupper_l**|\<ctype.h>|
|**iswupper**|\<ctype.h> o \<wchar.h>|
|**_iswupper_l**|\<ctype.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
