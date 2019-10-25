---
title: _strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
ms.date: 11/04/2016
api_name:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
ms.openlocfilehash: 6d1645c33684f5a0fbabc2119592c39a7df97ca3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947134"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l

Compara el número de caracteres especificado de dos cadenas sin distinción entre mayúsculas y minúsculas.

> [!IMPORTANT]
> **_mbsnicmp** y **_mbsnicmp_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*cadena1*, *cadena2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*count*<br/>
Número de caracteres que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Indica la relación entre las subcadenas, como se muestra a continuación.

|Valor devuelto|DESCRIPCIÓN|
|------------------|-----------------|
|< 0|la subcadena *cadena1* es menor que *cadena2* subcadena.|
|0|la subcadena *cadena1* es idéntica a la subcadena *cadena2* .|
|> 0|la subcadena *cadena1* es mayor que *cadena2* subcadena.|

En un error de validación de parámetros, estas funciones devuelven **_NLSCMPERROR**, \<que se define en String \<. h > y mbstring. h >.

## <a name="remarks"></a>Comentarios

La función **_strnicmp** compara ordinalmente, como máximo, los primeros caracteres de *recuento* de *cadena1* y *cadena2*. La comparación se realiza sin distinguir entre mayúsculas y minúsculas, ya que todos los caracteres se convierten a minúsculas. **_strnicmp** es una versión de **strncmp**que no distingue mayúsculas de minúsculas. La comparación finaliza si se alcanza un carácter nulo de terminación en una cadena antes de que se comparen los caracteres de *recuento* . Si las cadenas son iguales cuando se alcanza un carácter nulo de terminación en una cadena antes de que se comparen los caracteres de *recuento* , la cadena más corta es menor.

Los caracteres 91 a 96 en la tabla ASCII ("[", "\\", "]", "^", "_" y "\`") se consideran menores que cualquier carácter alfabético. Esta ordenación es idéntica a la de **stricmp**.

**_wcsnicmp** y **_mbsnicmp** son versiones de caracteres anchos y multibyte de **_strnicmp**. Los argumentos de **_wcsnicmp** son cadenas de caracteres anchos; los de **_mbsnicmp** son cadenas de caracteres multibyte. **_mbsnicmp** reconoce las secuencias de caracteres multibyte según la página de códigos multibyte actual y devuelve **_NLSCMPERROR** en un error. Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md). Estas tres funciones se comportan exactamente igual. Estas funciones se ven afectadas por la configuración regional; las versiones que no tienen el sufijo **_L** usan la configuración regional actual para su comportamiento dependiente de la configuración regional; en su lugar, las versiones que tienen el sufijo **_L** usan la *configuración regional* que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Todas estas funciones validan sus parámetros. Si *string1* o *cadena2* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y establecen **errno** en **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strnicmp**, **_strnicmp_l**|\<string.h>|
|**_wcsnicmp**, **_wcsnicmp_l**|\<string.h> o \<wchar.h>|
|**_mbsnicmp**, **_mbsnicmp_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
