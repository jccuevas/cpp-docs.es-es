---
title: _snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _snprintf_s
- _snprintf_s_l
- _snwprintf_s
- _snwprintf_s_l
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
- _snwprintf_s_l
- _sntprintf_s_l
- snprintf_s_l
- _snprintf_s_l
- _sntprintf_s
- _snprintf_s
- snprintf_s
- _snwprintf_s
- snwprintf_s_l
- snwprintf_s
- sntprintf_s
- sntprintf_s_l
dev_langs:
- C++
helpviewer_keywords:
- _snprintf_s_l function
- _snwprintf_s_l function
- _sntprintf_s_l function
- snwprintf_s_l function
- snprintf_s function
- _snprintf_s function
- snprintf_s_l function
- _sntprintf_s function
- sntprintf_s_l function
- sntprintf_s function
- snwprintf_s function
- _snwprintf_s function
- formatted text [C++]
ms.assetid: 9336ab86-13e5-4a29-a3cd-074adfee6891
caps.latest.revision: 32
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51962d696583023f0cd5fc5b0def22f05d87b9fb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="snprintfs-snprintfsl-snwprintfs-snwprintfsl"></a>_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l

Escribe datos con formato en una cadena. Se trata de versiones de [snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int _snprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento del resultado.

*sizeOfBuffer*<br/>
Tamaño de la ubicación de almacenamiento para la salida. Cambio de tamaño en **bytes** para **_snprintf_s** o tamaño en **palabras** para **_snwprintf_s**.

*count*<br/>
Número máximo de caracteres que se pueden almacenar o [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Cadena de control de formato.

*Argumento*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_snprintf_s** devuelve el número de caracteres almacenados en *búfer*, sin contar el carácter nulo de terminación. **_snwprintf_s** devuelve el número de caracteres anchos almacenados en *búfer*, sin contar el carácter ancho final null.

Si supera el almacenamiento necesario para almacenar los datos y un carácter nulo final *sizeOfBuffer*, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución continúa después del controlador de parámetros no válidos, estas funciones establecen *búfer* en una cadena vacía, establecen **errno** a **ERANGE**y devuelven -1.

Si *búfer* o *formato* es un **NULL** puntero, o si *recuento* es menor o igual a cero, se invoca el controlador de parámetros no válidos. Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devuelven -1.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_snprintf_s** formatos de función y almacenes de *recuento* caracteres o menos en *búfer* y anexa un carácter nulo. Cada argumento (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. El formato es coherente con la **printf** familia de funciones; vea [sintaxis de especificación de formato: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

Si *recuento* es [_TRUNCATE](../../c-runtime-library/truncate.md), a continuación, **_snprintf_s** escrituras como gran parte de la cadena como caben en *búfer* dejando espacio para un terminación null. Si toda la cadena (con valor nulo final) cabe *búfer*, a continuación, **_snprintf_s** devuelve el número de caracteres escrito (sin incluir el carácter null final); en caso contrario, **_snprintf_s**  devuelve -1 para indicar que el truncamiento se produjo.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

**_snwprintf_s** es una versión con caracteres anchos de **_snprintf_s**; los argumentos de puntero a **_snwprintf_s** son cadenas de caracteres anchos. Detección de errores en de codificación **_snwprintf_s** pueden diferir de la de **_snprintf_s**. **_snwprintf_s**, como **swprintf_s**, escribe la salida a una cadena en lugar de a un destino de tipo **archivo**.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf_s**|**_snprintf_s**|**_snprintf_s**|**_snwprintf_s**|
|**_sntprintf_s_l**|**_snprintf_s_l**|**_snprintf_s_l**|**_snwprintf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_snprintf_s**, **_snprintf_s_l**|\<stdio.h>|
|**_snwprintf_s**, **_snwprintf_s_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_snprintf_s.cpp
// compile with: /MTd

// These #defines enable secure template overloads
// (see last part of Examples() below)
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <crtdbg.h>  // For _CrtSetReportMode
#include <errno.h>

// This example uses a 10-byte destination buffer.

int snprintf_s_tester( const char * fmt, int x, size_t count )
{
   char dest[10];

   printf( "\n" );

   if ( count == _TRUNCATE )
      printf( "%zd-byte buffer; truncation semantics\n",
               _countof(dest) );
   else
      printf( "count = %zd; %zd-byte buffer\n",
               count, _countof(dest) );

   int ret = _snprintf_s( dest, _countof(dest), count, fmt, x );

   printf( "    new contents of dest: '%s'\n", dest );

   return ret;
}

void Examples()
{
   // formatted output string is 9 characters long: "<<<123>>>"
   snprintf_s_tester( "<<<%d>>>", 121, 8 );
   snprintf_s_tester( "<<<%d>>>", 121, 9 );
   snprintf_s_tester( "<<<%d>>>", 121, 10 );

   printf( "\nDestination buffer too small:\n" );

   snprintf_s_tester( "<<<%d>>>", 1221, 10 );

   printf( "\nTruncation examples:\n" );

   int ret = snprintf_s_tester( "<<<%d>>>", 1221, _TRUNCATE );
   printf( "    truncation %s occur\n", ret == -1 ? "did"
                                                  : "did not" );

   ret = snprintf_s_tester( "<<<%d>>>", 121, _TRUNCATE );
   printf( "    truncation %s occur\n", ret == -1 ? "did"
                                                  : "did not" );
   printf( "\nSecure template overload example:\n" );

   char dest[10];
   _snprintf( dest, 10, "<<<%d>>>", 12321 );
   // With secure template overloads enabled (see #defines
   // at top of file), the preceding line is replaced by
   //    _snprintf_s( dest, _countof(dest), 10, "<<<%d>>>", 12345 );
   // Instead of causing a buffer overrun, _snprintf_s invokes
   // the invalid parameter handler.
   // If secure template overloads were disabled, _snprintf would
   // write 10 characters and overrun the dest buffer.
   printf( "    new contents of dest: '%s'\n", dest );
}

void myInvalidParameterHandler(
   const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);
}

int main( void )
{
   _invalid_parameter_handler oldHandler, newHandler;

   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);
   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   Examples();
}
```

```Output

count = 8; 10-byte buffer
    new contents of dest: '<<<121>>'

count = 9; 10-byte buffer
    new contents of dest: '<<<121>>>'

count = 10; 10-byte buffer
    new contents of dest: '<<<121>>>'

Destination buffer too small:

count = 10; 10-byte buffer
Invalid parameter handler invoked: ("Buffer too small", 0)
    new contents of dest: ''

Truncation examples:

10-byte buffer; truncation semantics
    new contents of dest: '<<<1221>>'
    truncation did occur

10-byte buffer; truncation semantics
    new contents of dest: '<<<121>>>'
    truncation did not occur

Secure template overload example:
Invalid parameter handler invoked: ("Buffer too small", 0)
    new contents of dest: ''
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf (funciones)](../../c-runtime-library/vprintf-functions.md)<br/>
