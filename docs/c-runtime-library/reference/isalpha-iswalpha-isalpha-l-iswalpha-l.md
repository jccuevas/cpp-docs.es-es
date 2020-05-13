---
title: isalpha, iswalpha, _isalpha_l, _iswalpha_l
ms.date: 4/2/2020
api_name:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
- _o_isalpha
- _o_iswalpha
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
ms.openlocfilehash: abce570aecc307efd4986fab78d45954d7a79588
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919798"
---
# <a name="isalpha-iswalpha-_isalpha_l-_iswalpha_l"></a>isalpha, iswalpha, _isalpha_l, _iswalpha_l

Determina si un entero representa un carácter alfabético.

## <a name="syntax"></a>Sintaxis

```C
int isalpha(
   int c
);
int iswalpha(
   wint_t c
);
int _isalpha_l(
   int c,
   _locale_t locale
);
int _iswalpha_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Entero que se va a probar.

*locale*<br/>
Configuración regional que se va a usar en lugar de la configuración regional actual.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si *c* es una representación concreta de un carácter alfabético. **isalpha** devuelve un valor distinto de cero si *c* está dentro de los intervalos a-z o a-z. **iswalpha** devuelve un valor distinto de cero solo para caracteres anchos para los que [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) o **iswlower** es distinto de cero; es decir, para cualquier carácter ancho que sea uno de un conjunto definido por la implementación para el que ninguno de **iswcntrl**, **iswdigit**, **iswpunct**o **iswspace** sea distinto de cero. Cada una de estas rutinas devuelve 0 si *c* no cumple la condición de prueba.

Las versiones de estas funciones que tienen el sufijo **_L** utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **isalpha** y **_isalpha_l** es undefined si *c* no es EOF o en el intervalo comprendido entre 0 y 0xFF, ambos incluidos. Cuando se usa una biblioteca CRT de depuración y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha**|
|**_istalpha_l**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l**|

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha**|\<ctype.h> o \<wchar.h>|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l**|\<ctype.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
