---
title: _ismbbalnum, _ismbbalnum_l
ms.date: 4/2/2020
api_name:
- _ismbbalnum
- _ismbbalnum_l
- _o__ismbbalnum
- _o__ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
ms.openlocfilehash: 3a200415571498c25ce5aacc6271004125ef16d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343692"
---
# <a name="_ismbbalnum-_ismbbalnum_l"></a>_ismbbalnum, _ismbbalnum_l

Determina si un carácter multibyte especificado es alfa o numérico.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbalnum(
   unsigned int c
);
int _ismbbalnum_l(
   unsigned int c
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_ismbbalnum** devuelve un valor distinto de cero si la expresión:

`isalnum(c) || _ismbbkalnum(c)`

es distinto de cero para *c*, o 0 si no lo es.

La versión de esta función con el sufijo **_l** es idéntica, excepto que utiliza la configuración regional pasada en lugar de la configuración regional actual para su comportamiento dependiente de la configuración regional.

## <a name="remarks"></a>Observaciones

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbalnum**|\<mbctype.h>|
|**_ismbbalnum_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[rutinas _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
