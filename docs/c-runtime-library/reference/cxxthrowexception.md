---
title: _CxxThrowException
ms.date: 11/04/2016
apiname:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: 925b72a120b31029b76fa38bee73eea003511cd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550338"
---
# <a name="cxxthrowexception"></a>_CxxThrowException

Genera el registro de excepciones y llama al entorno de tiempo de ejecución para iniciar el procesamiento de la excepción.

## <a name="syntax"></a>Sintaxis

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>Parámetros

*pExceptionObject*<br/>
Objeto que ha generado la excepción.

*pThrowInfo*<br/>
Información necesaria para procesar la excepción.

## <a name="remarks"></a>Comentarios

Este método se incluye en un archivo para uso exclusivo del compilador que este usa para procesar excepciones. No llame al método directamente desde el código.

## <a name="requirements"></a>Requisitos

**Origen:** Throw.cpp

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
