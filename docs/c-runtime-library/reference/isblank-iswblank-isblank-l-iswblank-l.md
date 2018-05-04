---
title: isblank, iswblank, _isblank_l, _iswblank_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
dev_langs:
- C++
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2787be85aa4e12bf22d1be14f90568891b83824
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank, iswblank, _isblank_l, _iswblank_l

Determina si un entero representa un carácter en blanco.

## <a name="syntax"></a>Sintaxis

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de un espacio o un carácter de tabulación horizontal o forma parte de un conjunto de configuración regional de caracteres que se utilizan para separar las palabras dentro de una línea de texto. **ISBLANK** devuelve un valor distinto de cero si *c* es un carácter de espacio (0 x 20) o carácter de tabulación horizontal (0 x 09). El resultado de la condición de prueba para la **isblank** depende de las funciones del **LC_CTYPE** categoría de configuración de la configuración regional; para obtener más información, vea [setlocale, _wsetlocale](setlocale-wsetlocale.md). Las versiones de estas funciones que no tienen la **_l** sufijo usan la configuración regional actual para cualquier comportamiento que dependa de la configuración regional; las versiones que tienen la **_l** sufijo son idénticas salvo que usan el configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**iswblank** devuelve un valor distinto de cero si *c* es un carácter ancho que corresponde a un espacio estándar o carácter de tabulación horizontal.

El comportamiento de **isblank** y **_isblank_l** es indefinido si *c* no es EOF o en el intervalo de 0 a 0xFF, incluidos. Cuando se usa una biblioteca de depuración CRT y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> o \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
