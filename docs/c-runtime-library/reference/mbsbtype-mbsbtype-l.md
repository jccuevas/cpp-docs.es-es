---
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340871"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

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
|**_MBC_SINGLE** (0)|Carácter de un solo byte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 0 si el byte especificado está dentro del intervalo 0x20 - 0x7E o 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Byte inicial de un carácter multibyte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 1 si el byte especificado está dentro del intervalo 0x81 - 0x9F o 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Byte final de un carácter multibyte. Por ejemplo, en la página de códigos 932, **_mbsbtype** devuelve 2 si el byte especificado está dentro del intervalo 0x40 - 0x7E o 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**Cadena NULL,** carácter no válido o byte nulo encontrado antes del byte en el *recuento* de desplazamiento en *mbstr*.|

## <a name="remarks"></a>Observaciones

La función **_mbsbtype** determina el tipo de un byte en una cadena de caracteres multibyte. La función examina solo el byte en el *recuento* de desplazamientos en *mbstr*, ignorando los caracteres no válidos antes del byte especificado.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. La versión de esta función sin el **sufijo _l** utiliza la configuración regional actual para este comportamiento dependiente de la configuración regional; la versión con el sufijo **_l** es idéntica, excepto que utiliza el parámetro de configuración regional pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si la cadena de entrada es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **_MBC_ILLEGAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* En el caso de las constantes de manifiesto usadas como valores devueltos.

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
