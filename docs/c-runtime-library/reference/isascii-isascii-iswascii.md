---
title: isascii, __isascii, iswascii | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
dev_langs:
- C++
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bffc46bae24689558999d188f96e5b9f8d21c54e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="isascii-isascii-iswascii"></a>isascii, __isascii, iswascii

Determina si un carácter determinado es un carácter ASCII.

## <a name="syntax"></a>Sintaxis

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si **c** es una representación concreta de un carácter ASCII. **__isascii** devuelve un valor distinto de cero si **c** es un carácter ASCII (en el intervalo 0 x 00 - 0x7F). **iswascii** devuelve un valor distinto de cero si **c** es una representación de caracteres anchos de un carácter ASCII. Cada una de estas rutinas devuelve 0 si **c** no satisface la condición de prueba.

## <a name="remarks"></a>Comentarios

Ambos **__isascii** y **iswascii** se implementan como macros a menos que se define la macro de preprocesador _CTYPE_DISABLE_MACROS.

Por compatibilidad con versiones anteriores, **isascii** se implementa como un solo si macro [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) no está definido o se define como 0; en caso contrario, es indefinido.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|
|**iswascii**|C: \<wctype.h>, \<ctype.h> o \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> o \<wchar.h>|

El **isascii**, **__isascii** y **iswascii** funciones son específicas de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
