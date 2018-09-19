---
title: isleadbyte, _isleadbyte_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 682cdde6983c5e590920c43418e510b9c275b34e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401023"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Determina si un carácter es el byte inicial de un carácter multibyte.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parámetros

*c*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

**isleadbyte** devuelve un valor distinto de cero si el argumento cumple la condición de prueba o 0 si no es así. En la configuración regional "C" y en un solo byte del juego de caracteres configuraciones regionales (SBCS), **isleadbyte** siempre devuelve 0.

## <a name="remarks"></a>Comentarios

El **isleadbyte** macro devuelve un valor distinto de cero si el argumento es el primer byte de un carácter multibyte. **isleadbyte** genera un resultado significativo para cualquier argumento entero comprendido entre -1 (**EOF**) a **UCHAR_MAX** (0xFF), ambos inclusive.

El tipo de argumento esperado de **isleadbyte** es **int**; si se pasa un carácter con signo, el compilador podría convertirlo en un entero por la extensión de signo y producir resultados imprevisibles.

La versión de esta función con el **_l** sufijo es idéntico, salvo que usa la configuración regional pasada en lugar de la configuración regional actual de su comportamiento dependiente de la configuración regional.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Siempre devuelve false|**_isleadbyte**|Siempre devuelve false|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Clasificación de bytes](../../c-runtime-library/byte-classification.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[_ismbb (rutinas)](../../c-runtime-library/ismbb-routines.md)<br/>
