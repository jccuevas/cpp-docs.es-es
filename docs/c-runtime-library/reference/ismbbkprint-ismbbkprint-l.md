---
title: _ismbbkprint, _ismbbkprint_l
ms.date: 4/2/2020
api_name:
- _ismbbkprint
- _ismbbkprint_l
- _o__ismbbkprint
- _o__ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
ms.openlocfilehash: e59d06678b2601375bf3174fa84bc261c350c4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343629"
---
# <a name="_ismbbkprint-_ismbbkprint_l"></a>_ismbbkprint, _ismbbkprint_l

Determina si un carácter multibyte determinado es un signo de puntuación.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbkprint(
   unsigned int c
);
int _ismbbkprint_l(
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

**_ismbbkprint** devuelve un valor distinto de cero si el entero *c* es un símbolo de puntuación que no es ASCII o no ASCII o 0 si no lo es. Por ejemplo, solo en la página de códigos 932, **_ismbbkprint** comprueba si hay caracteres o signos de puntuación katakana (intervalo: 0xA1 - 0xDF). **_ismbbkprint** utiliza la configuración regional actual para la configuración de caracteres dependiente de la configuración regional. **_ismbbkprint_l** es idéntica, excepto que utiliza la configuración regional pasada. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Observaciones

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbkprint**|\<mbctype.h>|
|**_ismbbkprint_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[rutinas _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
