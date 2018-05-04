---
title: _query_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8907b043e8b4441d6e5213a1d386dbc1a5a6910a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="querynewmode"></a>_query_new_mode

Devuelve un entero que indica el nuevo modo de controlador establecido por **_set_new_mode** para **malloc**.

## <a name="syntax"></a>Sintaxis

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Valor devuelto

Devuelve el modo controlador nuevo actual, es decir, 0 o 1, para **malloc**. A devolver el valor de 1 indica que, en caso de error para asignar memoria, **malloc** llama a la rutina del controlador nuevo; un valor devuelto de 0 indica que no es así.

## <a name="remarks"></a>Comentarios

C++ **_query_new_mode** función devuelve un entero que indica el nuevo modo de controlador establecido por el C++ [_set_new_mode](set-new-mode.md) funcionar por [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error para asignar memoria, **malloc** consiste en llamar a la rutina del controlador nuevo según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del controlador de nuevo en caso de error. Puede usar **_set_new_mode** para invalidar este comportamiento de modo que en caso de error **malloc** llama a la rutina del controlador de nuevo en la misma forma en que la **nueva** operador realiza cuando se produce un error asignar memoria. Para obtener más información, vea la descripción de los [operadores new y delete](../../cpp/new-and-delete-operators.md) en la referencia del lenguaje de C++.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
