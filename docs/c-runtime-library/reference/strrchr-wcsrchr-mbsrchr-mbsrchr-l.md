---
title: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
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
apitype: DLLExport
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a41b52b07d5f3abc290773bd7c96ca82d1b698a8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strrchr-wcsrchr-mbsrchr-mbsrchrl"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

Examina una cadena para buscar la última repetición de un carácter.

> [!IMPORTANT]
> **_mbsrchr** y **_mbsrchr_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Cadena terminada en NULL que se va a buscar.

*c*<br/>
Carácter que se va a buscar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la última aparición de *c* en *str*, o **NULL** si *c* no se encuentra.

## <a name="remarks"></a>Comentarios

El **strrchr** función busca la última aparición de *c* (convertido en **char**) en *str*. La búsqueda incluye el carácter nulo de terminación.

**wcsrchr** y **_mbsrchr** son versiones de caracteres multibyte y anchos de **strrchr**. Los argumentos y el valor devuelto de **wcsrchr** son caracteres anchos cadenas; los de **_mbsrchr** son cadenas de caracteres multibyte.

En C, estas funciones toman una ** const ** puntero para el primer argumento. En C++, hay disponibles dos sobrecargas. La sobrecarga que toma un puntero a ** const ** devuelve un puntero a **const **; la versión que toma un puntero a no -** const ** devuelve un puntero a no es**const **. La macro **_CRT_CONST_CORRECT_OVERLOADS** se define si tanto el **const ** y no-** const ** las versiones de estas funciones están disponibles. Si necesitas no es**const ** comportamiento para ambas sobrecargas de C++, defina el símbolo **_CONST_RETURN**.

**_mbsrchr** valida sus parámetros. Si *str* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y **_mbsrchr** devuelve 0. **strrchr** y **wcsrchr** no validan sus parámetros. Estas tres funciones se comportan exactamente igual.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** categoría de configuración de la configuración regional; para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrchr**|**strrchr**|**_mbsrchr**|**wcsrchr**|
|**N/D**|**N/D**|**_mbsrchr_l**|**N/D**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strrchr**|\<string.h>|
|**wcsrchr**|\<string.h> o \<wchar.h>|
|**_mbsrchr**, **_mbsrchr_l**|\<mbstring.h>|

Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo del uso de **strrchr**, consulte [strchr](strchr-wcschr-mbschr-mbschr-l.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
