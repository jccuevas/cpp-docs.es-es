---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 11/04/2016
apiname:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: c5eb0b51cf0371100ed884221ee04885dfbe9ad9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563168"
---
# <a name="isctype-iswctype-isctypel-iswctypel"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Pruebas *c* para la propiedad ctype especificada por el *desc* argumento. Para cada valor válido de *desc*, hay una rutina de clasificación de caracteres anchos equivalente.

## <a name="syntax"></a>Sintaxis

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

*DESC*<br/>
Propiedad que se va a probar. Normalmente se recupera mediante ctype o [wctype](wctype.md).

*locale*<br/>
Configuración regional que se va a usar para las pruebas dependientes de la configuración regional.

## <a name="return-value"></a>Valor devuelto

**_isctype** y **iswctype** devuelven un valor distinto de cero si *c* tiene la propiedad especificada por *desc* en la configuración regional actual o 0 si no es así. Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El comportamiento de **_isctype** y **_isctype_l** es indefinido si *c* no es EOF o en el intervalo de 0 a 0xFF, incluidos. Cuando se usa una biblioteca de depuración CRT y *c* no es uno de estos valores, las funciones generan una aserción.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|N/D|**_isctype**|N/D|**_iswctype**|
|N/D|**_isctype_l**|N/D|**_iswctype_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h> o \<wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
