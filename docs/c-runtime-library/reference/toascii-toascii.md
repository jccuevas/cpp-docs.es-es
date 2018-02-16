---
title: toascii, __toascii | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf4c29934d22d3f20d79650faa406f217ffdd4c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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

*c*  
Carácter que se va a convertir.

## <a name="return-value"></a>Valor devuelto

`__toascii` Convierte el valor de *c* para el código ASCII de 7 bits intervalo y devuelve el resultado. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

La rutina `__toascii` convierte el carácter especificado en un carácter ASCII al truncarlo a los 7 bits de valor inferior. No se aplica ninguna otra transformación.

La rutina `__toascii` se define como una macro, a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS. Por compatibilidad con versiones anteriores, `toascii` se define como una macro solamente cuando [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, es indefinido.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`toascii`, `__toascii`|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|

La macro `toascii` es una extensión POSIX y `__toascii` es una implementación específica de Microsoft de la extensión POSIX. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)   
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)   
[to (Funciones)](../../c-runtime-library/to-functions.md)