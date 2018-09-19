---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73157691cc1635d038339d9fe707aa535e1df93f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413465"
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

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

*c*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas convierte una copia de *c*, si es posible y devuelve el resultado.

Si *c* es un carácter ancho para el que **iswlower** es distinto de cero y no hay un carácter ancho correspondiente para el que [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) es distinto de cero, **towupper** devuelve el carácter ancho correspondiente; en caso contrario, **towupper** devuelve *c* sin cambios.

No se reserva ningún valor devuelto para indicar un error.

En orden para **toupper** para proporcionar a los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [islower](islower-iswlower-islower-l-iswlower-l.md) debe devolver es distinto de cero.

## <a name="remarks"></a>Comentarios

Cada una de estas rutinas convierte una determinada letra minúscula en una letra mayúscula si es posible y pertinente. La conversión del tipo de **towupper** es específico de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el **_l** sufijo usar el conjunto actual configuración regional. Las versiones de estas funciones con el **_l** sufijo toman la configuración regional como parámetro y que utilice el conjunto actual configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En orden para **toupper** para proporcionar a los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [isupper](isupper-isupper-l-iswupper-iswupper-l.md) debe devolver es distinto de cero.

[Rutinas de conversión de datos](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** y **_towupper_l** no tienen dependen de la configuración regional y no están diseñadas para ser llamado directamente. Se proporcionan para uso interno exclusivo **_totupper_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Vea también

[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
