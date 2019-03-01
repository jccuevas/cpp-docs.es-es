---
title: strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l
ms.date: 11/04/2016
apiname:
- _wcsncat_s_l
- wcsncat_s
- _mbsncat_s_l
- _mbsncat_s
- strncat_s
- _strncat_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- strncat_s_l
- _mbsncat_s_l
- _tcsncat_s
- wcsncat_s
- wcsncat_s_l
- strncat_s
- _mbsncat_s
- _tcsncat_s_l
helpviewer_keywords:
- concatenating strings
- _mbsncat_s function
- mbsncat_s_l function
- _tcsncat_s function
- _mbsncat_s_l function
- strncat_s function
- strings [C++], appending
- strncat_s_l function
- string concatenation [C++]
- _tcsncat_s_l function
- wcsncat_s function
- appending strings
- wcsncat_s_l function
- mbsncat_s function
ms.assetid: de77eca2-4d9c-4e66-abf2-a95fefc21e5a
ms.openlocfilehash: 6651bb6ac405ed51945f021e8d1e19f1db05d5e7
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210944"
---
# <a name="strncats-strncatsl-wcsncats-wcsncatsl-mbsncats-mbsncatsl"></a>strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l

Anexa caracteres a una cadena. Estas versiones de [strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbsncat_s** y **_mbsncat_s_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t strncat_s(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count
);
errno_t _strncat_s_l(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count,
   _locale_t locale
);
errno_t wcsncat_s(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count
);
errno_t _wcsncat_s_l(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
errno_t _mbsncat_s(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count
);
errno_t _mbsncat_s_l(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t strncat_s(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _strncat_s_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t wcsncat_s(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _wcsncat_s_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbsncat_s(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsncat_s_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Cadena de destino terminada en NULL.

*numberOfElements*<br/>
Tamaño del búfer de destino.

*strSource*<br/>
Cadena de origen terminada en NULL.

*count*<br/>
Número de caracteres que se van a anexar o [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*strDestination*|*numberOfElements*|*strSource*|Valor devuelto|Contenido de *strDestination*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL** o sin terminar|any|any|**EINVAL**|no modificado|
|any|any|**NULL**|**EINVAL**|no modificado|
|any|0, o demasiado pequeño|any|**ERANGE**|no modificado|

## <a name="remarks"></a>Comentarios

Estas funciones intentan anexar los primeros *d.* caracteres de *strSource* al final de *strDest*, donde *d.* es el menor de *recuento* y la longitud de *strSource*. Si los anexa *d.* se ajusten a caracteres *strDest* (cuyo tamaño se da como *numberOfElements*) y queda espacio para un terminador nulo, entonces esos caracteres adicionales. se anexan, empezando en el original terminación null de *strDest*, y un carácter nulo final nueva se anexa; en caso contrario, *strDest*[0] se establece en el carácter nulo y el parámetro no válido se invoca el controlador, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Existe una excepción al comportamiento anterior. Si *recuento* es [_TRUNCATE](../../c-runtime-library/truncate.md) , la parte de *strSource* que quepa se anexa a *strDest* , siempre dejando espacio para anexar un terminación null.

Por ejemplo,

```C
char dst[5];
strncpy_s(dst, _countof(dst), "12", 2);
strncat_s(dst, _countof(dst), "34567", 3);
```

significa que, te pedimos **strncat_s** que anexe tres caracteres a dos caracteres en un búfer de cinco caracteres; esto no quedaría espacio para el terminador nulo, por lo tanto, **strncat_s** ceros a la cadena y llama al controlador de parámetros no válidos.

Si se necesita comportamiento de truncamiento, utilice **_TRUNCATE** o ajustar el *tamaño* parámetro según corresponda:

```C
strncat_s(dst, _countof(dst), "34567", _TRUNCATE);
```

o

```C
strncat_s(dst, _countof(dst), "34567", _countof(dst)-strlen(dst)-1);
```

En todos los casos, la cadena resultante se termina con un carácter nulo. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

Si *strSource* o *strDest* es **NULL**, o es *numberOfElements* es cero, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, la función devuelve **EINVAL** sin modificar sus parámetros.

**wcsncat_s** y **_mbsncat_s** son versiones de caracteres anchos y caracteres multibyte de **strncat_s**. Los argumentos de cadena y el valor devuelto de **wcsncat_s** son caracteres anchos cadenas; los de **_mbsncat_s** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncat_s**|**strncat_s**|**_mbsnbcat_s**|**wcsncat_s**|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

**_strncat_s_l** y **_wcsncat_s_l** no que dependen de la configuración regional; se proporcionan solo para **_tcsncat_s_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strncat_s**|\<string.h>|
|**wcsncat_s**|\<string.h> o \<wchar.h>|
|**_mbsncat_s**, **_mbsncat_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```cpp
// crt_strncat_s.cpp
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

errno_t strncat_s_tester( const char * initialDest,
                          const char * src,
                          int count )
{
   char dest[10];
   strcpy_s( dest, _countof(dest), initialDest );

   printf_s( "\n" );

   if ( count == _TRUNCATE )
      printf_s( "Appending '%s' to %d-byte buffer dest with truncation semantics\n",
               src, _countof(dest) );
   else
      printf_s( "Appending %d chars of '%s' to %d-byte buffer dest\n",
              count, src, _countof(dest) );

   printf_s( "    old contents of dest: '%s'\n", dest );

   errno_t err = strncat_s( dest, _countof(dest), src, count );

   printf_s( "    new contents of dest: '%s'\n", dest );

   return err;
}

void Examples()
{
   strncat_s_tester( "hi ", "there", 4 );
   strncat_s_tester( "hi ", "there", 5 );
   strncat_s_tester( "hi ", "there", 6 );

   printf_s( "\nDestination buffer too small:\n" );
   strncat_s_tester( "hello ", "there", 4 );

   printf_s( "\nTruncation examples:\n" );

   errno_t err = strncat_s_tester( "hello ", "there", _TRUNCATE );
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   err = strncat_s_tester( "hello ", "!", _TRUNCATE );
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   printf_s( "\nSecure template overload example:\n" );

   char dest[10] = "cats and ";
   strncat( dest, "dachshunds", 15 );
   // With secure template overloads enabled (see #define
   // at top of file), the preceding line is replaced by
   //    strncat_s( dest, _countof(dest), "dachshunds", 15 );
   // Instead of causing a buffer overrun, strncat_s invokes
   // the invalid parameter handler.
   // If secure template overloads were disabled, strncat would
   // append "dachshunds" and overrun the dest buffer.
   printf_s( "    new contents of dest: '%s'\n", dest );
}

void myInvalidParameterHandler(
   const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf_s(L"Invalid parameter handler invoked: %s\n", expression);
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
Appending 4 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi ther'

Appending 5 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi there'

Appending 6 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi there'

Destination buffer too small:

Appending 4 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hello '
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''

Truncation examples:

Appending 'there' to 10-byte buffer dest with truncation semantics
    old contents of dest: 'hello '
    new contents of dest: 'hello the'
    truncation did occur

Appending '!' to 10-byte buffer dest with truncation semantics
    old contents of dest: 'hello '
    new contents of dest: 'hello !'
    truncation did not occur

Secure template overload example:
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
