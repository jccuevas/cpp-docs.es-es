---
title: _ismbbalpha, _ismbbalpha_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbbalpha
- _ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
dev_langs:
- C++
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fa4708cf4c5c297d5a537728d4e5988f21e21b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ismbbalpha-ismbbalphal"></a>_ismbbalpha, _ismbbalpha_l

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

*c*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_ismbbalpha** devuelve un valor distinto de cero si la expresión:

`isalpha(c) || _ismbbkalnum(c)`

es distinto de cero para *c*, o 0 si no lo está. **_ismbbalpha** usa la configuración regional actual para cualquier configuración de caracteres dependientes de la configuración regional. **_ismbbalpha_l** es idéntica, salvo que usa la configuración regional pasada en.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
