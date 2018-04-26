---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
dev_langs:
- C++
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1415a7423e231b994ff21120faeb49a45d51a70
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Convierte caracteres de JIS en caracteres de Japan Microsoft (JMS), y viceversa.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

En la configuración regional japonesa, estas funciones devuelven un carácter convertidos, o 0 si la conversión no es posible. En una configuración regional no japonesa, estas funciones devuelven el carácter que se pasa.

## <a name="remarks"></a>Comentarios

El **_mbcjistojms** función convierte un carácter de Japan sector estándar (JIS) en un carácter de Microsoft Kanji (Shift JIS). El carácter se convierte solo si los bytes inicial y final están en el intervalo 0 x 21 - 0x7E. Si el byte inicial o final está fuera de este intervalo, **errno** está establecido en **EILSEQ**. Para obtener más información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El **_mbcjmstojis** función convierte un carácter Shift JIS en un carácter JIS. El carácter se convierte solo si el byte inicial está en el intervalo 0 x 81-0x9F o 0xE0 - 0xFC y el byte final está en el intervalo 0 x 40-0x7E o 0 x 80 - 0xFC. Observe que algunos puntos de código de ese intervalo no tienen un carácter asignado, por lo que no pueden convertirse.

El valor *c* debe ser un valor de 16 bits cuyos 8 bits superiores representen el byte inicial del carácter que se va a convertir y cuyos 8 bits inferiores representen el byte final.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En versiones anteriores, **_mbcjistojms** y **_mbcjmstojis** llamó **jistojms** y **jmstojis**, respectivamente. **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** y **_mbcjmstojis_l** debe usarse en su lugar.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbcjistojms**|\<mbstring.h>|
|**_mbcjistojms_l**|\<mbstring.h>|
|**_mbcjmstojis**|\<mbstring.h>|
|**_mbcjmstojis_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
