---
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: dcad8bea4f8cec28d8cb15a9937b1032593ef0cc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956710"
---
# <a name="_freea"></a>_freea

Desasigna o libera un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Bloque de memoria anteriormente asignada que se va a liberar.

## <a name="return-value"></a>Valor devuelto

Ninguno.

## <a name="remarks"></a>Comentarios

La función **_freea** desasigna un bloque de memoria (*memblock*) que se asignó previamente mediante una llamada a [_malloca](malloca.md). **_freea** comprueba si la memoria se asignó en el montón o en la pila. Si se asignó en la pila, **_freea** no hace nada. Si se ha asignado en el montón, el número de bytes liberados es equivalente al número de bytes solicitado al asignar el bloque. Si *memblock* es **null**, el puntero se omite y **_freea** vuelve inmediatamente. Intentar liberar un puntero no válido (un puntero a un bloque de memoria que no fue asignado por **_malloca**) puede afectar a las solicitudes de asignación posteriores y producir errores.

**_freea** llama a **Free** internamente si detecta que la memoria está asignada en el montón. Si la memoria está en el montón o en la pila lo determina un marcador que se coloca en la memoria en la dirección inmediatamente anterior a la memoria asignada.

Si se produce un error al liberar memoria, **errno** se establece con información del sistema operativo sobre la naturaleza del error. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Una vez liberado un bloque de memoria, [_heapmin](heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.

Una llamada a **_freea** debe acompañar a todas las llamadas a **_malloca**. También es un error llamar a **_freea** dos veces en la misma memoria. Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, especialmente con las características [_ malloc_dbg](malloc-dbg.md) habilitadas al definir _ **crtdbg_map_alloc**, es más fácil encontrar llamadas que faltan o están duplicadas en **_freea**. Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea** está marcado `__declspec(noalias)`, lo que significa que se garantiza que la función no modifica las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_freea**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_malloca](malloca.md).

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
