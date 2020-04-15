---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332318"
---
# <a name="_set_new_mode"></a>_set_new_mode

Establece un nuevo modo de controlador para **malloc**.

## <a name="syntax"></a>Sintaxis

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parámetros

*newhandlermode*<br/>
Nuevo modo de manejador para **malloc**; valor válido es 0 o 1.

## <a name="return-value"></a>Valor devuelto

Devuelve el modo de controlador anterior establecido para **malloc**. Un valor devuelto de 1 indica que, al no asignar memoria, **malloc** anteriormente llamó a la nueva rutina de controlador; un valor devuelto de 0 indica que no lo hizo. Si el argumento *newhandlermode* no es igual a 0 o 1, devuelve -1.

## <a name="remarks"></a>Observaciones

La función **_set_new_mode** de C++ establece el nuevo modo de controlador para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error, **malloc** debe llamar a la nueva rutina de controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la nueva rutina de controlador al no asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no puede asignar memoria, **malloc** llama a la nueva rutina de controlador de la misma manera que lo hace el **operador new** cuando se produce un error por el mismo motivo. Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*. Para invalidar el valor predeterminado, llame a:

```cpp
_set_new_mode(1);
```

al principio del programa o enlace con Newmode.obj (consulte Opciones de [enlace](../../c-runtime-library/link-options.md)).

Esta función valida su parámetro. Si *newhandlermode* es algo distinto de 0 o 1, la función invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, <strong>_set_new_mode</strong> devuelve -1 y establece **errno** `EINVAL`en .

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratis](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
