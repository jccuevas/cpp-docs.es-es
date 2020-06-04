---
title: _ismbbkpunct, _ismbbkpunct_l
ms.date: 4/2/2020
api_name:
- _ismbbkpunct_l
- _ismbbkpunct
- _o__ismbbkpunct
- _o__ismbbkpunct_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
ms.openlocfilehash: 8cf2d0d38466c370d0110b71a302471679e64657
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915695"
---
# <a name="_ismbbkpunct-_ismbbkpunct_l"></a>_ismbbkpunct, _ismbbkpunct_l

Comprueba si un carácter multibyte es un carácter de puntuación.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbkpunct(
   unsigned int c
);
int _ismbbkpunct_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_ismbbkpunct** devuelve un valor distinto de cero si el entero *c* es un signo de puntuación no ASCII, o 0 si no lo es. Por ejemplo, solo en la página de códigos 932, **_ismbbkpunct** prueba si hay signos de puntuación katakana. **_ismbbkpunct** usa la configuración regional actual para los valores de caracteres dependientes de la configuración regional. **_ismbbkpunct_l** es idéntico, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbkpunct**|\<mbctype.h>|
|**_ismbbkpunct_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb rutinas](../../c-runtime-library/ismbb-routines.md)<br/>
