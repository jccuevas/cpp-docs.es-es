---
title: isascii, __isascii, iswascii
ms.date: 11/04/2016
api_name:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: b7677819a4b138b08ed4ff97de38c091ce0e94fd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857793"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

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

### <a name="parameters"></a>Parameters

*c*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si **c** es una representación concreta de un carácter ASCII. **__isascii** devuelve un valor distinto de cero si **c** es un carácter ASCII (en el intervalo de 0x00 a 0x7F). **iswascii** devuelve un valor distinto de cero si **c** es una representación de caracteres anchos de un carácter ASCII. Cada una de estas rutinas devuelve 0 si **c** no cumple la condición de prueba.

## <a name="remarks"></a>Notas

Tanto **__isascii** como **iswascii** se implementan como macros, a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS.

Por compatibilidad con versiones anteriores, **isascii** se implementa como una macro solo si [ &#95; &#95;stdc&#95; ](../../preprocessor/predefined-macros.md) no está definido o está definido como 0; en caso contrario, no está definido.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|
|**iswascii**|C: \<wctype.h>, \<ctype.h> o \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> o \<wchar.h>|

Las funciones **isascii**, **__isascii** y **iswascii** son específicas de Microsoft. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
