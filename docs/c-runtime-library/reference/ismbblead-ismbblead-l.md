---
title: _ismbblead, _ismbblead_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ismbblead_l
- _ismbblead
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
dev_langs:
- C++
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7833abbe4a13a2c5f012926ffcca6befdc8b52ff
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="ismbblead-ismbbleadl"></a>_ismbblead, _ismbblead_l

Prueba un carácter para determinar si es un byte inicial de un carácter multibyte.

## <a name="syntax"></a>Sintaxis

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si el entero *c* es el primer byte de un carácter multibyte.

## <a name="remarks"></a>Comentarios

Los caracteres multibyte constan de un byte inicial seguido de un byte final. Los bytes iniciales se distinguen por encontrarse en un rango concreto de un juego de caracteres determinado. Por ejemplo, en código página 932 solo, los bytes iniciales van de 0 x 81-0x9F y 0xE0 - 0xFC.

**_ismbblead** usa la configuración regional actual para el comportamiento dependiente de la configuración regional. **_ismbblead_l** es idéntica, salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Siempre devuelve false|**_ismbblead**|Siempre devuelve false|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> o \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> o \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Para las constantes de manifiesto de las condiciones de prueba.

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
