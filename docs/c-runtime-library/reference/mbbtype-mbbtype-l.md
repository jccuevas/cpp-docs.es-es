---
title: _mbbtype, _mbbtype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs:
- C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91b78b0dc57873810f96a793288da3f1457299de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l

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

**_mbbtype** devuelve el tipo de byte de una cadena. Esta decisión es contextual, según lo especificado por el valor de *tipo*, que proporciona la condición de prueba del control. *tipo* es el tipo del byte anterior de la cadena. Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.

|Valor de *tipo*|**_mbbtype** para las pruebas|Valor devuelto|*c*|
|---------------------|--------------------------|------------------|---------|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_SINGLE** (0)|Un solo byte (0 x 20 - 0x7E, 0xA1 - 0xDF)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos|**_MBC_LEAD** (1)|Byte de un carácter multibyte inicial (0 x 81 - 0x9F, 0xE0 - 0xFC)|
|Cualquier valor excepto 1|Byte único o byte inicial válidos.|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|
|1|Byte final válido|**_MBC_TRAIL** (2)|Byte final de juegos de caracteres multibyte (0 x 40 - 0x7E, 0 x 80 - 0xFC)|
|1|Byte final válido|**_MBC_ILLEGAL**<br /><br /> ( -1)|Carácter no válido (cualquier valor excepto 0 x 20 - 0x7E, 0xA1 - 0xDF, 0 x 81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Comentarios

El **_mbbtype** función determina el tipo de un byte de un carácter multibyte. Si el valor de *tipo* es cualquier valor excepto 1, **_mbbtype** pruebas para un válido byte único o byte inicial de un carácter multibyte. Si el valor de *tipo* es 1, **_mbbtype** comprueba si un byte final válido de un carácter multibyte.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. El **_mbbtype** versión de esta función usa la configuración regional actual para este comportamiento dependiente de la configuración regional; la **_mbbtype_l** versión es idéntica, salvo que usa el parámetro de configuración regional que se pasa en su lugar . Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbbtype** se llamaba **chkctype**. Para código nuevo, use **_mbbtype** en su lugar.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Para las definiciones de constantes de manifiesto que se usan como valores devueltos.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
