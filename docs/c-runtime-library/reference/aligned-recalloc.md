---
title: _aligned_recalloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 9fbaae148ea373287991ebccbf53a5a859475d0c
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="alignedrecalloc"></a>_aligned_recalloc
Cambia el tamaño de un bloque de memoria que se ha asignado con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) e inicializa la memoria a 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _aligned_recalloc(  
   void *memblock,   
   size_t num,  
   size_t size,   
   size_t alignment  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `memblock`  
 Puntero de bloque de memoria actual.  
  
 [in] `num`  
 Número de elementos.  
  
 [in] `size`  
 Tamaño en bytes de cada elemento.  
  
 [in] `alignment`  
 El valor de alineación, que debe ser un entero potencia de 2.  
  
## <a name="return-value"></a>Valor devuelto  
 `_aligned_recalloc` devuelve un puntero void al bloque de memoria reasignado (y, probablemente, trasladado). El valor devuelto es `NULL` si el tamaño es cero y el argumento de búfer no es `NULL`, o si no hay memoria suficiente para expandir el bloque al tamaño en cuestión. En el primer caso, se libera el bloque original. En el segundo, el bloque original permanece inalterado. El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto a void, use una conversión de tipo en el valor devuelto.  
  
 Es un error reasignar memoria y cambiar la alineación del bloque.  
  
## <a name="remarks"></a>Comentarios  
 `_aligned_recalloc` se basa en `malloc`. Para obtener más información sobre el uso de `_aligned_offset_malloc`, consulte [malloc](../../c-runtime-library/reference/malloc.md).  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, `_aligned_recalloc` valida sus parámetros. Si `alignment` no es una potencia de 2, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_recalloc`|\<malloc.h>|  
  
## <a name="see-also"></a>Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)   
 [_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)
