---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
dev_langs:
- C++
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0014ea3c727db2a368123696c47df1eca6ba3bb4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418333"
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Realiza una comparación de cadenas sin distinción entre mayúsculas y minúsculas.

> [!IMPORTANT]
> **_mbsicmp** y **_mbsicmp_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*cadena1*, *cadena2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación de *string1* a *string2* como se indica a continuación.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|*cadena1* menor *cadena2*|
|0|*cadena1* idéntico al *cadena2*|
|> 0|*cadena1* mayor *cadena2*|

Produce un error, **_mbsicmp** devuelve **_NLSCMPERROR**, que se define en \<string.h > y \<mbstring.h >.

## <a name="remarks"></a>Comentarios

El **_stricmp** función ordinal compara *string1* y *string2* después de convertir cada carácter a minúsculas y devuelve un valor que indica su relación. **_stricmp** difiere de **_stricoll** en que la **_stricmp** comparación solo se ve afectada por **LC_CTYPE**, que determina qué caracteres van superiores y minúsculas. El **_stricoll** función compara las cadenas según las el **LC_CTYPE** y **LC_COLLATE** categorías de la configuración regional, que incluye el caso y la intercalación orden. Para obtener más información sobre la **LC_COLLATE** categoría, vea [setlocale](setlocale-wsetlocale.md) y [categorías de configuración regional](../../c-runtime-library/locale-categories.md). Las versiones de estas funciones sin el **_l** sufijo usan la configuración regional actual de comportamiento dependiente de la configuración regional. Las versiones con el sufijo son idénticas, salvo que usan el parámetro de configuración regional que se pasa. Si no se ha establecido la configuración regional, se utiliza la configuración regional de C. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** es equivalente a **_strcmpi**. Pueden usarse indistintamente pero **_stricmp** es el estándar preferido.

El **_strcmpi** función es equivalente a **_stricmp** y se proporciona por compatibilidad con versiones anteriores.

Dado que **_stricmp** comparaciones de minúsculas, se podrían producir un comportamiento inesperado.

Para mostrar cuándo caso la conversión de **_stricmp** influye en el resultado de una comparación, se supone que tiene las dos cadenas JOHNSTON y JOHN_HENRY. La cadena JOHN_HENRY se considera menor que JOHNSTON porque el carácter "_" tiene un valor ASCII menor que una S minúscula. De hecho, cualquier carácter que tenga un valor ASCII comprendido entre 91 y 96 se considerará menor que cualquier letra.

Si el [strcmp](strcmp-wcscmp-mbscmp.md) función se utiliza en lugar de **_stricmp**, JOHN_HENRY será mayor que JOHNSTON.

**_wcsicmp** y **_mbsicmp** son versiones de caracteres multibyte y anchos de **_stricmp**. Los argumentos y el valor devuelto de **_wcsicmp** son caracteres anchos cadenas; los de **_mbsicmp** son cadenas de caracteres multibyte. **_mbsicmp** reconoce las secuencias de caracteres multibyte según la página de códigos multibyte actual y devuelve **_NLSCMPERROR** produce un error. Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md). Estas tres funciones se comportan exactamente igual.

**_wcsicmp** y **wcscmp** se comportan exactamente igual, salvo que **wcscmp** no convierte los argumentos en minúsculas antes de compararlos. **_mbsicmp** y **_mbscmp** se comportan exactamente igual, salvo que **_mbscmp** no convierte los argumentos en minúsculas antes de compararlos.

Debe llamar a [setlocale](setlocale-wsetlocale.md) para **_wcsicmp** para trabajar con caracteres de Latín 1. La configuración regional de C está activada de forma predeterminada, de modo que, por ejemplo, ä no se considera igual a Ä. Llame a **setlocale** con cualquier configuración regional que no sea la configuración regional de C antes de llamar a **_wcsicmp**. El ejemplo siguiente se muestra cómo **_wcsicmp** es sensible a la configuración regional:

```C
// crt_stricmp_locale.c
#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

Una alternativa consiste en llamar a [_create_locale, _wcreate_locale](create-locale-wcreate-locale.md) y pase el objeto de configuración regional devuelto como un parámetro a **_wcsicmp_l**.

Todas estas funciones validan sus parámetros. Si el valor *string1* o *string2* son punteros nulos, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y establecer **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_stricmp**, **_stricmp_l**|\<string.h>|
|**_wcsicmp**, **_wcsicmp_l**|\<string.h> o \<wchar.h>|
|**_mbsicmp**, **_mbsicmp_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_stricmp.c

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
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
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
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
