---
title: nan, nanf, nanl | Microsoft Docs
ms.custom: ''
ms.date: 94/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- nanf
- nan
- nanl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- nan
- nanl
- nanf
dev_langs:
- C++
helpviewer_keywords:
- nan function
- nanf function
- nanl function
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 204d59d88c97d9b0fa161fda6f64f31267c73fd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401456"
---
# <a name="nan-nanf-nanl"></a>nan, nanf, nanl

Devuelve un valor NaN reservado.

## <a name="syntax"></a>Sintaxis

```C
double nan( const char* input );
float nanf( const char* input );
long double nanl( const char* input );
```

### <a name="parameters"></a>Parámetros

*Entrada*<br/>
Valor de cadena.

## <a name="return-value"></a>Valor devuelto

El **nan** funciones devuelven un valor NaN reservado.

## <a name="remarks"></a>Comentarios

El **nan** funciones devuelven un valor de punto flotante que corresponde a un valor NaN quiet (que no sea de señalización). El *entrada* valor se omite. Para obtener información sobre cómo se representa un NaN en la salida, vea [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**NaN**, **nanf**, **nanl**|\<math.h>|\<cmath> o \<math.h>|

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
