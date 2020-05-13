---
title: strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l
ms.date: 4/2/2020
api_name:
- strncat
- _strncat_l
- _mbsncat
- _mbsncat_l
- wcsncat
- wcsncat_l
- _o__mbsncat
- _o__mbsncat_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsncat_l
- _wcsncat_l
- _tcsnccat_l
- _mbsncat
- _strncat_l
- strncat
- _tcsnccat
- _mbsncat_l
- _ftcsncat
- wcsncat
- _tcsncat
helpviewer_keywords:
- concatenating strings
- ftcsncat function
- tcsncat_l function
- _tcsnccat_l function
- _tcsncat function
- strncat function
- _ftcsncat function
- mbsncat function
- mbsncat_l function
- strings [C++], appending
- wcsncat function
- tcsnccat function
- tcsnccat_l function
- _tcsnccat function
- string concatenation [C++]
- appending strings
- characters [C++], appending to strings
- _mbsncat function
- _tcsncat_l function
- _mbsncat_l function
- tcsncat function
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
ms.openlocfilehash: 98f13967d8abbe079934d0c09ab71c5e279d2b7f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918151"
---
# <a name="strncat-_strncat_l-wcsncat-_wcsncat_l-_mbsncat-_mbsncat_l"></a>strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l

Anexa caracteres de una cadena. Hay disponibles versiones más seguras de estas funciones; vea [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md).

> [!IMPORTANT]
> **_mbsncat** y **_mbsncat_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *strncat(
   char *strDest,
   const char *strSource,
   size_t count
);
wchar_t *wcsncat(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
unsigned char *_mbsncat(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count
);
unsigned char *_mbsncat_l(
   unsigned char *strDest,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
char *strncat(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
wchar_t *wcsncat(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsncat_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Cadena de destino terminada en NULL.

*strSource*<br/>
Cadena de origen terminada en NULL.

*count*<br/>
Número de caracteres que se van a anexar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la cadena de destino. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Observaciones

La función **strncat** anexa, como máximo, los primeros caracteres de *recuento* de *strSource* a *strDest*. El carácter inicial de *strSource* sobrescribe el carácter nulo de terminación de *strDest*. Si aparece un carácter nulo en *strSource* antes de que se anexen los caracteres de *recuento* , **strncat** anexa todos los caracteres de *strSource*, hasta el carácter nulo. Si el *recuento* es mayor que la longitud de *strSource*, se usa la longitud de *strSource* en lugar del *recuento*. En todos los casos, la cadena resultante se termina con un carácter nulo. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

> [!IMPORTANT]
> **strncat** no comprueba si hay espacio suficiente en *strDest*; por lo tanto, es una posible causa de saturaciones del búfer. Tenga en cuenta que el *recuento* limita el número de caracteres anexados. no es un límite en cuanto al tamaño de *strDest*. Observe el ejemplo siguiente. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

**wcsncat** y **_mbsncat** son versiones de caracteres anchos y multibyte de **strncat**. Los argumentos de cadena y el valor devuelto de **wcsncat** son cadenas de caracteres anchos; los de **_mbsncat** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, estas funciones tienen sobrecargas de plantilla. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncat**|**strncat**|**_mbsnbcat**|**wcsncat**|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

> [!NOTE]
> **_strncat_l** y **_wcsncat_l** no tienen ninguna dependencia de la configuración regional y no están diseñados para llamarse directamente. Se proporcionan para uso interno de **_tcsncat_l**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strncat**|\<string.h>|
|**wcsncat**|\<string.h> o \<wchar.h>|
|**_mbsncat**|\<mbstring.h>|
|**_mbsncat_l**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strncat.c
// Use strcat and strncat to append to a string.
#include <stdlib.h>

#define MAXSTRINGLEN 39

char string[MAXSTRINGLEN+1];
// or char *string = malloc(MAXSTRINGLEN+1);

void BadAppend( char suffix[], int n )
{
   strncat( string, suffix, n );
}

void GoodAppend( char suffix[], size_t n )
{
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );
}

int main( void )
{
   string[0] = '\0';
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   BadAppend( "Extra text to add to the string...", 20 );
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );

   strcpy( string, "This is the initial string!" );
   // concatenate up to 20 characters...
   GoodAppend( "Extra text to add to the string...", 20 );
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );
}
```

### <a name="output"></a>Output

```Output
string can hold up to 39 characters
After BadAppend :  This is the initial string!Extra text to add to (47 chars)
After GoodAppend:  This is the initial string!Extra text t (39 chars)
```

Tenga en cuenta que **BadAppend** causó una saturación del búfer.

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
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
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
