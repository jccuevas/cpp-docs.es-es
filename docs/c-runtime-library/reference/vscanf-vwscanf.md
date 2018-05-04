---
title: vscanf, vwscanf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vscanf
- vwscanf
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
- vscanf
- vwscanf
- _vtscanf
dev_langs:
- C++
ms.assetid: d1df595b-11bc-4682-9441-a92616301e3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825d0d61fccc6d0f83ae8b11648a3c7a3a9c50a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="vscanf-vwscanf"></a>vscanf, vwscanf

Lee datos con formato del flujo de entrada estándar. Hay disponibles versiones más seguras de estas funciones; vea [vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md).

## <a name="syntax"></a>Sintaxis

```C
int vscanf(
   const char *format,
   va_list arglist
);
int vwscanf(
   const wchar_t *format,
   va_list arglist
);

```

### <a name="parameters"></a>Parámetros

*format*<br/>
Cadena de control de formato.

*arglist*<br/>
Lista de argumentos de variable.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de campos que se han convertido y asignado correctamente; el valor devuelto no incluye los campos leídos pero no asignados. Un valor devuelto de 0 indica que no se ha asignado ningún campo.

Si *formato* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** y establecer **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **vscanf** función lee los datos del flujo de entrada estándar **stdin** y escribe los datos en las ubicaciones que se proporcionan en el *arglist* lista de argumentos. Cada argumento de la lista debe ser un puntero a una variable de un tipo que se corresponde con un especificador de tipo en *formato*. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

> [!IMPORTANT]
> Cuando usas **vscanf** para leer una cadena, especifique siempre un ancho para el **%s** formato (por ejemplo, **"% 32s"** en lugar de **"%s"**); en caso contrario, la entrada con formato incorrecto puede provocar una saturación del búfer. Como alternativa, puede usar [vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md) o [fgets](fgets-fgetws.md).

**vwscanf** es una versión con caracteres anchos de **vscanf**; el *formato* argumento pasado a **vwscanf** es una cadena de caracteres anchos. **vwscanf** y **vscanf** se comportan exactamente igual si el flujo se abre en modo ANSI. **vscanf** no admite la entrada desde un flujo UNICODE.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf**|**vscanf**|**vscanf**|**vwscanf**|

Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**vscanf**|\<stdio.h>|
|**vwscanf**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_vscanf.c
// compile with: /W3
// This program uses the vscanf and vwscanf functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>

int call_vscanf(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}

```

```Output

      71 98.6 h z Byte characters
36 92.3 y n Wide charactersThe number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vscanf_s, vwscanf_s](vscanf-s-vwscanf-s.md)<br/>
