---
title: free
ms.date: 11/04/2016
api_name:
- free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: 7e09bec7c83eae64064e3997f2e8d5632a47258a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956730"
---
# <a name="free"></a>free

Desasigna o libera un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Bloque de memoria anteriormente asignada que se va a liberar.

## <a name="remarks"></a>Comentarios

La función **Free** desasigna un bloque de memoria (*memblock*) que se asignó previamente mediante una llamada a **calloc**, **malloc**o **realloc**. El número de bytes liberados es equivalente al número de bytes solicitado al asignar (o reasignar) el bloque, en el caso de **realloc**. Si *memblock* es **null**, el puntero se omite y se **libera** inmediatamente. Intentar liberar un puntero no válido (un puntero a un bloque de memoria que no fue asignado por **calloc**, **malloc**o **realloc**) puede afectar a las solicitudes de asignación posteriores y producir errores.

Si se produce un error al liberar memoria, **errno** se establece con información del sistema operativo sobre la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Una vez liberado un bloque de memoria, [_heapmin](heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, se resuelve de forma **gratuita** en [_free_dbg](free-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**Free** está marcado `__declspec(noalias)`, lo que significa que se garantiza que la función no modifica las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).

Para liberar la memoria asignada con [_malloca](malloca.md), use [_freea](freea.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**free**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [malloc](malloc.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
