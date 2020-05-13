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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e84e6b367c428dc26a1864db80f6828f7ec9c176
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911828"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Compara **n** bytes de dos cadenas de caracteres multibyte y omite el uso de mayúsculas y minúsculas.

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

*cadena1*, *cadena2*<br/>
Cadenas terminadas en NULL que se van a comparar.

*count*<br/>
Número de bytes que se van a comparar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación entre las subcadenas.

|Valor devuelto|Descripción|
|------------------|-----------------|
|< 0|la subcadena de *cadena1* es menor que *cadena2* subcadena.|
|0|la subcadena *cadena1* es idéntica a la subcadena *cadena2* .|
|> 0|la subcadena *cadena1* es mayor que *cadena2* subcadena.|

En un error, **_mbsnbicmp** devuelve **_NLSCMPERROR**, que se define en String. h y mbstring. h.

## <a name="remarks"></a>Observaciones

La función **_mbsnbicmp** realiza una comparación ordinal de como máximo los primeros bytes de *número* de *cadena1* y *cadena2*. La comparación se realiza mediante la conversión de cada carácter a minúsculas. [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) es una versión de **_mbsnbicmp**que distingue mayúsculas de minúsculas. La comparación finaliza si se alcanza un carácter nulo de terminación en una cadena antes de que se comparen los caracteres de *recuento* . Si las cadenas son iguales cuando se alcanza un carácter nulo de terminación en una cadena antes de que se comparen los caracteres de *recuento* , la cadena más corta es menor.

**_mbsnbicmp** es similar a [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), salvo que compara las cadenas hasta *contar* bytes en lugar de caracteres.

Dos cadenas que contienen caracteres situados entre la 'Z' y la 'a' en la tabla ASCII ('[', '\\', ']', '^', '_' y '\`') se comparan de forma distinta. Por ejemplo, las dos cadenas "ABCDe" y "ABCD ^" se comparan de una manera si la comparación es minúscula ("ABCDE" > "ABCD ^") y la otra ("ABCDe" < "ABCD ^") si está en mayúsculas.

**_mbsnbicmp** reconoce secuencias de caracteres multibyte según la [Página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso. La configuración regional actual no le afecta.

Si *string1* o *cadena2* es un puntero nulo, **_mbsnbicmp** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **_NLSCMPERROR** y establece **errno** en **EINVAL**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
