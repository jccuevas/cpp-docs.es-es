---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 16bb294f7bbdc0b95b59b845d7b714f823f9d962
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357284"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Compara cadenas.

> [!IMPORTANT]
> **_mbscmp** y **_mbscmp_l** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*string1*, *string2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto para cada una de estas funciones indica la relación ordinal de *string1* a *string2*.

|Value|Relación de string1 y string2|
|-----------|----------------------------------------|
|< 0|*string1* es menor que *string2*|
|0|*string1* es idéntico a *string2*|
|> 0|*string1* es mayor que *string2*|

En un error de validación de parámetros, **_mbscmp** y \< **_mbscmp_l** devuelven **_NLSCMPERROR**, que se define en \<> string.h y mbstring.h>.

## <a name="remarks"></a>Observaciones

La función **strcmp** realiza una comparación ordinal de *string1* y *string2* y devuelve un valor que indica su relación. **wcscmp** y **_mbscmp** son, respectivamente, versiones de caracteres anchos y multibyte de **strcmp**. **_mbscmp** reconoce las secuencias de caracteres multibyte según la página de códigos multibyte actual y devuelve **_NLSCMPERROR** en un error. **_mbscmp_l** tiene el mismo comportamiento, pero usa el parámetro de configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md). Además, si *string1* o *string2* es un puntero nulo, **_mbscmp** invoca el controlador de parámetros no válidos, como se describe en validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_mbscmp** y **_mbscmp_l** devuelven **_NLSCMPERROR** y **establecen errno** en **EINVAL**. **strcmp** y **wcscmp** no validan sus parámetros. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Las funciones **strcmp** difieren de las funciones **strcoll** en que las comparaciones **de strcmp** son ordinales y no se ven afectadas por la configuración regional. **strcoll** compara las cadenas lexicográficamente mediante la categoría **LC_COLLATE** de la configuración regional actual. Para obtener más información acerca de la categoría **LC_COLLATE,** vea [setlocale, _wsetlocale](setlocale-wsetlocale.md).

En la configuración regional "C", el orden de los caracteres del juego de caracteres (juego de caracteres ASCII) es el mismo que en los caracteres lexicográficos. Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico. Por ejemplo, en algunas configuraciones regionales europeas el carácter “a” (valor 0x61) precede el carácter “ä” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.

En las configuraciones regionales para las que el juego de caracteres y el orden de caracteres lexicográficos difieren, puede utilizar **strcoll** en lugar de **strcmp** para la comparación lexicográfica de cadenas. Como alternativa, puede usar **strxfrm** en las cadenas originales y, a continuación, usar **strcmp** en las cadenas resultantes.

Las funciones **strcmp** distinguen mayúsculas de minúsculas. stricmp , ** \_wcsicmp**y ** \_mbsicmp** comparan cadenas convirtiéndolas primero en sus formas minúsculas. ** \_** Dos cadenas que contienen caracteres que se encuentran entre 'Z' y\\'a' en la tabla ASCII ('[', ' ', ']', ''', '_', y '\`') se comparan de manera diferente, dependiendo de su caso. Por ejemplo, las dos cadenas "ABCDE" y "ABCD" se comparan de una manera si la comparación está en minúsculas ("abcde" > "abcd-") y, por el contrario ("ABCDE" < "ABCD)") si la comparación está en mayúsculas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> o \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
