---
title: _query_new_mode
ms.date: 11/04/2016
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
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 327f22c847793316bd126721b4a66846d7da84dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620030"
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

Devuelve el actual nuevo modo de controlador, es decir, 0 o 1, para **malloc**. Un valor devuelto de 1 indica que, en caso de error para asignar memoria, **malloc** llama a la rutina del nuevo controlador; un valor devuelto de 0 indica que no.

## <a name="remarks"></a>Comentarios

El C++ **_query_new_mode** función devuelve un entero que indica el nuevo modo de controlador establecido por el C++ [_set_new_mode](set-new-mode.md) funcionar para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error para asignar memoria, **malloc** consiste en llamar a la rutina del nuevo controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error. Puede usar **_set_new_mode** para invalidar este comportamiento lo que en caso de error **malloc** llame a la rutina del nuevo controlador de la misma forma en que el **nuevo** operador hace cuando se produce un error asignar memoria. Para obtener más información, vea la descripción de los [operadores new y delete](../../cpp/new-and-delete-operators.md) en la referencia del lenguaje de C++.

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
