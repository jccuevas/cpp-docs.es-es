---
title: toascii, __toascii | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cead516a7e298e56d13d8f1a09a054057796ca64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408427"
---
# <a name="toascii-toascii"></a>toascii, __toascii

Convierte caracteres en ASCII de 7 bits por truncamiento.

## <a name="syntax"></a>Sintaxis

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a convertir.

## <a name="return-value"></a>Valor devuelto

**__toascii** convierte el valor de *c* para el código ASCII de 7 bits intervalo y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

El **__toascii** rutina convierte el carácter especificado en un carácter ASCII truncando a los 7 bits de orden inferior. No se aplica ninguna otra transformación.

El **__toascii** rutina se define como una macro, a menos que se define la macro de preprocesador _CTYPE_DISABLE_MACROS. Por compatibilidad con versiones anteriores, **toascii** se define como una macro solamente cuando [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, es indefinido.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ToAscii**, **__toascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|

El **toascii** macro es una extensión de POSIX, y **__toascii** es una implementación específica de Microsoft de la extensión POSIX. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
