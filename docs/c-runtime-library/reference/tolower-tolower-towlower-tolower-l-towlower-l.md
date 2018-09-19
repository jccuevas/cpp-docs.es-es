---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs:
- C++
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49b52bd65439165ef8dd83917a0d75926caba518
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023671"
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Convierte un carácter a minúsculas.

## <a name="syntax"></a>Sintaxis

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar para la traducción específica de configuración regional.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas convierte una copia de *c* a minúsculas si la conversión es posible y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

Cada una de estas rutinas convierte una determinada letra mayúscula en una letra minúscula si es posible y pertinente. La conversión del tipo **towlower** es específico de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el **_l** sufijo usar el conjunto actual configuración regional. Las versiones de estas funciones que tienen el **_l** sufijo toman la configuración regional como parámetro y usarlo en lugar de establecida actualmente configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En orden para **_tolower** para proporcionar a los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [isupper](isupper-isupper-l-iswupper-iswupper-l.md) debe devolver cero.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** y **_towlower_l** no tienen dependen de la configuración regional y no están diseñados para ser llamado directamente. Se proporcionan para uso interno **_totlower_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
