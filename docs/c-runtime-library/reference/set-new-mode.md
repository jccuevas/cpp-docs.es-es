---
title: _set_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0fa7022c5195882145452fa14e0cbf7347573a0a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

Devuelve el controlador anterior para el conjunto de modos **malloc**. A devolver el valor de 1 indica que, en caso de error para asignar memoria, **malloc** llamado previamente la rutina del controlador nuevo; un valor devuelto de 0 indica que no lo hizo. Si el *newhandlermode* argumento no es igual a 0 o 1, devuelve -1.

## <a name="remarks"></a>Comentarios

La función **_set_new_mode** de C++ establece el nuevo modo de controlador para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del controlador nuevo según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del controlador de nuevo en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no puede asignar memoria, **malloc** llama a la rutina del controlador de nuevo en la misma forma en que la **nueva** does de operador Cuando se produce un error por la misma razón. Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*. Para invalidar el valor predeterminado, llame a:

```cpp
_set_new_mode(1);
```

temprano en el programa o vincúlelo con Newmode.obj (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Esta función valida su parámetro. Si *newhandlermode* algo distinto de 0 ó 1, la función invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_ *** set_new_mode** devuelve -1 y establece **errno** a **EINVAL**.

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
