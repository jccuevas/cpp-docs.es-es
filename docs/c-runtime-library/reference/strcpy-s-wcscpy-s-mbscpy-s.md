---
title: strcpy_s, wcscpy_s, _mbscpy_s
ms.date: 03/22/2086
apiname:
- wcscpy_s
- _mbscpy_s
- strcpy_s
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
apitype: DLLExport
f1_keywords:
- strcpy_s
- _mbscpy_s
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: d7deeb2d3286ca20518527df26c4765197f8a087
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616611"
---
# <a name="strcpys-wcscpys-mbscpys"></a>strcpy_s, wcscpy_s, _mbscpy_s

Copia una cadena. Estas versiones de [strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscpy_s** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Ubicación del búfer de cadena de destino.

*dest_size*<br/>
Tamaño del búfer de cadena de destino en **char** unidades para las funciones estrechas y multibyte, y **wchar_t** unidades para las funciones anchas. Este valor debe ser mayor que cero y no mayor que **RSIZE_MAX**.

*src*<br/>
Búfer de cadena de origen terminada en NULL.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; en caso contrario, error.

### <a name="error-conditions"></a>Condiciones de error

|*dest*|*dest_size*|*src*|Valor devuelto|Contenido de *dest*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**|any|any|**EINVAL**|no modificado|
|any|any|**NULL**|**EINVAL**|*dest*[0] se establece en 0|
|any|0, o demasiado pequeño|any|**ERANGE**|*dest*[0] se establece en 0|

## <a name="remarks"></a>Comentarios

El **strcpy_s** función copia el contenido de la dirección de *src*, incluido el carácter nulo final, en la ubicación especificada por *dest*. La cadena de destino debe ser lo suficientemente grande como para contener la cadena de origen y su carácter nulo de terminación. El comportamiento de **strcpy_s** es indefinido si las cadenas de origen y destino se superponen.

**wcscpy_s** es la versión de caracteres anchos de **strcpy_s**, y **_mbscpy_s** es la versión de caracteres multibyte. Los argumentos de **wcscpy_s** son caracteres anchos cadenas; los de **_mbscpy_s** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

Si *dest* o *src* es un puntero nulo, o si el tamaño de la cadena de destino *dest_size* es demasiado pequeño, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EINVAL** y establecer **errno** a **EINVAL** cuando *dest* o  *src* es un puntero nulo, y devuelven **ERANGE** y establecer **errno** a **ERANGE** cuando la cadena de destino es demasiado pequeña.

Si la ejecución finaliza correctamente, la cadena de destino siempre termina en null.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla —que pueden realizar automáticamente una inferencia de la longitud de búfer para eliminar la necesidad de especificar un argumento de tamaño— y pueden reemplazar automáticamente funciones anteriores no seguras por sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<string.h> o \<wchar.h>|
|**_mbscpy_s**|\<mbstring.h>|

Estas funciones son específicas de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

A diferencia del código de calidad de producción, en este ejemplo llama a las funciones de cadena segura sin comprobación de errores:

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

Al compilar el código de C++, las versiones de plantilla pueden ser más fáciles de usar.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md) <br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
