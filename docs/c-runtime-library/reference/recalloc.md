---
title: _recalloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 9
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
ms.openlocfilehash: 89626019b42a478b2dfe3800e2f732ba6b90d106
ms.lasthandoff: 02/24/2017

---
# <a name="recalloc"></a>_recalloc
Combinación de `realloc` y `calloc`. Reasigna una matriz en la memoria e inicializa sus elementos a 0.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero al bloque de memoria asignado previamente.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Longitud en bytes de cada elemento.  
  
## <a name="return-value"></a>Valor devuelto  
 `_recalloc` devuelve un puntero `void` al bloque de memoria reasignado (y, probablemente, trasladado).  
  
 Si no hay memoria suficiente para expandir el bloque al tamaño determinado, el bloque original permanece inalterado y se devuelve `NULL`.  
  
 Si el tamaño solicitado es cero, el bloque señalado por `memblock` se libera; el valor devuelto es `NULL` y `memblock` sigue apuntando a un bloque liberado.  
  
 El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de `void`, use una conversión de tipo en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La función _`recalloc` cambia el tamaño de un bloque de memoria asignado. El argumento `memblock` apunta al principio del bloque de memoria. Si `memblock` es `NULL`, \_`recalloc` se comporta del mismo modo que [calloc](../../c-runtime-library/reference/calloc.md) y asigna un nuevo bloque de `num` * `size` bytes. Cada elemento se inicializa en 0. Si `memblock` no es `NULL`, debe ser un puntero devuelto por una llamada anterior a `calloc`, [malloc](../../c-runtime-library/reference/malloc.md) o [realloc](../../c-runtime-library/reference/realloc.md).  
  
 Dado que el bloque nuevo puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por _`recalloc` sea el puntero que se pasa a través del argumento `memblock`.  
  
 `_recalloc` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `recalloc` llama a `realloc` para usar la función [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) de C++ y establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, `realloc` va a llamar a la rutina del nuevo controlador, según lo establecido por [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). De forma predeterminada, `realloc` no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando _`recalloc` no pueda asignar memoria, `realloc` llame a la rutina del nuevo controlador de la misma forma que hace el operador `new` cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a  
  
```  
_set_new_mode(1)  
```  
  
 temprano en el programa o vincúlelo con NEWMODE.OBJ.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, _`recalloc` se resuelve como [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_recalloc` está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_recalloc`|\<stdlib.h> y \<malloc.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [_recalloc_dbg](../../c-runtime-library/reference/recalloc-dbg.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)   
 [_aligned_offset_recalloc](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [Opciones de vínculo](../../c-runtime-library/link-options.md)
