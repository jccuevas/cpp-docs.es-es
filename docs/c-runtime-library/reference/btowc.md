---
title: btowc
ms.date: 11/04/2016
apiname:
- btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 399f56fe133a9f67ed457b435ae6c0496e1ecaa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514687"
---
# <a name="btowc"></a>btowc

Determina si un entero representa un carácter de un solo byte válido en el estado de desplazamiento inicial.

## <a name="syntax"></a>Sintaxis

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parámetros

*Carácter*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Devuelve la representación de caracteres anchos del carácter si el entero representa un carácter de un solo byte válido en el estado de desplazamiento inicial. Devuelve WEOF si el entero es EOF o no es un carácter de un solo byte válido en el estado de desplazamiento inicial. El resultado de esta función se ve afectado por el actual **LC_TYPE** configuración regional.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**btowc**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
