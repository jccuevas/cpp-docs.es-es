---
title: _CrtDbgBreak
ms.date: 11/04/2016
api_name:
- _CrtDbgBreak
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 9471b1a93abd9777c3a53c54c2517e59896d8160
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942584"
---
# <a name="_crtdbgbreak"></a>_CrtDbgBreak

Establece un punto de interrupción en una determinada línea de código. (Solo se usa en modo de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>Valor devuelto

No hay ningún valor devuelto.

## <a name="remarks"></a>Comentarios

La función **_CrtDbgBreak** establece un punto de interrupción de depuración en la línea de código determinada donde reside la función. Esta función solo se usa en modo de depuración y depende de **_ Debug** que se ha definido previamente.

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
