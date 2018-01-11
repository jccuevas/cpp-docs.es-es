---
title: _freea | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _freea
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
apitype: DLLExport
f1_keywords:
- freea
- _freea
dev_langs: C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 921687fbc5d8ab0b509e5a2e43c9c9ff4b18727a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="freea"></a>_freea
Desasigna o libera un bloque de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Bloque de memoria anteriormente asignada que se va a liberar.  
  
## <a name="return-value"></a>Valor devuelto  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 La función `_freea` desasigna un bloque de memoria (`memblock`) que se había asignado previamente mediante una llamada a [_malloca](../../c-runtime-library/reference/malloca.md). `_freea` comprueba si la memoria se ha asignado en el montón o en la pila. Si se ha asignado en la pila, `_freea` no hace nada. Si se ha asignado en el montón, el número de bytes liberados es equivalente al número de bytes solicitado al asignar el bloque. Si `memblock` es `NULL`, el puntero se omite y `_freea` se devuelve inmediatamente. Puede que el intento de liberación de un puntero no válido (un puntero a un bloque de memoria que no se ha asignado con `_malloca`) afecte a las solicitudes de asignación posteriores y provoque errores.  
  
 `_freea`llamadas `free` internamente si detecta que la memoria está asignada en el montón. Si la memoria está en el montón o en la pila lo determina un marcador que se coloca en la memoria en la dirección inmediatamente anterior a la memoria asignada.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Una vez liberado un bloque de memoria, [_heapmin](../../c-runtime-library/reference/heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.  
  
 Una llamada a `_freea` debe ir acompañada de todas las llamadas a `_malloca`. También es un error llamar dos veces a `_freea` en la misma memoria. Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, especialmente con características [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) habilitadas mediante la definición de `_CRTDBG_MAP_ALLOC`, resulta más fácil encontrar llamadas a `_freea` que faltan o están duplicadas. Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_freea` está marcado como `__declspec(noalias)`, lo que significa que se garantiza que la función no modifica las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h> y \<malloc.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [_malloca](../../c-runtime-library/reference/malloca.md).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)