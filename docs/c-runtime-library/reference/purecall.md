---
title: _purecall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfcd454aa6a4053ff30eef27b9c9c7d3d8bf7b34
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="purecall"></a>_purecall

Controlador de errores predeterminado de llamadas de función virtual pura. El compilador genera un código para llamar a esta función cuando se llama a una función miembro virtual pura.

## <a name="syntax"></a>Sintaxis

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Comentarios

El **_purecall** función es un detalle de implementación específicos de Microsoft del compilador de Microsoft Visual C++. Esta función no está diseñada para ser llamada directamente por el código; además, no tiene ninguna declaración de encabezado pública. Se documenta aquí porque se trata de una exportación pública de la biblioteca en tiempo de ejecución de C.

Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. El compilador genera código para invocar la **_purecall** función de controlador de errores cuando se llama a una función virtual pura. De forma predeterminada, **_purecall** finaliza el programa. Antes de terminar, la **_purecall** función invoca un **_purecall_handler** funcionar si se ha definido alguna para el proceso. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tiene el **_purecall_handler** firma, a continuación, utilice [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) para que sea el controlador actual.

## <a name="requirements"></a>Requisitos

El **_purecall** la función no tiene una declaración de encabezado. El **_purecall_handler** typedef se define en \<stdlib.h >.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
