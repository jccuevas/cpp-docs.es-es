---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
ms.openlocfilehash: 51469ccec348545ff780d14d5f433099def3eb69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511948"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Escribir datos con formato en una cadena. Se trata de versiones de [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento para los resultados

*sizeOfBuffer*<br/>
Número máximo de caracteres que se pueden almacenar.

*format*<br/>
Cadena de control de formato

*...*<br/>
Argumentos opcionales a los que dar formato

*locale*<br/>
Configuración regional que se va a usar.

Para más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor devuelto

El número de caracteres escritos, o -1 si se produjo un error. Si *búfer* o *formato* es un puntero nulo, **sprintf_s** y **swprintf_s** devuelven -1 y establezca **errno**a **EINVAL**.

**sprintf_s** devuelve el número de bytes almacenados en *búfer*, sin contar el carácter nulo de terminación. **swprintf_s** devuelve el número de caracteres anchos almacenados en *búfer*, sin contar el carácter ancho final null.

## <a name="remarks"></a>Comentarios

El **sprintf_s** función da formato y almacena una serie de caracteres y valores en *búfer*. Cada *argumento* (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. El formato consta de caracteres ordinarios y tiene el mismo formato y función que el *formato* argumento para [printf](printf-printf-l-wprintf-wprintf-l.md). Un carácter null se anexa después del último carácter escrito. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

Una diferencia principal entre **sprintf_s** y [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) es que **sprintf_s** comprueba la cadena de formato de caracteres de formato válidos, mientras que [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) solo comprueba si el búfer o cadena de formato son **NULL** punteros. Si hay errores en alguna comprobación, se invoca el controlador de parámetros no válidos, tal y como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y establece **errno** a **EINVAL**.

La principal diferencia entre **sprintf_s** y [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) es que **sprintf_s** toma un parámetro de longitud especifica el tamaño del búfer de salida en caracteres. Si el búfer es demasiado pequeño para el texto con formato, incluido el terminador nulo, entonces el búfer se establece en una cadena vacía colocando un carácter null en *búfer*[0], y se invoca el controlador de parámetros no válidos. A diferencia de **_snprintf**, **sprintf_s** garantiza que el búfer se termina en null a menos que el tamaño del búfer sea cero.

**swprintf_s** es una versión con caracteres anchos de **sprintf_s**; los argumentos de puntero **swprintf_s** son cadenas de caracteres anchos. Detección de errores de codificación **swprintf_s** podría diferir en **sprintf_s**. Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla. Las sobrecargas pueden realizar una inferencia de longitud de búfer automáticamente (lo que elimina la necesidad de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus equivalentes, seguras y más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Hay versiones de **sprintf_s** que ofrecer un mayor control sobre lo que sucede si el búfer es demasiado pequeño. Para obtener más información, consulta [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio> o \<stdio.h>|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio.h> o \<wchar.h><br /><br /> C++: \<cstdio>, \<cwchar>, \<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Ejemplo

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
