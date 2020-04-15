---
title: libre
ms.date: 4/2/2020
api_name:
- free
- _o_free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345978"
---
# <a name="free"></a>libre

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

## <a name="remarks"></a>Observaciones

La función **free** desasigna un bloque de memoria (*memblock*) que se asignó previamente mediante una llamada a **calloc**, **malloc**o **realloc**. El número de bytes liberados es equivalente al número de bytes solicitados cuando se asignó el bloque (o se reasigna, en el caso de **realloc**). Si *memblock* es **NULL**, el puntero se omite y **free** devuelve inmediatamente. Intentar liberar un puntero no válido (un puntero a un bloque de memoria que no se asignó mediante **calloc**, **malloc**o **realloc**) puede afectar a las solicitudes de asignación posteriores y provocar errores.

Si se produce un error al liberar la memoria, **errno** se establece con información del sistema operativo sobre la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Una vez liberado un bloque de memoria, [_heapmin](heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **se** resuelve de forma [gratuita en _free_dbg](free-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**libre** está `__declspec(noalias)`marcado, lo que significa que se garantiza que la función no modifique las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).

Para liberar la memoria asignada con [_malloca](malloca.md), use [_freea](freea.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**Gratis**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [malloc](malloc.md).

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
