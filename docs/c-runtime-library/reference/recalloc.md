---
title: _recalloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _recalloc
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
- _recalloc
- recalloc
dev_langs:
- C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c4ae06fbd3d10f1014fe1c879b482f30302a4f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="recalloc"></a>_recalloc

Una combinación de **realloc** y **calloc**. Reasigna una matriz en la memoria e inicializa sus elementos a 0.

## <a name="syntax"></a>Sintaxis

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria asignado previamente.

*Número*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**_recalloc** devuelve un **void** puntero al bloque de memoria reasignado (y, probablemente, trasladado).

Si no hay memoria suficiente para expandir el bloque al tamaño especificado, el bloque original se permanecen sin cambios, y **NULL** se devuelve.

Si el tamaño solicitado es cero, el bloque que señala *memblock* se libera; el valor devuelto es **NULL**, y *memblock* haciendo referencia a un bloque liberado.

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use un conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **_recalloc** función cambia el tamaño de un bloque de memoria asignado. El *memblock* argumento apunta al principio del bloque de memoria. Si *memblock* es **NULL**, **_recalloc** se comporta del mismo modo que [calloc](calloc.md) y asigna un nuevo bloque de *número*  *  *tamaño* bytes. Cada elemento se inicializa en 0. Si *memblock* no **NULL**, debe ser un puntero devuelto por una llamada anterior a **calloc**, [malloc](malloc.md), o [realloc ](realloc.md).

Dado que el nuevo bloque puede ser en una nueva ubicación de memoria, el puntero devuelto por **_recalloc** no se garantiza que el puntero que se pasa a través de la *memblock* argumento.

**_recalloc** establece **errno** a **ENOMEM** si se produce un error en la asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** llamadas **realloc** para poder usar C++ [_set_new_mode](set-new-mode.md) función para establecer el modo de controlador nuevo. El nuevo modo de controlador indica si, en caso de error, **realloc** consiste en llamar a la rutina del controlador nuevo según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **realloc** no llama a la rutina del controlador de nuevo en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **_recalloc** no puede asignar memoria, **realloc** llama a la rutina del controlador de nuevo en la misma forma en que la **nueva** (operador) realiza cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincúlelo con NEWMODE.OBJ.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **_recalloc** se resuelve como [_recalloc_dbg](recalloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[Opciones de vínculo](../../c-runtime-library/link-options.md)<br/>
