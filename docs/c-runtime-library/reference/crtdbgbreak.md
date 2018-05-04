---
title: _CrtDbgBreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgBreak
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
apitype: DLLExport
f1_keywords:
- _CrtDbgBreak
- CrtDbgBreak
dev_langs:
- C++
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2141b3c70755eb03e77c8f66feed482b5e86b529
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak

Establece un punto de interrupción en una determinada línea de código. (Solo se usa en modo de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>Valor devuelto

No hay ningún valor devuelto.

## <a name="remarks"></a>Comentarios

El **_CrtDbgBreak** función establece un punto de interrupción de depuración en la línea determinada de código donde reside la función. Esta función se utiliza en modo de depuración solo y depende de **_DEBUG** previamente que se está definiendo.

Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, consulte [Escribir sus propias funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
