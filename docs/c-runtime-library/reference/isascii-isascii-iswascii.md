---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343915"
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

### <a name="parameters"></a>Parámetros

*C*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve distinto de cero si **c** es una representación particular de un carácter ASCII. **__isascii** devuelve un valor distinto de cero si **c** es un carácter ASCII (en el intervalo 0x00 - 0x7F). **iswascii** devuelve un valor distinto de cero si **c** es una representación de caracteres anchos de un carácter ASCII. Cada una de estas rutinas devuelve 0 si **c** no satisface la condición de prueba.

## <a name="remarks"></a>Observaciones

Tanto **__isascii** como **iswascii** se implementan como macros a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS.

Por compatibilidad con versiones anteriores, **isascii** se implementa como una macro solo si [&#95;&#95;&#95;&#95;STDC](../../preprocessor/predefined-macros.md) no está definido o se define como 0; de lo contrario es indefinido.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|
|**iswascii**|C: \<wctype.h>, \<ctype.h> o \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> o \<wchar.h>|

Las funciones **isascii**, **__isascii** e **iswascii** son específicas de Microsoft. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
