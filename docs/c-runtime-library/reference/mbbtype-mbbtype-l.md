---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
api_name:
- _mbbtype
- _mbbtype_l
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
ms.openlocfilehash: ba4311921a0924d3f447feb1929a81ae1d816604
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952722"
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

*c*<br/>
Carácter que se va a probar.

*type*<br/>
El tipo de byte que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbbtype** devuelve el tipo de byte de una cadena. Esta decisión es contextual, tal y como se especifica en el valor de *tipo*, que proporciona la condición de prueba del control. *Type* es el tipo del byte anterior de la cadena. Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.

|Valor de *tipo*|pruebas de **_mbbtype** para|Valor devuelto|*c*|
|---------------------|--------------------------|------------------|---------|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_SINGLE** (0)|Un solo byte (0x20-0x7E, 0xA1-0xDF)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_LEAD** (1)|Byte inicial de un carácter multibyte (0x81-0x9F, 0xE0-0xFC)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos.|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|
|1|Byte final válido|**_MBC_TRAIL** (2)|Byte final de un carácter multibyte (0x40-0x7E, 0x80-0xFC)|
|1|Byte final válido|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|

## <a name="remarks"></a>Comentarios

La función **_mbbtype** determina el tipo de un byte en un carácter multibyte. Si el valor de *tipo* es cualquier valor excepto 1, **_mbbtype** comprueba si hay un byte de un solo byte válido o un byte inicial de un carácter multibyte. Si el valor de *tipo* es 1, **_mbbtype** comprueba si hay un byte final válido de un carácter multibyte.

El valor de salida se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. La versión **_mbbtype** de esta función usa la configuración regional actual para este comportamiento dependiente de la configuración regional; la versión de **_mbbtype_l** es idéntica, salvo que usa el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbbtype** tenía el nombre **chkctype**. Para el nuevo código, utilice **_mbbtype** en su lugar.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Para las definiciones de constantes de manifiesto que se usan como valores devueltos.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
