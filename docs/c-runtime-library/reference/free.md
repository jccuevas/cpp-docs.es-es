---
title: free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- free
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
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fa01be1421c4b241a86a02e97cb444404ce8f734
ms.lasthandoff: 02/24/2017

---
# <a name="free"></a>free
Desasigna o libera un bloque de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Bloque de memoria anteriormente asignada que se va a liberar.  
  
## <a name="remarks"></a>Comentarios  
 La función `free` desasigna un bloque de memoria (`memblock`) que se había asignado previamente mediante una llamada a `calloc`, `malloc` o `realloc`. El número de bytes liberados es equivalente al número de bytes solicitado al asignar (o reasignar, en el caso de `realloc`) el bloque. Si `memblock` es `NULL`, el puntero se omite y `free` se devuelve inmediatamente. Puede que el intento de liberación de un puntero no válido (un puntero a un bloque de memoria que no se ha asignado con `calloc`, `malloc` o `realloc`) afecte a las solicitudes de asignación posteriores y provoque errores.  
  
 Si se produce un error al liberar memoria, en `errno` se muestra información sobre la naturaleza del error proporcionada por el sistema operativo. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Una vez liberado un bloque de memoria, [_heapmin](../../c-runtime-library/reference/heapmin.md) minimiza la cantidad de memoria libre en el montón al fusionar las regiones no usadas y liberarlas de nuevo en el sistema operativo. La memoria liberada que no se ha liberado en el sistema operativo se restaura en el grupo libre y vuelve a estar disponible para su asignación.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `free` se resuelve como [_free_dbg](../../c-runtime-library/reference/free-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `free` está marcado como `__declspec(noalias)`, lo que significa que se garantiza que la función no modifica las variables globales. Para obtener más información, consulte [noalias](../../cpp/noalias.md).  
  
 Para liberar la memoria asignada con [_malloca](../../c-runtime-library/reference/malloca.md), use [_freea](../../c-runtime-library/reference/freea.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`free`|\<stdlib.h> y \<malloc.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [malloc](../../c-runtime-library/reference/malloc.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_freea](../../c-runtime-library/reference/freea.md)
