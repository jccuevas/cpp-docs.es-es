---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 11/04/2016
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
ms.openlocfilehash: 7519b8f41d77ed668bb7da1e8ced18ee13c0a5bf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957887"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Compara cadenas usando la configuración regional actual o una categoría de conversión de estado LC_COLLATE especificada.

> [!IMPORTANT]
> **_mbscoll** y **_mbscoll_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*cadena1*, *cadena2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un valor que indica la relación entre *string1* y *cadena2*, como se indica a continuación.

|Valor devuelto|Relación de string1 y string2|
|------------------|----------------------------------------|
|< 0|*cadena1* menor que *cadena2*|
|0|*cadena1* idéntico a *cadena2*|
|> 0|*cadena1* mayor que *cadena2*|

Cada una de estas funciones devuelve **_NLSCMPERROR** en un error. Para usar **_NLSCMPERROR**, incluya cualquier cadena. H o MBSTRING. C. se puede producir un error en **wcscoll** si *string1* o *cadena2* es **null** o contiene códigos de caracteres anchos fuera del dominio de la secuencia de intercalación. Cuando se produce un error, **wcscoll** puede establecer **errno** en **EINVAL**. Para comprobar si hay un error en una llamada a **wcscoll**, establezca **errno** en 0 y, a continuación, compruebe **errno** después de llamar a **wcscoll**.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones realiza una comparación con distinción entre mayúsculas y minúsculas de *cadena1* y *cadena2* según la página de códigos actualmente en uso. Estas funciones solo se deben usar cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos son distintos en la página de códigos actual, y la diferencia influye en la comparación de cadenas.

Todas estas funciones validan sus parámetros. Si *string1* o *cadena2* es un puntero nulo, o si *Count* es mayor que **INT_MAX**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y establecen **errno** en **EINVAL**.

La comparación de las dos cadenas es una operación dependiente de la configuración regional, ya que cada configuración regional tiene distintas reglas para ordenar los caracteres. Las versiones de estas funciones sin el sufijo **_L** usan la configuración regional del subproceso actual para este comportamiento dependiente de la configuración regional; las versiones con el sufijo **_L** son idénticas a la función correspondiente sin el sufijo, salvo que usan la configuración regional que se pasa como parámetro en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

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

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
