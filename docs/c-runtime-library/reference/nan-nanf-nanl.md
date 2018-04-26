---
title: nan, nanf, nanl | Microsoft Docs
ms.custom: ''
ms.date: 94/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2fa378cdded71f0f99ad0fbe152d1282c9e6fe4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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
