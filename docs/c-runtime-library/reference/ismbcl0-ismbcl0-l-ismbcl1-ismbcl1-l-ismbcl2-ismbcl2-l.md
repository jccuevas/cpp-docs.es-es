---
title: _ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l
ms.date: 4/2/2020
api_name:
- _ismbcl2
- _ismbcl1
- _ismbcl0
- _ismbcl2_l
- _ismbcl1_l
- _ismbcl0_l
- _o__ismbcl0
- _o__ismbcl0_l
- _o__ismbcl1
- _o__ismbcl1_l
- _o__ismbcl2
- _o__ismbcl2_l
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
- ismbcl0
- _ismbcl1_l
- _ismbcl0
- ismbcl1
- ismbcl0_l
- _ismbcl2_l
- ismbcl2
- ismbcl1_l
- _ismbcl1
- _ismbcl0_l
- _ismbcl2
- ismbcl2_l
helpviewer_keywords:
- _ismbcl0_l function
- _ismbcl2 function
- _ismbcl1_l function
- ismbcl2 function
- _ismbcl1 function
- ismbcl0_l function
- ismbcl2_l function
- ismbcl1_l function
- ismbcl0 function
- ismbcl1 function
- _ismbcl2_l function
- _ismbcl0 function
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
ms.openlocfilehash: 813e6359d17f2ea4c6c0ded87a97c2afda243642
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919739"
---
# <a name="_ismbcl0-_ismbcl0_l-_ismbcl1-_ismbcl1_l-_ismbcl2-_ismbcl2_l"></a>_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l

**Funciones concretas de la página de códigos 932**, usando la configuración regional actual o la categoría de estado de conversión LC_CTYPE especificada.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _ismbcl0(
   unsigned int c
);
int _ismbcl0_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcl1(
   unsigned int c
);
int _ismbcl1_l(
   unsigned int c ,
   _locale_t locale
);
int _ismbcl2(
   unsigned int c
);
int _ismbcl2_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Carácter que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si *c* <= 255 y hay una rutina de **_ismbb** correspondiente (por ejemplo, **_ismbcalnum** corresponde a **_ismbbalnum**), el resultado es el valor devuelto de la rutina de **_ismbb** correspondiente.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

|Rutina|Condición de prueba (solo página de códigos 932)|
|-------------|-------------------------------------------|
|**_ismbcl0**|JIS no kanji: 0x8140<=*c*<= 0x889E.|
|**_ismbcl0_l**|JIS no kanji: 0x8140<=*c*<= 0x889E.|
|**_ismbcl1**|JIS Level-1:0x889F<=*c*<= 0x9872.|
|**_ismbcl1_l**|JIS Level-1:0x889F<=*c*<= 0x9872.|
|**_ismbcl2**|JIS LEVEL-2:0x989F<=*c*<= 0xEAA4.|
|**_ismbcl2_l**|JIS LEVEL-2:0x989F<=*c*<= 0xEAA4.|

Las funciones comprueban que el valor especificado *c* coincide con las condiciones de prueba descritas anteriormente, pero no comprueban que *c* es un carácter multibyte válido. Si el byte inferior está en los intervalos 0x00 - 0x3F, 0x7F, o 0xFD - 0xFF, estas funciones devuelven un valor distinto de cero, lo que indica que el carácter cumple la condición de prueba. Use [_ismbbtrail](ismbbtrail-ismbbtrail-l.md) para comprobar si el carácter multibyte está definido.

**Final de la página de códigos 932 específica**

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbcl0**|\<mbstring.h>|
|**_ismbcl0_l**|\<mbstring.h>|
|**_ismbcl1**|\<mbstring.h>|
|**_ismbcl1_l**|\<mbstring.h>|
|**_ismbcl2**|\<mbstring.h>|
|**_ismbcl2_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[_ismbc (Rutinas)](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
