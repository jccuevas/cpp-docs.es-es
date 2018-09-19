---
title: _mbsnbicmp, _mbsnbicmp_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43c9da102f81654062518ca8e886aab1c49df623
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314968"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Compara **n** bytes de caracteres multibyte dos cadenas y no distingue entre mayúsculas.

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
|< 0|*cadena1* subcadena menor *cadena2* subcadena.|
|0|*cadena1* idéntico de la subcadena *cadena2* subcadena.|
|> 0|*cadena1* subcadena mayor *cadena2* subcadena.|

Produce un error, **_mbsnbicmp** devuelve **_NLSCMPERROR**, que se define en String.h y Mbstring.h.

## <a name="remarks"></a>Comentarios

El **_mbsnbicmp** función realiza una comparación ordinal de a lo sumo *recuento* bytes de *string1* y *cadena2*. La comparación se realiza mediante la conversión de cada carácter a minúscula. [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) es una versión entre mayúsculas y minúsculas de **_mbsnbicmp**. La comparación finaliza si se alcanza un carácter nulo de terminación en una de las cadenas antes de *recuento* se comparan los caracteres. Si las cadenas son iguales cuando se alcanza un carácter nulo de terminación en una de las cadenas antes de *recuento* se comparan los caracteres, la cadena más corta es menor.

**_mbsnbicmp** es similar a [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), salvo por que compara cadenas hasta *recuento* bytes en lugar de caracteres.

Dos cadenas que contienen caracteres situados entre la 'Z' y la 'a' en la tabla ASCII ('[', '\\', ']', '^', '_' y '\`') se comparan de forma distinta. Por ejemplo, las dos cadenas "ABCDE" y "ABCD ^" comparan de un modo si la comparación es minúscula ("abcde" > "abcd ^") y la otra manera ("ABCDE" < "ABCD ^") si está en mayúsculas.

**_mbsnbicmp** reconoce secuencias de caracteres multibyte según la [página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso. La configuración regional actual no le afecta.

Si bien *string1* o *cadena2* es un puntero nulo, **_mbsnbicmp** invoca el controlador de parámetros no válidos, como se describe en [devalidacióndeparámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **_NLSCMPERROR** y establece **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
