---
title: printf, _printf_l, wprintf, _wprintf_l
ms.date: 11/04/2016
api_name:
- _printf_l
- wprintf
- _wprintf_l
- printf
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
- printf
- _tprintf
- wprintf
helpviewer_keywords:
- printf function
- printf_l function
- tprintf_l function
- tprintf function
- _printf_l function
- wprintf function
- writing to console
- wprintf_l function
- _tprintf_l function
- _wprintf_l function
- _tprintf function
- printf function, format specification fields
- printf function, using
- formatted text [C++]
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
ms.openlocfilehash: 73de90667479fff647e399068f9b97453819d27c
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507058"
---
# <a name="printf-_printf_l-wprintf-_wprintf_l"></a>printf, _printf_l, wprintf, _wprintf_l

Imprime el resultado con formato en la cadena de salida estándar. Hay versiones más seguras de estas funciones disponibles; vea [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int printf(
   const char *format [,
   argument]...
);
int _printf_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf(
   const wchar_t *format [,
   argument]...
);
int _wprintf_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Control de formato.

*argument*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres impreso o un valor negativo si se produce un error. Si *Format* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve-1 y establece **errno** en **EINVAL**. Si se encuentra **EOF** (0xFFFF) en el *argumento*, la función devuelve-1.

Para obtener información sobre **errno** y códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **printf** da formato e imprime una serie de caracteres y valores en el flujo de salida estándar, **stdout**. Si los argumentos siguen a la cadena de *formato* , la cadena de *formato* debe contener especificaciones que determinen el formato de salida de los argumentos. **printf** y [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md) se comportan exactamente igual, salvo que **printf** escribe la salida en **stdout** en lugar de en un destino de tipo **File**.

**wprintf** es una versión con caracteres anchos de **printf**; *Format* es una cadena de caracteres anchos. **wprintf** y **printf** se comportan exactamente igual si la secuencia se abre en modo ANSI. **printf** no admite actualmente la salida en un flujo Unicode.

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_unicode definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|

El argumento de *formato* consta de caracteres ordinarios, secuencias de escape y (si los argumentos siguen *formato*) Especificaciones de formato. Los caracteres ordinarios y las secuencias de escape se copian en **stdout** en orden de aparición. Por ejemplo, la línea:

```C
printf("Line one\n\t\tLine two\n");
```

genera el resultado:

```Output
Line one
        Line two
```

Las [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) siempre comienzan con un signo de porcentaje ( **%** ) y se leen de izquierda a derecha. Cuando **printf** encuentra la primera especificación de formato (si existe), convierte el valor del primer argumento después del *formato* y lo envía en consecuencia. La segunda especificación de formato genera el segundo argumento que se convertirá y saldrá, y así sucesivamente. Si hay más argumentos que especificaciones de formato, se omiten los argumentos adicionales. Los resultados son indefinidos si no hay suficientes argumentos para todas las especificaciones de formato.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tprintf**|**printf**|**printf**|**wprintf**|
|**_tprintf_l**|**_printf_l**|**_printf_l**|**_wprintf_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**printf**, **_printf_l**|\<stdio.h>|
|**wprintf**, **_wprintf_l**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Los identificadores de flujo estándar que están asociados a la consola, **stdin**, **stdout**y **stderr**deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

> [!IMPORTANT]
> A partir de la versión 2004 de Windows 10 (compilación 19041), la `printf` familia de funciones imprime los números de punto flotante que se representarán exactamente según las reglas IEEE 754 para el redondeo. En versiones anteriores de Windows, los números de punto flotante que se representaban exactamente finales de ' 5 ' siempre se redondeaban. IEEE 754 indica que deben redondear al dígito par más cercano (también conocido como "redondeo bancario"). Por ejemplo, 1,5 y 2,5 se deben redondear a 2. Anteriormente, 1,5 se redondeaba a 2 y 2,5 se redondeaba a 3. Este cambio solo afecta a los números que se van a representar exactamente. Por ejemplo, 2,35 (que, cuando se representa en memoria, está más cerca de 2.35000000000000008) continúa redondeando a 2,4. El redondeo realizado por estas funciones ahora también respeta el modo de redondeo de punto flotante establecido por [fesetround](fegetround-fesetround2.md). Anteriormente, el redondeo siempre escogió FE_TONEAREST comportamiento. Este cambio solo afecta a los programas compilados con Visual Studio 2019, versión 16,2 y versiones posteriores. Para usar el comportamiento de redondeo de punto flotante heredado, vincule con [legacy_stdio_float_rounding. obj](../link-options.md).

## <a name="example"></a>Ejemplo

```C
// crt_printf.c
// This program uses the printf and wprintf functions
// to produce formatted output.

#include <stdio.h>

int main( void )
{
   char     ch = 'h',
            *string = "computer";
   wchar_t  wch = L'w',
            *wstring = L"Unicode";
   int      count = -9234;
   double   fp = 251.7366;

   // Display integers
   printf( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  "
           "Unsigned: %u\n",
           count, count, count, count );

   // Display decimals
   printf( "Decimal %d as:\n   Hex: %Xh  "
           "C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   // Display in different radixes
   printf( "Digits 10 equal:\n   Hex: %i  "
           "Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   // Display characters
   printf("Characters in field (1):\n"
          "%10c%5hc%5C%5lc\n",
          ch, ch, wch, wch);
   wprintf(L"Characters in field (2):\n"
           L"%10C%5hc%5c%5lc\n",
           ch, ch, wch, wch);

   // Display strings
   printf("Strings in field (1):\n%25s\n"
          "%25.4hs\n   %S%25.3ls\n",
          string, string, wstring, wstring);
   wprintf(L"Strings in field (2):\n%25S\n"
           L"%25.4hs\n   %s%25.3ls\n",
           string, string, wstring, wstring);

   // Display real numbers
   printf("Real numbers:\n   %f %.2f %e %E\n",
          fp, fp, fp, fp );

   // Display pointer
   printf( "\nAddress as:   %p\n", &count);
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF3C
```

## <a name="see-also"></a>Consulte también:

[Sintaxis de especificación de formato: funciones printf y wprintf](../format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[Compatibilidad de punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Funciones de vprintf (](../../c-runtime-library/vprintf-functions.md)<br/>
[_set_output_format](../../c-runtime-library/set-output-format.md)<br/>
