---
title: _purecall
ms.date: 11/04/2016
api_name:
- _purecall
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
ms.openlocfilehash: 5d62ec30731ce26c4683afc88474d4bddb63a697
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950165"
---
# <a name="_purecall"></a>_purecall

Controlador de errores predeterminado de llamadas de función virtual pura. El compilador genera un código para llamar a esta función cuando se llama a una función miembro virtual pura.

## <a name="syntax"></a>Sintaxis

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>Comentarios

La función **_purecall** es un detalle de implementación específico de Microsoft del compilador de Microsoft C++ . Esta función no está diseñada para ser llamada directamente por el código; además, no tiene ninguna declaración de encabezado pública. Se documenta aquí porque se trata de una exportación pública de la biblioteca en tiempo de ejecución de C.

Una llamada a una función virtual pura es un error, porque no tiene ninguna implementación. El compilador genera código para invocar la función de controlador de errores **_purecall** cuando se llama a una función virtual pura. De forma predeterminada, **_purecall** finaliza el programa. Antes de finalizar, la función **_purecall** invoca una función **_purecall_handler** si se ha establecido una para el proceso. Puede instalar su propia función de controlador de errores para llamadas de función virtual pura, para capturarlas con fines informativos o de depuración. Para usar su propio controlador de errores, cree una función que tenga la firma **_purecall_handler** y, a continuación, use [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) para convertirlo en el controlador actual.

## <a name="requirements"></a>Requisitos

La función **_purecall** no tiene una declaración de encabezado. La definición de tipo **_purecall_handler** se \<define en stdlib. h >.

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
