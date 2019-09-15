---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950114"
---
# <a name="_query_new_mode"></a>_query_new_mode

Devuelve un entero que indica el nuevo modo de controlador establecido por **_set_new_mode** para **malloc**.

## <a name="syntax"></a>Sintaxis

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Valor devuelto

Devuelve el nuevo modo de controlador actual, es decir, 0 o 1, para **malloc**. Un valor devuelto de 1 indica que, en caso de error al asignar memoria, **malloc** llama a la nueva rutina del controlador; un valor devuelto de 0 indica que no es así.

## <a name="remarks"></a>Comentarios

La C++ función **_query_new_mode** devuelve un entero que indica el nuevo modo de controlador establecido por C++ la función [_set_new_mode](set-new-mode.md) para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error al asignar memoria, **malloc** es llamar a la rutina del nuevo controlador tal y como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error. Puede usar **_set_new_mode** para invalidar este comportamiento de modo que, en caso de error, **malloc** llame a la rutina del nuevo controlador de la misma forma que el operador **New** cuando no se puede asignar memoria. Para obtener más información, vea la descripción de los [operadores new y delete](../../cpp/new-and-delete-operators.md) en la referencia del lenguaje de C++.

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
