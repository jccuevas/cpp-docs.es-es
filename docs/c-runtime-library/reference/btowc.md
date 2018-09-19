---
title: btowc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d0e56649218e6249550638af4e198cbd1284bc2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393321"
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
