---
title: _ismbbblank, _ismbbblank_l
ms.date: 11/04/2016
apiname:
- _ismbbblank_l
- _ismbbblank
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
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
ms.openlocfilehash: c6709d5a5870c44d200b704e4a34043ff9c37226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646269"
---
# <a name="ismbbblank-ismbbblankl"></a>_ismbbblank, _ismbbblank_l

Determina si el carácter multibyte especificado es un carácter en blanco.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _ismbbblank(
   unsigned int c
);
int _ismbbblank_l(
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

**_ismbbblank** devuelve un valor distinto de cero si *c* representa un carácter de espacio (0 x 20), un carácter de tabulación horizontal (0 x 09) o un carácter específico de configuración regional que se usa para separar las palabras dentro de una línea de texto para qué **isspace** es true; de lo contrario, devuelve 0. **_ismbbblank** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional. **_ismbbblank_l** es idéntico, salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_ismbbblank**|\<mbctype.h>|
|**_ismbbblank_l**|\<mbctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
