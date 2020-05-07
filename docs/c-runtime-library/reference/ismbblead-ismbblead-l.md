---
title: _ismbblead, _ismbblead_l
description: Describe las funciones _ismbblead y _ismbblead_l de la biblioteca en tiempo de ejecución de Microsoft C (CRT).
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: 7680793b71c4535ed75433ac98167e52a39896ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918668"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

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

*unidad*\
Entero que se va a probar.

*configuración regional*\
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un valor distinto de cero si el entero *c* es el primer byte de un carácter multibyte.

## <a name="remarks"></a>Observaciones

Los caracteres multibyte constan de un byte inicial seguido de un byte final. Los bytes iniciales se distinguen por encontrarse en un rango concreto de un juego de caracteres determinado. Por ejemplo, en la página de códigos 932 solo, los bytes iniciales van de 0x81-0x9F y 0xE0-0xFC.

**_ismbblead** usa la configuración regional actual para el comportamiento dependiente de la configuración regional. **_ismbblead_l** es idéntico, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Cuando la configuración regional es UTF-8, **_ismbblead** y **_ismbblead_l** siempre devuelven 0 (false), tanto si *c* es un byte inicial como si no.

**_ismbblead** y **_ismbblead_l** son específicos de Microsoft, no forman parte de la biblioteca estándar de C. No se recomienda usarlas donde quiera código portable. Para la compatibilidad estándar de C, use **mbrlen** en su lugar.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)\
[_ismbb rutinas](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
