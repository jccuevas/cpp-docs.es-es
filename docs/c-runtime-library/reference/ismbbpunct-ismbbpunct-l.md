---
title: _ismbbpunct, _ismbbpunct_l
ms.date: 4/2/2020
api_name:
- _ismbbpunct
- _ismbbpunct_l
- _o__ismbbpunct
- _o__ismbbpunct_l
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
- ismbbpunct
- ismbbpunct_l
- _ismbbpunct_l
- _ismbbpunct
helpviewer_keywords:
- ismbbpunct function
- _ismbbpunct function
- ismbbpunct_l function
- _ismbbpunct_l function
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
ms.openlocfilehash: bee75f971f6e185b4081ba123e6aef5e1865a14e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918657"
---
# <a name="_ismbbpunct-_ismbbpunct_l"></a>_ismbbpunct, _ismbbpunct_l

Determina si un carácter determinado es un carácter de puntuación.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbpunct(
   unsigned int c
);
int _ismbbpunct_l(
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

**_ismbbpunct** devuelve un valor distinto de cero si el entero *c* es un signo de puntuación no ASCII. **_ismbbpunct** usa la configuración regional actual para los valores de caracteres dependientes de la configuración regional. **_ismbbpunct_l** es idéntico, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbpunct**|\<mbctype.h>|
|**_ismbbpunct_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb rutinas](../../c-runtime-library/ismbb-routines.md)<br/>
