---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
- _o__mbsnbcoll
- _o__mbsnbcoll_l
- _o__mbsnbicoll
- _o__mbsnbicoll_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 491a652f19e9e1895aa62092c5c890923008f6e1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911910"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Compara *n* bytes de dos cadenas de caracteres multibyte usando la información de página de códigos multibyte.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*cadena1*, *cadena2*<br/>
Cadenas que se van a comparar.

*count*<br/>
Número de bytes que se van a comparar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación de las subcadenas de *string1* y *String2*.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|la subcadena de *cadena1* es menor que *cadena2* subcadena.|
|0|la subcadena *cadena1* es idéntica a la subcadena *cadena2* .|
|> 0|la subcadena *cadena1* es mayor que *cadena2* subcadena.|

Si *string1* o *cadena2* es **null** o *Count* es mayor que **INT_MAX**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **_NLSCMPERROR** y establecen **errno** en **EINVAL**. Para usar **_NLSCMPERROR**, incluya String. h o mbstring. h.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones intercala, como máximo, el primer *número* de bytes en *cadena1* y *cadena2* , y devuelve un valor que indica la relación entre las subcadenas resultantes de *string1* y *String2*. Si el byte final de la subcadena de *cadena1* o *cadena2* es un byte inicial, no se incluye en la comparación; Estas funciones comparan solo caracteres completos en las subcadenas. **_mbsnbicoll** es una versión que no distingue entre mayúsculas y minúsculas de **_mbsnbcoll**. Como [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) y [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** y **_mbsnbicoll** intercalan las dos cadenas de caracteres multibyte según el orden lexicográfico especificado por la página de [códigos](../../c-runtime-library/code-pages.md) multibyte actualmente en uso.

En el caso de algunas páginas de códigos y los juegos de caracteres correspondientes, el orden de los caracteres del juego de caracteres no es igual que el orden lexicográfico de los caracteres. En la configuración regional de "C" no es así: el orden de los caracteres del juego de caracteres ASCII es igual que el orden lexicográfico de los caracteres. Sin embargo, en algunas páginas de códigos europeas, por ejemplo, el carácter “a” (valor 0x61) precede el carácter “ä” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente. Para realizar una comparación lexicográfico de cadenas por bytes en una instancia de este tipo, utilice **_mbsnbcoll** en lugar de **_mbsnbcmp**; para comprobar solo la igualdad de cadenas, use **_mbsnbcmp**.

Dado que las funciones de **Intercalación** intercalan cadenas lexicográficamente para su comparación, mientras que las funciones **CMP** simplemente prueban la igualdad de cadenas, las funciones de **Intercalación** son mucho más lentas que las versiones de **CMP** correspondientes. Por lo tanto, las funciones de **Intercalación** deben usarse solo cuando hay una diferencia entre el orden del juego de caracteres y el orden de los caracteres lexicográfico en la página de códigos actual y esta diferencia es de interés para la comparación.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[Funciones de strcoll (](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
