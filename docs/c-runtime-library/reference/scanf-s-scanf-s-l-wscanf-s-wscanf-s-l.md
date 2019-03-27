---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 28697cac20181c3dda0581c7486ebb673aec1241
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508811"
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

Lee datos con formato del flujo de entrada estándar. Estas versiones de [scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Cadena de control de formato.

*argument*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de campos convertidos y asignados correctamente. El valor devuelto no incluye los campos que se leyeron pero no asignados. Un valor devuelto de 0 indica que se ha asignado ningún campo. El valor devuelto es **EOF** para un error, o si el carácter de final de archivo o el carácter de final de cadena se encuentra en el primer intento de leer un carácter. Si *formato* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **scanf_s** y **wscanf_s** devolver **EOF** y establecer **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **scanf_s** función lee los datos de la secuencia de entrada estándar **stdin**y lo escribe en *argumento*. Cada *argumento* debe ser un puntero a un tipo de variable que se corresponde con el especificador de tipo en *formato*. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

**wscanf_s** es una versión con caracteres anchos de **scanf_s**; el *formato* argumento **wscanf_s** es una cadena de caracteres anchos. **wscanf_s** y **scanf_s** se comportan exactamente igual si el flujo se abre en modo ANSI. **scanf_s** no admite actualmente la entrada desde un flujo UNICODE.

Las versiones de estas funciones que tienen el **_l** sufijo son idénticas, salvo que usan el *configuración regional* parámetro en lugar de la configuración regional del subproceso actual.

A diferencia de **scanf** y **wscanf**, **scanf_s** y **wscanf_s** debe especificar los tamaños de búfer para algunos parámetros. Especificar los tamaños de todos los **c**, **C**, **s**, **S**, o conjunto de controles de la cadena **[]** parámetros. El tamaño del búfer en caracteres se pasa como un parámetro adicional. Inmediatamente se sigue el puntero en el búfer o variable. Por ejemplo, si está leyendo una cadena, el tamaño del búfer para esa cadena se pasa como sigue:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

El tamaño de búfer incluye el carácter null de terminal. Puede usar un campo de especificación de ancho para garantizar el token que se lee se ajustará en el búfer. Cuando un token es demasiado grande para caber, nada se escribe en el búfer, a menos que exista una especificación de ancho.

> [!NOTE]
> El parámetro de tamaño es de tipo **sin signo**, no **size_t**. Use una conversión estática para convertir un **size_t** valor **sin signo** configuraciones de compilación de 64 bits.

El parámetro de tamaño de búfer indica el número máximo de caracteres, no en bytes. En este ejemplo, el ancho del tipo de búfer no coincide con el ancho del especificador de formato.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

El **S** especificador de formato significa usar el ancho de caracteres es "opuesto" el ancho predeterminado admitido por la función. El ancho de caracteres es un solo byte, pero la función admite caracteres de doble byte. En este ejemplo lee una cadena de hasta nueve caracteres de byte-ancho y los coloca en un búfer de caracteres de doble byte-ancho. Los caracteres se tratan como valores de un solo byte; los primeros dos caracteres se almacenan en `ws[0]`, los siguientes dos se almacenan en `ws[1]`, y así sucesivamente.

En este ejemplo se lee un carácter único:

```C
char c;
scanf_s("%c", &c, 1);
```

Cuando se leen varios caracteres para cadenas no terminadas en null, se usan enteros para la especificación de ancho y el tamaño del búfer.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Para obtener más información, consulte [scanf (Especificación de ancho)](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**scanf_s**, **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**, **_wscanf_s_l**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Identificadores estándar de flujo **stdin**, **stdout**, y **stderr** debe redirigir antes las funciones de tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Este programa produce el siguiente resultado cuando se especifica esta entrada:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
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
