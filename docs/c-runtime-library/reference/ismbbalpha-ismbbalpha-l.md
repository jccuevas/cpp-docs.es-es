---
title: _ismbbalpha, _ismbbalpha_l
ms.date: 4/2/2020
api_name:
- _ismbbalpha
- _ismbbalpha_l
- _o__ismbbalpha
- _o__ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
ms.openlocfilehash: 1fa92d8e0f0ed331110666add1015fbdacf20f07
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917499"
---
# <a name="_ismbbalpha-_ismbbalpha_l"></a>_ismbbalpha, _ismbbalpha_l

Determina si un carácter multibyte especificado es alfa.

## <a name="syntax"></a>Sintaxis

```C
int _ismbbalpha(
   unsigned int c
);
int _ismbbalpha_l(
   unsigned int c
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_ismbbalpha** devuelve un valor distinto de cero si la expresión:

`isalpha(c) || _ismbbkalnum(c)`

es distinto de cero para *c*, o 0 si no lo es. **_ismbbalpha** usa la configuración regional actual para los valores de caracteres dependientes de la configuración regional. **_ismbbalpha_l** es idéntico, salvo que usa la configuración regional que se pasa.

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulta también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb rutinas](../../c-runtime-library/ismbb-routines.md)<br/>
