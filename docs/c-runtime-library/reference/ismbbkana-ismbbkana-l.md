---
title: _ismbbkana, _ismbbkana_l
ms.date: 4/2/2020
api_name:
- _ismbbkana_l
- _ismbbkana
- _o__ismbbkana
- _o__ismbbkana_l
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
- _ismbbkana_l
- ismbbkana_l
- ismbbkana
- _ismbbkana
helpviewer_keywords:
- _ismbbkana_l function
- _ismbbkana function
- ismbbkana function
- ismbbkana_l function
ms.assetid: 64d4eb4a-205a-40ef-be35-ff9d77fabbaf
ms.openlocfilehash: dd788d18692e11886caf4ee12703bb5878de1163
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918947"
---
# <a name="_ismbbkana-_ismbbkana_l"></a>_ismbbkana, _ismbbkana_l

Prueba un símbolo de katakana y es específica de la página de códigos 932.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbkana(
   unsigned int c
);
int _ismbbkana_l(
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

**_ismbbkana** devuelve un valor distinto de cero si el entero *c* es un símbolo katakana o 0 si no lo es. **_ismbbkana** usa la configuración regional actual para la información de caracteres que dependen de la configuración regional. **_ismbbkana_l** es idéntico, salvo que usa el objeto de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbkana**|\<mbctype.h>|
|**_ismbbkana_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb rutinas](../../c-runtime-library/ismbb-routines.md)<br/>
