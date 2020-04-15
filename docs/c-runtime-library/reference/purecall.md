---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: f841bc70a4a5365bb9cc6086dd752bd2a1b583ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338484"
---
# <a name="_purecall"></a>_purecall

Controlador de errores predeterminado de llamadas de función virtual pura. El compilador genera un código para llamar a esta función cuando se llama a una función miembro virtual pura.

## <a name="syntax"></a>Sintaxis

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Observaciones

La función **_purecall** es un detalle de implementación específico de Microsoft del compilador de Microsoft C++. Esta función no está diseñada para ser llamada directamente por el código; además, no tiene ninguna declaración de encabezado pública. Se documenta aquí porque se trata de una exportación pública de la biblioteca en tiempo de ejecución de C.

Una llamada a una función virtual pura es un error porque no tiene ninguna implementación. El compilador genera código para invocar la **_purecall** función de controlador de errores cuando se llama a una función virtual pura. De forma predeterminada, **_purecall** finaliza el programa. Antes de finalizar, la función **_purecall** invoca una función **_purecall_handler** si se ha establecido una para el proceso. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tenga la firma **_purecall_handler** y, a continuación, use [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) para convertirlo en el controlador actual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

La función **_purecall** no tiene una declaración de encabezado. El **_purecall_handler** typedef \<se define en stdlib.h>.

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
