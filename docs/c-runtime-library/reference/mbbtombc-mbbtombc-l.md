---
title: _mbbtombc, _mbbtombc_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbbtombc_l
- _mbbtombc
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
dev_langs:
- C++
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7fe46b278a93f1c6dedde28f74a270244ebc6ba
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mbbtombc-mbbtombcl"></a>_mbbtombc, _mbbtombc_l

Convierte un carácter multibyte de byte único en el carácter multibyte de doble byte correspondiente.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter de byte único que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Si **_mbbtombc** convierte correctamente *c*, devuelve un carácter multibyte; de lo contrario, devuelve *c*.

## <a name="remarks"></a>Comentarios

El **_mbbtombc** función convierte un carácter multibyte dado de un solo byte en un carácter multibyte de doble byte correspondiente. Caracteres deben estar dentro del intervalo 0 x 20-0x7E o 0xA1 - 0xDF va a convertir.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de esta función son idénticas, salvo que **_mbbtombc** usa la configuración regional actual para este comportamiento dependiente de la configuración regional y **_mbbtombc_l** en su lugar utiliza el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbbtombc** se llamaba **hantozen**. Para código nuevo, use **_mbbtombc**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
