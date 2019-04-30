---
title: _set_new_mode
ms.date: 11/04/2016
apiname:
- _set_new_mode
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
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 0228170e4ab5b55b4b061fa61a412766de77a063
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356607"
---
# <a name="setnewmode"></a>_set_new_mode

Establece un nuevo modo de controlador para **malloc**.

## <a name="syntax"></a>Sintaxis

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parámetros

*newhandlermode*<br/>
Nuevo modo de controlador para **malloc**; válido valor es 0 o 1.

## <a name="return-value"></a>Valor devuelto

Devuelve el controlador anterior para el conjunto de modos **malloc**. Un valor devuelto de 1 indica que, en caso de error para asignar memoria, **malloc** llamaban la rutina del nuevo controlador; un valor devuelto de 0 indica que no es así. Si el *newhandlermode* argumento no es igual a 0 o 1, devuelve -1.

## <a name="remarks"></a>Comentarios

La función **_set_new_mode** de C++ establece el nuevo modo de controlador para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del nuevo controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error para asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no puede asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma forma en que el **nuevo** operador Cuando se produce un error por la misma razón. Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*. Para invalidar el valor predeterminado, llame a:

```cpp
_set_new_mode(1);
```

temprano en el programa o vincúlelo con Newmode.obj (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Esta función valida su parámetro. Si *newhandlermode* algo distinto de 0 o 1, la función invoca al controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, <strong>_set_new_mode</strong> devuelve -1 y establece **errno** a `EINVAL`.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
