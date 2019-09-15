---
title: toascii, __toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 09df829511b38b87cb41e32a59bee9f38a9b8f32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957472"
---
# <a name="toascii-__toascii"></a>toascii, __toascii

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

**__toascii** convierte el valor de *c* en el intervalo ASCII de 7 bits y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

La rutina **__toascii** convierte el carácter especificado en un carácter ASCII al truncarlo en los 7 bits de orden inferior. No se aplica ninguna otra transformación.

La rutina **__toascii** se define como una macro a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS. Por compatibilidad con versiones anteriores, **toascii** se define como una macro solo cuando [ &#95; &#95;stdc&#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, no está definido.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**toascii**, **__toascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|

La macro **toascii** es una extensión POSIX y **__toascii** es una implementación específica de Microsoft de la extensión POSIX. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[to (funciones)](../../c-runtime-library/to-functions.md)<br/>
