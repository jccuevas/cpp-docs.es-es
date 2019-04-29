---
title: _ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
ms.date: 11/04/2016
apiname:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
ms.openlocfilehash: d2a5d0336e5ed4ad8bbb19f8a259128ab33d004e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286738"
---
# <a name="ismbchira-ismbchiral-ismbckata-ismbckatal"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l

**Funciones concretas de la página de códigos 932**

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _ismbchira(
   unsigned int c
);
int _ismbchira_l(
   unsigned int c,
   _locale_t locale
);
int _ismbckata(
   unsigned int c
);
int _ismbckata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Carácter que se va a probar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si *c* < = 255 y hay correspondiente **_ismbb** rutina (por ejemplo, **_ismbcalnum** corresponde a **_ismbbalnum**), el resultado es el valor devuelto de la correspondiente **_ismbb** rutina.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

|Rutina|Condición de prueba (solo página de códigos 932)|
|-------------|-------------------------------------------|
|**_ismbchira**|Hiragana de doble byte: 0x829F<=*c*<=0x82F1.|
|**_ismbchira_l**|Hiragana de doble byte: 0x829F<=*c*<=0x82F1.|
|**_ismbckata**|Katakana de doble byte: 0x8340<=*c*<=0x8396.|
|**_ismbckata_l**|Katakana de doble byte: 0x8340<=*c*<=0x8396.|

**Información específica de la página de códigos de fin 932**

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbchira**|\<mbstring.h>|
|**_ismbchira_l**|\<mbstring.h>|
|**_ismbckata**|\<mbstring.h>|
|**_ismbckata_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[_ismbc (rutinas)](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
