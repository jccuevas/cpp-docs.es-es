---
title: __uncaught_exception
ms.date: 11/04/2016
apiname:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 19d1e18af27722d6f9da39ebaaf6c9415c281849
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579639"
---
# <a name="uncaughtexception"></a>__uncaught_exception

Indica si se ha producido una o más excepciones, pero aún no se han manipulado por el correspondiente **catch** block de un [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) instrucción.

## <a name="syntax"></a>Sintaxis

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Valor devuelto

**True** desde el momento en que se produce una excepción un **intente** se bloquean hasta que la coincidencia de **catch** bloque está inicializado; de lo contrario, **false**.

## <a name="remarks"></a>Comentarios

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Vea también

[Instrucciones try, throw y catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
