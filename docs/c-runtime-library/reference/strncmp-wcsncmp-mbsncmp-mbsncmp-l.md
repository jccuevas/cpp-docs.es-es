---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- ntdll.dll
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
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: deae95f8cf7d538dfe22ebbe0e86524765d9d234
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919313"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Compara dos cadenas hasta el número especificado de caracteres.

> [!IMPORTANT]
> **_mbsncmp** y **_mbsncmp_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*cadena1*, *cadena2*<br/>
Cadenas que se van a comparar.

*count*<br/>
Número de caracteres que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación de las subcadenas de *string1* y *String2* de la siguiente manera.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|*cadena1* subcadena inferior a *cadena2* subcadena|
|0|la subcadena *cadena1* es idéntica a la subcadena *cadena2*|
|> 0|la subcadena *cadena1* es mayor que *cadena2* subcadena|

En un error de validación de parámetros, **_mbsncmp** y **_mbsncmp_l** devuelven **_NLSCMPERROR**, \<que se define en string \<. h> y mbstring. h>.

## <a name="remarks"></a>Observaciones

La función **strncmp** realiza una comparación ordinal de, como máximo, los primeros caracteres de *recuento* de *cadena1* y *cadena2* , y devuelve un valor que indica la relación entre las subcadenas. **strncmp** es una versión de **_strnicmp**que distingue mayúsculas de minúsculas. **wcsncmp** y **_mbsncmp** son versiones con distinción de mayúsculas y minúsculas de **_wcsnicmp** y **_mbsnicmp**.

**wcsncmp** y **_mbsncmp** son versiones de caracteres anchos y multibyte de **strncmp**. Los argumentos de **wcsncmp** son cadenas de caracteres anchos; los de **_mbsncmp** son cadenas de caracteres multibyte. **_mbsncmp** reconoce las secuencias de caracteres multibyte según una página de códigos multibyte y devuelve **_NLSCMPERROR** en un error.

Además, **_mbsncmp** y **_mbsncmp_l** validar parámetros. Si *string1* o *cadena2* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_mbsncmp** y **_mbsncmp_l** devuelven **_NLSCMPERROR** y establecen **errno** en **EINVAL**. **strncmp** y **wcsncmp** no validan sus parámetros. Por lo demás, estas funciones se comportan exactamente igual.

El comportamiento de comparación de **_mbsncmp** y **_mbsncmp_l** se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. Esta opción controla la detección de los bytes iniciales y finales de caracteres multibyte. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md). La función **_mbsncmp** usa la configuración regional actual para este comportamiento dependiente de la configuración regional. La función **_mbsncmp_l** es idéntica, salvo que usa el parámetro *locale* en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md). Si la configuración regional es una configuración regional de un solo byte, el comportamiento de estas funciones es idéntico a **strncmp**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Se asigna a una macro o una función insertada|**_mbsncmp**|Se asigna a una macro o una función insertada|
|**no aplicable**|**no aplicable**|**_mbsncmp_l**|**no aplicable**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> o \<wchar.h>|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>Consulte también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[Funciones de strcoll (](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
