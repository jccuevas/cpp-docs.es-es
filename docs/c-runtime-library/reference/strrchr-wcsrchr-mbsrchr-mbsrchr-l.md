---
title: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
ms.date: 4/2/2020
api_name:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
- _o__mbsrchr
- _o__mbsrchr_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
ms.openlocfilehash: 2475eab34c6a18b3dc7a8a15145c184cea543aee
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911158"
---
# <a name="strrchr-wcsrchr-_mbsrchr-_mbsrchr_l"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

Examina una cadena para buscar la última repetición de un carácter.

> [!IMPORTANT]
> `_mbsrchr` y `_mbsrchr_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*CAD*<br/>
Cadena terminada en NULL que se va a buscar.

*unidad*<br/>
Carácter que se va a buscar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la última aparición de *c* en *Str*, o null si no se encuentra *c* .

## <a name="remarks"></a>Observaciones

La `strrchr` función encuentra la última aparición de *c* (convertida en **Char**) en *Str*. La búsqueda incluye el carácter nulo de terminación.

`wcsrchr` y `_mbsrchr` son versiones de caracteres anchos y multibyte de `strrchr`. Los argumentos y el valor devuelto de `wcsrchr` son cadenas de caracteres anchos; los de `_mbsrchr` son cadenas de caracteres multibyte.

En C, estas funciones toman un puntero **const** para el primer argumento. En C++, hay disponibles dos sobrecargas. La sobrecarga que toma un puntero a **const** devuelve un puntero a **const**; la versión que toma un puntero a no**const** devuelve un puntero a no**const**. La macro _CRT_CONST_CORRECT_OVERLOADS se define si están disponibles tanto las versiones **const** como las no**const** de estas funciones. Si necesita el comportamiento no**const** para ambas sobrecargas de C++, defina el símbolo _CONST_RETURN.

`_mbsrchr` valida sus parámetros. Si *Str* es null, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en EINVAL y `_mbsrchr` devuelve 0. `strrchr` y `wcsrchr` no validan sus parámetros. Estas tres funciones se comportan exactamente igual.

El valor de salida se ve afectado por la configuración de la categoría LC_CTYPE de la configuración regional. para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**n/a**|**n/a**|`_mbsrchr_l`|**n/a**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> o \<wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo sobre cómo se usa `strrchr`, vea[strchr](strchr-wcschr-mbschr-mbschr-l.md).

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
