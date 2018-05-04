---
title: _ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
dev_langs:
- C++
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d2bd03eb230d85a1f93038d50566b8ccae468a5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l

Comprueba si un carácter multibyte es un carácter o símbolo válido.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
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

Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple. Si *c*< = 255 y hay un correspondiente **_ismbb** rutina (por ejemplo, **_ismbcalnum** corresponde a **_ismbbalnum**), el resultado es el valor devuelto de los correspondientes **_ismbb** rutina.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|Multibyte válido|Devuelve cero si y solo si el primer byte de *c* está dentro de los intervalos 0 x 81-0x9F o 0xE0 - 0xFC, y el segundo byte está dentro de los intervalos 0 x 40-0x7E o 0 x 80 - FC.|
|**_ismbcsymbol**|Símbolo multibyte|Devuelve cero si y solo si 0x8141 < =*c*< = 0x81AC.|

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|Siempre devuelve false|**_ismbclegal**|Siempre devuelve false.|
|**_istlegal_l**|Siempre devuelve false|**_ismbclegal_l**|Siempre devuelve false.|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbclegal**, **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol**, **_ismbcsymbol_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de caracteres](../../c-runtime-library/character-classification.md)<br/>
[_ismbc (rutinas)](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw (rutinas)](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
