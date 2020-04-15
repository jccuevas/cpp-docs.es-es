---
title: _mbbtype, _mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341411"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Devuelve el tipo de bytes, según el byte anterior.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Carácter que se va a probar.

*type*<br/>
El tipo de byte que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbbtype** devuelve el tipo de byte en una cadena. Esta decisión es sensible al contexto, según lo especificado por el valor de *type*, que proporciona la condición de prueba de control. *tipo* es el tipo del byte anterior en la cadena. Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.

|Valor del *tipo*|**_mbbtype** pruebas para|Valor devuelto|*C*|
|---------------------|--------------------------|------------------|---------|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_SINGLE** (0)|Byte único (0x20 - 0x7E, 0xA1 - 0xDF)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_LEAD** (1)|Byte principal de carácter multibyte (0x81 - 0x9F, 0xE0 - 0xFC)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos.|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|
|1|Byte final válido|**_MBC_TRAIL** (2)|Byte final de carácter multibyte (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Byte final válido|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Observaciones

La función **_mbbtype** determina el tipo de un byte en un carácter multibyte. Si el valor de *type* es cualquier valor excepto 1, **_mbbtype** pruebas para un byte único o un byte principal válido de un carácter multibyte. Si el valor de *type* es 1, **_mbbtype** pruebas para un byte de seguimiento válido de un carácter multibyte.

El valor de salida se ve afectado por la configuración de la **LC_CTYPE** configuración de categoría de la configuración regional; ver [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. La **versión _mbbtype** de esta función utiliza la configuración regional actual para este comportamiento dependiente de la configuración regional; la versión **_mbbtype_l** es idéntica, excepto que usa el parámetro de configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbbtype** se denominaba **chkctype**. Para el nuevo código, use **_mbbtype** en su lugar.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Para las definiciones de constantes de manifiesto que se usan como valores devueltos.

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
