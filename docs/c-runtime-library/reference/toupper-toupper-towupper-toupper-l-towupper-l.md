---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l
ms.date: 4/2/2020
api_name:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
- _o__toupper
- _o__toupper_l
- _o__towupper_l
- _o_toupper
- _o_towupper
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
- towupper
- _toupper
- _totupper
- toupper
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
ms.openlocfilehash: 85c218fdb3f5153e572e434bffbdb64510554d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362320"
---
# <a name="toupper-_toupper-towupper-_toupper_l-_towupper_l"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Convierte caracteres a mayúsculas.

## <a name="syntax"></a>Sintaxis

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas convierte una copia de *c*, si es posible, y devuelve el resultado.

Si *c* es un carácter ancho para el que **iswlower** es distinto de cero y hay un carácter ancho correspondiente para el que [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) es distinto de cero, **towupper** devuelve el carácter ancho correspondiente; de lo contrario, **el remolque** devuelve *c* sin cambios.

No se reserva ningún valor devuelto para indicar un error.

Para **que toupper** dé los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [esmás lento](islower-iswlower-islower-l-iswlower-l.md) deben devolver distinto de cero.

## <a name="remarks"></a>Observaciones

Cada una de estas rutinas convierte una determinada letra minúscula en una letra mayúscula si es posible y pertinente. La conversión de casos de remolque es específica de la configuración **regional.** Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el **sufijo _l** utilizan la configuración regional establecida actualmente. Las versiones de estas funciones con el sufijo **_l** toman la configuración regional como parámetro y lo utilizan en lugar de la configuración regional establecida actualmente. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Para **que toupper** dé los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [isupper](isupper-isupper-l-iswupper-iswupper-l.md) deben devolver distinto de cero.

[Rutinas de conversión de datos](../../c-runtime-library/data-conversion.md)

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** y **_towupper_l** no tienen dependencia local y no están destinados a ser llamados directamente. Se proporcionan para uso interno por **_totupper_l.**

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Consulte también

[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
