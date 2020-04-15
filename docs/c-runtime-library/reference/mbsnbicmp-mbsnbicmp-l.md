---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340580"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Compara **n** bytes de dos cadenas de caracteres multibyte e ignora mayúsculas y minúsculas.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*string1*, *string2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*count*<br/>
Número de bytes que se van a comparar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación entre las subcadenas.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|*string1* subcadena menor que *string2* subcadena.|
|0|subcadena *string1* idéntica a la subcadena *string2.*|
|> 0|*string1* subcadena mayor que *string2* subcadena.|

En un error, **_mbsnbicmp** devuelve **_NLSCMPERROR**, que se define en String.h y Mbstring.h.

## <a name="remarks"></a>Observaciones

La función **_mbsnbicmp** realiza una comparación ordinal de como máximo los primeros bytes de *recuento* de *string1* y *string2*. La comparación se realiza convirtiendo cada carácter a minúsculas; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) es una versión de **_mbsnbicmp**que distingue mayúsculas de minúsculas. La comparación finaliza si se alcanza un carácter nulo de terminación en cualquiera de las cadenas antes de que se comparen los caracteres de *recuento.* Si las cadenas son iguales cuando se alcanza un carácter nulo de terminación en cualquiera de las cadenas antes de que se comparen los caracteres de *recuento,* la cadena más corta es menor.

**_mbsnbicmp** es similar a [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), excepto que compara cadenas hasta *contar* bytes en lugar de por caracteres.

Dos cadenas que contienen caracteres situados entre la 'Z' y la 'a' en la tabla ASCII ('[', '\\', ']', '^', '_' y '\`') se comparan de forma distinta. Por ejemplo, las dos cadenas "ABCDE" y "ABCD" se comparan de una manera si la comparación está en minúsculas ("abcde" > "abcd") y la otra ("ABCDE" < "ABCD) si está en mayúsculas.

**_mbsnbicmp** reconoce las secuencias de caracteres multibyte según la página de [códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso. La configuración regional actual no le afecta.

Si *string1* o *string2* es un puntero nulo, **_mbsnbicmp** invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **_NLSCMPERROR** y establece **errno** en **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
