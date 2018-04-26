---
title: sscanf, _sscanf_l, swscanf, _swscanf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
apitype: DLLExport
f1_keywords:
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
dev_langs:
- C++
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8319a5546674b8a36d6d40037f356c7a1d33d80c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="sscanf-sscanfl-swscanf-swscanfl"></a>sscanf, _sscanf_l, swscanf, _swscanf_l

Lea datos con formato de una cadena. Hay disponibles versiones más seguras de estas funciones; vea [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Datos almacenados

*format*<br/>
Cadena de control de formato. Para obtener más información, consulte [Especificaciones de formato](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*Argumento*<br/>
Argumentos opcionales

*locale*<br/>
Configuración regional que se va a usar

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el número de campos convertidos y asignados correctamente; el valor devuelto no incluye los campos que se han leído pero no se han asignado. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** si hay un error o si se alcanza el final de la cadena antes de la primera conversión.

Si *búfer* o *formato* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **sscanf** función lee los datos de *búfer* en la ubicación proporcionada por cada *argumento*. Cada *argumento* debe ser un puntero a una variable con un tipo que se corresponde con un especificador de tipo en *formato*. El *formato* controles de argumento campos de la interpretación de la entrada y tiene el mismo formato y función que el *formato* argumento para el **scanf** función. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

> [!IMPORTANT]
> Al leer una cadena con **sscanf**, especifique siempre un ancho para el **%s** formato (por ejemplo, **"% 32s"** en lugar de **"%s"**); en caso contrario , la entrada con formato incorrecto puede provocar una saturación del búfer.

**swscanf** es una versión con caracteres anchos de **sscanf**; los argumentos a **swscanf** son cadenas de caracteres anchos. **sscanf** no controla caracteres hexadecimales multibyte. **swscanf** no controla caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode. En caso contrario, **swscanf** y **sscanf** se comportan exactamente igual.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**sscanf**, **_sscanf_l**|\<stdio.h>|
|**swscanf**, **_swscanf_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
