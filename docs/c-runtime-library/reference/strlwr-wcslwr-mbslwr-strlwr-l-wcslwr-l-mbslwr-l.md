---
title: _strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l
ms.date: 4/2/2020
api_name:
- _strlwr_l
- _strlwr
- _wcslwr_l
- _mbslwr_l
- _wcslwr
- _mbslwr
- _o__mbslwr
- _o__mbslwr_l
- _o__strlwr
- _o__strlwr_l
- _o__wcslwr
- _o__wcslwr_l
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
- _strlwr
- wcslwr_l
- _ftcslwr
- mbslwr_l
- _mbslwr
- _wcslwr
- strlwr_l
- _tcslwr
- mbslwr
helpviewer_keywords:
- tcslwr function
- _strlwr function
- converting case
- string conversion [C++], case
- mbslwr function
- _strlwr_l function
- strlwr_l function
- _wcslwr function
- ftcslwr function
- strings [C++], case
- _tcslwr_l function
- _wcslwr_l function
- wcslwr_l function
- mbslwr_l function
- tcslwr_l function
- _tcslwr function
- converting case, CRT functions
- _ftcslwr function
- _mbslwr function
- case, converting
- strings [C++], converting case
- _mbslwr_l function
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
ms.openlocfilehash: 9ba2570ff02cf11cb5822666b5569fa88caf76b9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919942"
---
# <a name="_strlwr-_wcslwr-_mbslwr-_strlwr_l-_wcslwr_l-_mbslwr_l"></a>_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l

Convierte una cadena a minúsculas. Hay disponibles versiones más seguras de estas funciones; vea [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).

> [!IMPORTANT]
> **_mbslwr** y **_mbslwr_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *_strlwr(
   char * str
);
wchar_t *_wcslwr(
   wchar_t * str
);
unsigned char *_mbslwr(
   unsigned char * str
);
char *_strlwr_l(
   char * str,
   _locale_t locale
);
wchar_t *_wcslwr_l(
   wchar_t * str,
   _locale_t locale
);
unsigned char *_mbslwr_l(
   unsigned char * str,
   _locale_t locale
);
template <size_t size>
char *_strlwr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcslwr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbslwr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strlwr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcslwr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbslwr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*CAD*<br/>
Cadena terminada en NULL que se va a cambiar a minúsculas.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero a la cadena convertida. Dado que la modificación se hace en contexto, el puntero devuelto es el mismo que el puntero que se pasa como argumento de entrada. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Observaciones

La función **_strlwr** convierte las letras mayúsculas de *Str* a minúsculas, según lo determinado por el valor de la categoría **LC_CTYPE** de la configuración regional. Otros caracteres no resultan afectados. Para obtener más información sobre **LC_CTYPE**, vea [setlocale](setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo **_L** usan la configuración regional actual para su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_L** son idénticas, salvo que usan en su lugar la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Las funciones **_wcslwr** y **_mbslwr** son versiones de caracteres anchos y multibyte de **_strlwr**. El argumento y el valor devuelto de **_wcslwr** son cadenas de caracteres anchos; los de **_mbslwr** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

Si *Str* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones devuelven la cadena original y establecen **errno** en **EINVAL**.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr**|**_strlwr**|**_mbslwr**|**_wcslwr**|
|**_tcslwr_l**|**_strlwr_l**|**_mbslwr_l**|**_wcslwr_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strlwr**, **_strlwr_l**|\<string.h>|
|**_wcslwr**, **_wcslwr_l**|\<string.h> o \<wchar.h>|
|**_mbslwr**, **_mbslwr_l**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strlwr.c
// compile with: /W3
// This program uses _strlwr and _strupr to create
// uppercase and lowercase copies of a mixed-case string.
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The String to End All Strings!";
   char * copy1 = _strdup( string ); // make two copies
   char * copy2 = _strdup( string );

   _strlwr( copy1 ); // C4996
   // Note: _strlwr is deprecated; consider using _strlwr_s instead
   _strupr( copy2 ); // C4996
   // Note: _strupr is deprecated; consider using _strupr_s instead

   printf( "Mixed: %s\n", string );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>Consulte también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)<br/>
