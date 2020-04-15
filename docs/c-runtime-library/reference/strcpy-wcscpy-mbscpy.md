---
title: strcpy, wcscpy, _mbscpy
ms.date: 4/2/2020
api_name:
- strcpy
- wcscpy
- _mbscpy
- _o_wcscpy
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscpy
- _ftcscpy
- wcscpy
- _tcscpy
- strcpy
helpviewer_keywords:
- strcpy function
- tcscpy function
- ftcscpy function
- mbscpy function
- wcscpy function
- copying strings
- strings [C++], copying
- _tcscpy function
- _ftcscpy function
- _mbscpy function
ms.assetid: f97a4f81-e9ee-4f15-888a-0fa5d7094c5a
ms.openlocfilehash: 166d44c32a593ad9f32fcd19c56747bfaf4b5d0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359190"
---
# <a name="strcpy-wcscpy-_mbscpy"></a>strcpy, wcscpy, _mbscpy

Copia una cadena. Hay disponibles versiones más seguras de estas funciones; vea [strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md).

> [!IMPORTANT]
> **_mbscpy** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *strcpy(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscpy(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscpy(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcpy(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscpy(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscpy(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDestination*<br/>
Cadena de destino.

*strSource*<br/>
Cadena de origen terminada en NULL.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve la cadena de destino. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Observaciones

La función **strcpy** copia *strSource*, incluido el carácter nulo de terminación, en la ubicación especificada por *strDestination*. El comportamiento de **strcpy** es indefinido si las cadenas de origen y destino se superponen.

> [!IMPORTANT]
> Dado que **strcpy** no comprueba si hay suficiente espacio en *strDestination* antes de copiar *strSource*, es una posible causa de saturaciones de búfer. Por tanto, es recomendable usar la propiedad [strcpy_s](strcpy-s-wcscpy-s-mbscpy-s.md) en su lugar.

**wcscpy** y **_mbscpy** son, respectivamente, versiones de caracteres anchos y multibyte de **strcpy**. Los argumentos y el valor devuelto de **wcscpy** son cadenas de caracteres anchos; las de **_mbscpy** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy**|**strcpy**|**_mbscpy**|**wcscpy**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcpy**|\<string.h>|
|**wcscpy**|\<string.h> o \<wchar.h>|
|**_mbscpy**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strcpy.c
// compile with: /W3
// This program uses strcpy
// and strcat to build a phrase.

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[80];

   // If you change the previous line to
   //   char string[20];
   // strcpy and strcat will happily overrun the string
   // buffer.  See the examples for strncpy and strncat
   // for safer string handling.

   strcpy( string, "Hello world from " ); // C4996
   // Note: strcpy is deprecated; use strcpy_s instead
   strcat( string, "strcpy " );           // C4996
   // Note: strcat is deprecated; use strcat_s instead
   strcat( string, "and " );              // C4996
   strcat( string, "strcat!" );           // C4996
   printf( "String = %s\n", string );
}
```

```Output
String = Hello world from strcpy and strcat!
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
