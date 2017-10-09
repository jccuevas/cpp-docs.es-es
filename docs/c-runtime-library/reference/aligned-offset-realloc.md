---
title: _aligned_offset_realloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9b90b8b2ff057e42425825ae7d02b8d0901a5e45
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="alignedoffsetrealloc"></a>_aligned_offset_realloc
Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _aligned_offset_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero de bloque de memoria actual.  
  
 `size`  
 Tamaño de la asignación de memoria.  
  
 `alignment`  
 El valor de alineación, que debe ser un entero potencia de 2.  
  
 `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## <a name="return-value"></a>Valor devuelto  
 `_aligned_offset_realloc` devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es `NULL` si el tamaño es cero y el argumento de búfer no es `NULL`, o si no hay memoria suficiente para expandir el bloque al tamaño en cuestión. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.  
  
 `_aligned_offset_realloc` está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no modifica variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).  
  
## <a name="remarks"></a>Comentarios  
 Al igual que [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_realloc` permite alinear una estructura en un desplazamiento dentro de la estructura.  
  
 `_aligned_offset_realloc` se basa en `malloc`. Para obtener más información sobre el uso de `_aligned_offset_malloc`, consulte [malloc](../../c-runtime-library/reference/malloc.md). Si `memblock` es `NULL`, la función llama internamente a `_aligned_offset_malloc`.  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, `_aligned_offset_realloc` valida sus parámetros. Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_offset_realloc`|\<malloc.h>|  
  
## <a name="example"></a>Ejemplo  
 Para obtener más información, consulte [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)
