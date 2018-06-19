---
title: _CxxThrowException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd3ab2994359e99e490422fbb2f11cf28a05d6e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395665"
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

*pExceptionObject* el objeto que generó la excepción.

*pThrowInfo* la información necesaria para procesar la excepción.

## <a name="remarks"></a>Comentarios

Este método se incluye en un archivo para uso exclusivo del compilador que este usa para procesar excepciones. No llame al método directamente desde el código.

## <a name="requirements"></a>Requisitos

**Origen:** Throw.cpp

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
