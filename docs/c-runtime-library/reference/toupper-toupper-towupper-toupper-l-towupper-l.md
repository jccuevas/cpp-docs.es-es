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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 943b66bf03420dc707415fd5da0ddf8cc3107d85
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913865"
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

*unidad*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas convierte una copia de *c*, si es posible, y devuelve el resultado.

Si *c* es un carácter ancho para el que **iswlower** es distinto de cero y hay un carácter ancho correspondiente para el que [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) es distinto de cero, **towupper** devuelve el carácter ancho correspondiente; de lo contrario, **towupper** devuelve *c* sin modificar.

No se reserva ningún valor devuelto para indicar un error.

Para que **ToUpper** proporcione los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [islower](islower-iswlower-islower-l-iswlower-l.md) deben devolver un valor distinto de cero.

## <a name="remarks"></a>Observaciones

Cada una de estas rutinas convierte una determinada letra minúscula en una letra mayúscula si es posible y pertinente. La conversión de mayúsculas y minúsculas de **towupper** es específica de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el sufijo **_L** usan la configuración regional establecida actualmente. Las versiones de estas funciones con el sufijo **_L** toman la configuración regional como parámetro y la usan en lugar de la configuración regional establecida en ese momento. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Para que **ToUpper** proporcione los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [isupper](isupper-isupper-l-iswupper-iswupper-l.md) deben devolver un valor distinto de cero.

[Rutinas de conversión de datos](../../c-runtime-library/data-conversion.md)

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**ToUpper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** y **_towupper_l** no tienen ninguna dependencia de la configuración regional y no están diseñados para llamarse directamente. Se proporcionan para uso interno de **_totupper_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ToUpper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Consulta también

[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
