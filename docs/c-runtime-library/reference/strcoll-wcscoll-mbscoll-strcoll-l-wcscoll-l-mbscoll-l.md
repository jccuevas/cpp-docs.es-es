---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 4/2/2020
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
- _o__mbscoll
- _o__mbscoll_l
- _o__strcoll_l
- _o__wcscoll_l
- _o_strcoll
- _o_wcscoll
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 9cbf24fafa78ac6a53a99abf0d1bb1ab3a0625c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358124"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Compara cadenas usando la configuración regional actual o una categoría de conversión de estado LC_COLLATE especificada.

> [!IMPORTANT]
> **_mbscoll** y **_mbscoll_l** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
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

Cada una de estas funciones devuelve un valor que indica la relación de *string1* a *string2*, como se indica a continuación.

|Valor devuelto|Relación de string1 y string2|
|------------------|----------------------------------------|
|< 0|*string1* menor que *string2*|
|0|*string1* idéntico a *string2*|
|> 0|*string1* mayor que *string2*|

Cada una de estas funciones devuelve **_NLSCMPERROR** en un error. Para utilizar **_NLSCMPERROR**, incluya STRING. H o MBSTRING. H. **wcscoll** puede producir un error si *string1* o *string2* es **NULL** o contiene códigos de caracteres anchos fuera del dominio de la secuencia de intercalación. Cuando se produce un error, **wcscoll** puede establecer **errno en** **EINVAL**. Para comprobar si hay un error en una llamada a **wcscoll**, establezca **errno** en 0 y, a continuación, compruebe **errno** después de llamar a **wcscoll**.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones realiza una comparación que distingue mayúsculas de minúsculas de *string1* y *string2* según la página de códigos actualmente en uso. Estas funciones solo se deben usar cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos son distintos en la página de códigos actual, y la diferencia influye en la comparación de cadenas.

Todas estas funciones validan sus parámetros. Si *string1* o *string2* es un puntero nulo, o si *count* es mayor que **INT_MAX**, se invoca el controlador de parámetros no válidos, como se describe en [validación](../../c-runtime-library/parameter-validation.md) de parámetros . Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y **establecen errno** en **EINVAL**.

La comparación de las dos cadenas es una operación dependiente de la configuración regional, ya que cada configuración regional tiene distintas reglas para ordenar los caracteres. Las versiones de estas funciones sin el **_l** sufijo utilizan la configuración regional del subproceso actual para este comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas a la función correspondiente sin el sufijo excepto que utilizan la configuración regional pasada como parámetro en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>, \<string.h>|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>, \<string.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
