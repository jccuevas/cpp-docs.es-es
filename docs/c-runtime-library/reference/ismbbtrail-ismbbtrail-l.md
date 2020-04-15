---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 4/2/2020
api_name:
- _ismbbtrail
- _ismbbtrail_l
- _o__ismbbtrail
- _o__ismbbtrail_l
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
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
ms.openlocfilehash: 5e8615adf5d17986c1a52658fe5d680cc326976a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343401"
---
# <a name="_ismbbtrail-_ismbbtrail_l"></a>_ismbbtrail, _ismbbtrail_l

Determina si un byte es el byte final de un carácter multibyte.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbtrail(
   unsigned int c
);
int _ismbbtrail_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_ismbbtrail** devuelve un valor distinto de cero si el entero *c* es el segundo byte de un carácter multibyte. Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son de 0x40 a 0x7E y de 0x80 a 0xFC.

## <a name="remarks"></a>Observaciones

**_ismbbtrail** utiliza la configuración regional actual para el comportamiento dependiente de la configuración regional. **_ismbbtrail_l** es idéntica, excepto que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<mbctype.h> o \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbbtrail_l**|\<mbctype.h> o \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Para las constantes de manifiesto de las condiciones de prueba.

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[rutinas _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
