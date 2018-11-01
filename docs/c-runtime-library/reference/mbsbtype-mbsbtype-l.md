---
title: _mbsbtype, _mbsbtype_l
ms.date: 11/04/2016
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: 5c2927b4e4b68b1284341fe7e767ec50feb21a44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566808"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

Devuelve el tipo de byte en una cadena.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*mbstr*<br/>
Dirección de una secuencia de caracteres multibyte.

*count*<br/>
Desplazamiento de bytes desde el encabezado de la cadena.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbsbtype** y **_mbsbtype_l** devuelve un valor entero que indica el resultado de la prueba en el byte especificado. Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.

|Valor devuelto|Tipo de byte|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Carácter de un solo byte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 0 si el byte especificado está dentro del intervalo 0 x 20-0x7E o 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Byte inicial de un carácter multibyte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 1 si el byte especificado está dentro del intervalo 0 x 81-0x9F o 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Byte final de un carácter multibyte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 2 si el byte especificado está dentro del intervalo 0 x 40-0x7E o 0 x 80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**NULL** cadena, carácter no válido o byte nulo encontrado antes del byte en el desplazamiento *recuento* en *mbstr*.|

## <a name="remarks"></a>Comentarios

El **_mbsbtype** función determina el tipo de un byte en una cadena de caracteres multibyte. La función solo examina el byte en el desplazamiento *recuento* en *mbstr*, omitiendo los caracteres no válidos anteriores al byte especificado.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. La versión de esta función sin el **_l** sufijo usa la configuración regional actual para este comportamiento dependiente de la configuración regional; la versión con el **_l** sufijo es idéntico, salvo que use el parámetro locale pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si la cadena de entrada es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **_MBC_ILLEGAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* En el caso de las constantes de manifiesto usadas como valores devueltos.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
