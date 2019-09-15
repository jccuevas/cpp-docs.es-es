---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: b01aaf29ff0cd3994c45433db9ff0b9f4ca7481c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953643"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace, iswspace, _isspace_l, _iswspace_l

Determina si un entero representa un carácter de espacio.

## <a name="syntax"></a>Sintaxis

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
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

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de un carácter de espacio. **isspace** devuelve un valor distinto de cero si *c* es un carácter de espacio en blanco (0x09-0x0D o 0x20). El resultado de la condición de prueba para la función **isspace** depende del valor de la categoría **LC_CTYPE** de la configuración regional. vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones que no tienen el sufijo **_L** usan la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo **_L** son idénticas, salvo que usan la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**iswspace** devuelve un valor distinto de cero si *c* es un carácter ancho que corresponde a un carácter de espacio en blanco estándar.

El comportamiento de **isspace** y **_isspace_l** es undefined si *c* no es EOF o en el intervalo de 0 a 0xFF, ambos incluidos. Cuando se usa una biblioteca CRT de depuración y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<ctype.h> o \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
