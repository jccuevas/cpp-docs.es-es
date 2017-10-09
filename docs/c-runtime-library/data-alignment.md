---
title: "Alineación de datos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- data.alignment
dev_langs:
- C++
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 2dcbb5c484e92089f7a669426b9a6727d205b45d
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="data-alignment"></a>Alineación de datos
Las siguientes funciones de tiempo de ejecución de C admiten la alineación de datos.  
  
### <a name="data-alignment-routines"></a>Rutinas de alineación de datos  
  
|Rutina|Uso|  
|-------------|---------|  
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|Libera un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Libera un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (solo versión de depuración).|  
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|Asigna memoria en un límite de alineación especificado.|  
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Asigna memoria en un límite de alineación especificado con espacio adicional para un encabezado de depuración y búferes sobrescritos (solo versión de depuración).|  
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|Devuelve el tamaño de un bloque de memoria asignado en el montón.|  
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Devuelve el tamaño de un bloque de memoria asignado en el montón (solo versión de depuración).|  
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Asigna memoria en un límite de alineación especificado.|  
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Asigna memoria en un límite de alineación especificado (solo versión de depuración).|  
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (solo versión de depuración).|  
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0.|  
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0 (solo versión de depuración).|  
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md).|  
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) (solo versión de depuración).|  
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0.|  
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0 (solo versión de depuración).|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
