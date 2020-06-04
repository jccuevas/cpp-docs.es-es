---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
ms.openlocfilehash: e869f9e0d4fa87c87878ffea987e4b6d85a75616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948874"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l

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

Devuelve el número de campos convertidos y asignados correctamente. El valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error, o si se encuentra el carácter de final de archivo o el carácter de final de cadena en el primer intento de leer un carácter. Si *Format* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **scanf_s** y **wscanf_s** devuelven **EOF** y establecen **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **scanf_s** Lee los datos del flujo de entrada estándar, **stdin**, y los escribe en el *argumento*. Cada *argumento* debe ser un puntero a un tipo de variable que se corresponda con el especificador de tipo en *formato*. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

**wscanf_s** es una versión con caracteres anchos de **scanf_s**; el argumento de *formato* para **wscanf_s** es una cadena de caracteres anchos. **wscanf_s** y **scanf_s** se comportan exactamente igual si la secuencia se abre en modo ANSI. **scanf_s** no admite actualmente la entrada desde un flujo Unicode.

Las versiones de estas funciones que tienen el sufijo **_L** son idénticas, salvo que usan el parámetro *locale* en lugar de la configuración regional del subproceso actual.

A diferencia de **scanf** y **wscanf**, **scanf_s** y **wscanf_s** requieren que especifique tamaños de búfer para algunos parámetros. Especifique los tamaños de todos los parámetros **c**, **c**, **s**, **s**o String Control set **[]** . El tamaño de búfer en caracteres se pasa como parámetro adicional. Sigue inmediatamente al puntero en el búfer o la variable. Por ejemplo, si está leyendo una cadena, el tamaño de búfer para esa cadena se pasa como se indica a continuación:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

El tamaño de búfer incluye el terminal null. Puede usar un campo de especificación de ancho para asegurarse de que el token que se lee en cabe en el búfer. Cuando un token es demasiado grande para ajustarse, no se escribe nada en el búfer a menos que haya una especificación de ancho.

> [!NOTE]
> El parámetro de tamaño es de tipo sin **signo**, no **size_t**. Use una conversión estática para convertir un valor **size_t** en **sin signo** para configuraciones de compilación de 64 bits.

El parámetro de tamaño de búfer describe el número máximo de caracteres, no los bytes. En este ejemplo, el ancho del tipo de búfer no coincide con el ancho del especificador de formato.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

El especificador de formato **S** significa usar el ancho de caracteres "opuesto" al ancho predeterminado admitido por la función. El ancho de carácter es de un solo byte, pero la función admite caracteres de doble byte. En este ejemplo se lee una cadena de hasta nueve caracteres de un solo byte y se colocan en un búfer de caracteres de ancho doble byte. Los caracteres se tratan como valores de un solo byte; los primeros dos caracteres se almacenan en `ws[0]`, los siguientes dos se almacenan en `ws[1]`, y así sucesivamente.

En este ejemplo se lee un solo carácter:

```C
char c;
scanf_s("%c", &c, 1);
```

Cuando se leen varios caracteres para cadenas que no terminan en null, se usan enteros para la especificación de ancho y el tamaño de búfer.

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

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). El flujo estándar controla **stdin**, **stdout**y **stderr** deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
