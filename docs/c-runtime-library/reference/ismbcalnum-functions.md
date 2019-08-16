---
title: _ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
ms.date: 11/04/2016
apiname:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
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
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
ms.openlocfilehash: 1a2f928d826b70b788220130f69c53cc351b4910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157315"
---
# <a name="ismbcalnum-ismbcalnuml-ismbcalpha-ismbcalphal-ismbcdigit-ismbcdigitl"></a>_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l

Comprueba si un carácter multibyte es un carácter alfanumérico, alfa o de dígito.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _ismbcalnum
(
   unsigned int c
);
int _ismbcalnum_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcalpha
(
   unsigned int c
);
int _ismbcalpha_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcdigit
(
   unsigned int c
);
int _ismbcdigit_l
(
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

Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si *c*< = 255 y hay correspondiente **_ismbb** rutina (por ejemplo, **_ismbcalnum** corresponde a **_ismbbalnum**), el resultado es el valor devuelto de la correspondiente **_ismbb** rutina.

## <a name="remarks"></a>Comentarios

Cada una de estas rutinas prueba si un carácter multibyte dado cumple una condición determinada.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|
|-------------|--------------------|---------------------------|
|**_ismbcalnum**, **_ismbcalnum_l**|Alfanumérico|Devuelve cero si y solo si *c* es una representación de un byte de una letra inglesa ASCII: Vea los ejemplos de **_ismbcdigit** y **_ismbcalpha**.|
|**_ismbcalpha**, **_ismbcalpha_l**|Alfabético|Devuelve cero si y solo si *c* es una representación de un byte de una letra inglesa ASCII: 0 x 41 < =*c*< = 0x5A o 0 x 61 < =*c*< = 0x7A; o una letra katakana: 0xA6<=*c*<=0xDF.|
|**_ismbcdigit**, **_ismbcdigit**|Dígito|Devuelve cero si y solo si *c* es una representación de un byte de un dígito ASCII: 0x30<=*c*<=0x39.|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbcalnum**, **_ismbcalnum_l**|\<mbstring.h>|
|**_ismbcalpha**, **_ismbcalpha_l**|\<mbstring.h>|
|**_ismbcdigit**, **_ismbcdigit_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[_ismbc (rutinas)](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
