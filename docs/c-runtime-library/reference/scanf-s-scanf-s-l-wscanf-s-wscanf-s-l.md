---
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 33
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b40d891c4148a92a3d2f0060401cd84b371d73
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*Argumento*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de campos que se han convertido y asignado correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error, o si se encuentra el carácter de final de archivo o el carácter de final de cadena en el primer intento de leer un carácter. Si *formato* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **scanf_s** y **wscanf_s** devolver **EOF** y establecer **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **scanf_s** función lee los datos del flujo de entrada estándar **stdin** y escribe los datos en la ubicación determinada por *argumento*. Cada *argumento* debe ser un puntero a una variable de un tipo que se corresponde con un especificador de tipo en *formato*. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

**wscanf_s** es una versión con caracteres anchos de **scanf_s**; el *formato* argumento pasado a **wscanf_s** es una cadena de caracteres anchos. **wscanf_s** y **scanf_s** se comportan exactamente igual si el flujo se abre en modo ANSI. **scanf_s** no admite actualmente la entrada desde un flujo UNICODE.

Las versiones de estas funciones que tienen la **_l** sufijo son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

A diferencia de **scanf** y **wscanf**, **scanf_s** y **wscanf_s** requieren que se pueden especificar para todos los parámetros de entrada del tipo eltamañodebúfer**c**, **C**, **s**, **S**, o los conjuntos de control que se incluyen en cadenas **[]**. El tamaño de búfer en caracteres se pasa como parámetro adicional inmediatamente después del puntero en el búfer o la variable. Por ejemplo, si está leyendo una cadena, el tamaño de búfer para esa cadena se pasa como se indica a continuación:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

El tamaño de búfer incluye el valor nulo final. Puede usar un campo de especificación de ancho para garantizar que el token que se lee se ajustará al búfer. Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.

> [!NOTE]
> El parámetro de tamaño es del tipo **sin signo**, no **size_t**. Usar una conversión estática para convertir un **size_t** valor **sin signo** configuraciones de compilación de 64 bits.

En el ejemplo siguiente se muestra que el parámetro de tamaño de búfer indica el número máximo de caracteres, no bytes. En la llamada a **wscanf_s**, el ancho de caracteres que se indica mediante el tipo de búfer no coincide con el ancho de caracteres que se indica mediante el especificador de formato.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

El **S** especificador de formato indica el uso del ancho de carácter que es "opuesto" al ancho predeterminado admitido por la función. El ancho de carácter es de un solo byte, pero la función admite caracteres de doble byte. En este ejemplo se lee una cadena de hasta 9 caracteres con ancho de un solo byte y los coloca en un búfer de caracteres con ancho de doble byte. Los caracteres se tratan como valores de un solo byte; los primeros dos caracteres se almacenan en `ws[0]`, los siguientes dos se almacenan en `ws[1]`, y así sucesivamente.

En el caso de los caracteres, un carácter individual puede leerse como se indica a continuación:

```C
char c;
scanf_s("%c", &c, 1);
```

Cuando se leen varios caracteres para cadenas que no tienen un valor nulo final, se usan enteros como especificación del ancho y el tamaño de búfer.

```C
char c[4];
scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Para obtener más información, vea [scanf (Especificación de ancho)](../../c-runtime-library/scanf-width-specification.md).

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

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
