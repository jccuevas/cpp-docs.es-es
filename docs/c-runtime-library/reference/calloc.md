---
title: calloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- calloc
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
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6986e1caec25cd544919039f690544af429524af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="calloc"></a>calloc

Asigna una matriz en la memoria con elementos que se inicializan en 0.

## <a name="syntax"></a>Sintaxis

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*Número*<br/>
Número de elementos.

*size*<br/>
Longitud en bytes de cada elemento.

## <a name="return-value"></a>Valor devuelto

**calloc** devuelve un puntero en el espacio asignado. Se garantiza que el espacio de almacenamiento al que apunta el valor devuelto esté alineado correctamente para el almacenamiento de todo tipo de objeto. Para obtener un puntero a un tipo distinto de **void**, use un conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **calloc** función asigna espacio de almacenamiento para una matriz de *número* elementos, cada uno de longitud *tamaño* bytes. Cada elemento se inicializa en 0.

**calloc** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc** llamadas **malloc** utilizar C++ [_set_new_mode](set-new-mode.md) función para establecer el modo de controlador nuevo. El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del controlador nuevo según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del controlador de nuevo en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **calloc** no puede asignar memoria, **malloc** llama a la rutina del controlador de nuevo en la misma forma en que la **nueva** does de operador Cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a

```C
_set_new_mode(1);
```

temprano en el programa o vincúlelo con NEWMODE.OBJ (consulte [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **calloc** se resuelve como [_calloc_dbg](calloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**calloc**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
