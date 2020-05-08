---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 4/2/2020
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
- _o__tolower
- _o__tolower_l
- _o__towlower_l
- _o_tolower
- _o_towlower
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
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
ms.openlocfilehash: c8b27c4cc618d34d9da9b5884c6db2f525fd2388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910010"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

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

*unidad*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar para la traducción específica de configuración regional.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas convierte una copia de *c* a minúsculas si la conversión es posible, y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Observaciones

Cada una de estas rutinas convierte una determinada letra mayúscula en una letra minúscula si es posible y pertinente. La conversión de mayúsculas y minúsculas de **towlower** es específica de la configuración regional. Solo se convierten los caracteres pertinentes para la configuración regional actual. Las funciones sin el sufijo **_L** usan la configuración regional establecida actualmente. Las versiones de estas funciones que tienen el sufijo **_L** toman la configuración regional como parámetro y la usan en lugar de la configuración regional establecida en ese momento. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Para que **_tolower** proporcione los resultados esperados, [__isascii](isascii-isascii-iswascii.md) y [isupper](isupper-isupper-l-iswupper-iswupper-l.md) deben devolver un valor distinto de cero.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**ToLower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** y **_towlower_l** no tienen ninguna dependencia de la configuración regional y no están diseñados para llamarse directamente. Se proporcionan para uso interno de **_totlower_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ToLower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [to (Funciones)](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
