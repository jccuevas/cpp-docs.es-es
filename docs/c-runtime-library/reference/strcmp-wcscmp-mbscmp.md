---
title: strcmp, wcscmp, _mbscmp
ms.date: 11/04/2016
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscmp
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
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: b7d8614fffc96a600c0d1f92b85503259cfc5cbb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600530"
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp

Compara cadenas.

> [!IMPORTANT]
> **_mbscmp** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
```

### <a name="parameters"></a>Parámetros

*cadena1*, *cadena2*<br/>
Cadenas terminadas en NULL que se van a comparar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto para cada una de estas funciones indica la relación ordinal de *string1* a *cadena2*.

|Valor|Relación de string1 y string2|
|-----------|----------------------------------------|
|< 0|*cadena1* es menor que *cadena2*|
|0|*cadena1* es idéntico al *cadena2*|
|> 0|*cadena1* es mayor que *cadena2*|

Un error de validación de parámetros, **_mbscmp** devuelve **_NLSCMPERROR**, que se define en \<string.h > y \<mbstring.h >.

## <a name="remarks"></a>Comentarios

El **strcmp** función realiza una comparación ordinal de *string1* y *cadena2* y devuelve un valor que indica su relación. **wcscmp** y **_mbscmp** son, respectivamente, versiones de caracteres anchos y caracteres multibyte de **strcmp**. **_mbscmp** reconoce secuencias de caracteres multibyte según la página de códigos multibyte actual y devuelve **_NLSCMPERROR** produce un error. Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md). Además, si *string1* o *cadena2* es un puntero nulo, **_mbscmp** invoca el controlador de parámetros no válidos, tal y como se describe en [devalidacióndeparámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_mbscmp** devuelve **_NLSCMPERROR** y establece **errno** a **EINVAL**. **strcmp** y **wcscmp** no validan sus parámetros. Estas tres funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

El **strcmp** funciones se diferencian de las **strcoll** funciones en el que **strcmp** comparaciones son ordinales y no se ven afectadas por la configuración regional. **strcoll** compara las cadenas de manera lexicográfica usando la **LC_COLLATE** categoría de la configuración regional actual. Para obtener más información sobre la **LC_COLLATE** categoría, vea [setlocale, _wsetlocale](setlocale-wsetlocale.md).

En la configuración regional "C", el orden de los caracteres del juego de caracteres (juego de caracteres ASCII) es el mismo que en los caracteres lexicográficos. Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico. Por ejemplo, en algunas configuraciones regionales europeas el carácter “a” (valor 0x61) precede el carácter “ä” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.

En las configuraciones regionales para el que el juego de caracteres y el orden lexicográfico de los caracteres son diferentes, puede usar **strcoll** en lugar de **strcmp** para la comparación lexicográfica de cadenas. Como alternativa, puede usar **strxfrm** de las cadenas originales y luego usar **strcmp** en las cadenas resultantes.

El **strcmp** funciones distinguen mayúsculas de minúsculas. **_stricmp**, **_wcsicmp**, y **_mbsicmp** comparan cadenas convirtiéndolas primero en su forma minúscula. Dos cadenas que contienen caracteres que se encuentran entre la 'Z' y 'a' en la tabla ASCII ('[','\\', ']', ' ^', '_' y '\`') comparan de forma diferente, dependiendo de si son mayúsculas o minúsculas. Por ejemplo, las dos cadenas "ABCDE" y "ABCD ^" comparan de un modo si la comparación es minúscula ("abcde" > "abcd ^") y la otra manera ("ABCDE" < "ABCD ^") si la comparación es mayúscula.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> o \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
