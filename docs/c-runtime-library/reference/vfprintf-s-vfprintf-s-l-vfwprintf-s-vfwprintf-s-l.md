---
title: vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l
ms.date: 11/04/2016
api_name:
- vfwprintf_s
- _vfprintf_s_l
- vfprintf_s
- _vfwprintf_s_l
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vftprintf_s
- vfwprintf_s
- vfprintf_s
helpviewer_keywords:
- vfprintf_s_l function
- vfwprintf_s_l function
- vfwprintf_s function
- _vfprintf_s_l function
- _vfwprintf_s_l function
- vftprintf_s_l function
- vfprintf_s function
- _vftprintf_s_l function
- formatted text [C++]
- _vftprintf_s function
ms.assetid: eab6f563-46e2-4806-963f-2b23f339ecdc
ms.openlocfilehash: d7c3d268689fe8d60b4b3804223d7bba206bbed1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957445"
---
# <a name="vfprintf_s-_vfprintf_s_l-vfwprintf_s-_vfwprintf_s_l"></a>vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l

Escribe un resultado con formato mediante un puntero a una lista de argumentos. Estas son versiones de [vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int vfprintf_s(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vfwprintf_s(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

*format*<br/>
Especificación de formato.

*argptr*<br/>
Puntero a la lista de argumentos.

*locale*<br/>
Configuración regional que se va a usar.

Para más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

**vfprintf_s** y **vfwprintf_s** devuelven el número de caracteres escritos, sin incluir el carácter nulo de terminación, o un valor negativo si se produce un error de salida. Si la *secuencia* o el *formato* es un puntero nulo, o si la cadena de formato contiene caracteres de formato no válidos, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven-1 y establecen **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, da formato y escribe los datos especificados en la *secuencia*.

Estas funciones solo se diferencian de las versiones no seguras en que las versiones seguras comprueban que la cadena de *formato* contiene caracteres de formato válidos.

**vfwprintf_s** es la versión con caracteres anchos de **vfprintf_s**; las dos funciones se comportan exactamente igual si la secuencia se abre en modo ANSI. **vfprintf_s** no admite actualmente la salida en un flujo Unicode.

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_s**|**vfprintf_s**|**vfprintf_s**|**vfwprintf_s**|
|**_vftprintf_s_l**|**_vfprintf_s_l**|**_vfprintf_s_l**|**_vfwprintf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**vfprintf_s**, **_vfprintf_s_l**|\<stdio.h> y \<stdarg.h>|\<varargs.h>*|
|**vfwprintf_s**, **_vfwprintf_s_l**|\<stdio.h> o \<wchar.h> y \<stdarg.h>|\<varargs.h>*|

\* Necesario para la compatibilidad con UNIX V.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
