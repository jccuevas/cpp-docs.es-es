---
title: realloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs:
- C++
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: 20
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: a3612dfc9906b23bd3581729fd1de53212fb4b1a
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="realloc"></a>realloc
Reasigna bloques de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero al bloque de memoria asignado previamente.  
  
 `size`  
 Nuevo tamaño en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 `realloc` devuelve un puntero `void` al bloque de memoria reasignado (y, probablemente, trasladado).  
  
 Si no hay memoria suficiente para expandir el bloque al tamaño determinado, el bloque original permanece inalterado y se devuelve `NULL`.  
  
 Si `size` es cero, el bloque señalado por `memblock` se libera; el valor devuelto es `NULL` y `memblock` sigue apuntando a un bloque liberado.  
  
 El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para obtener un puntero a un tipo distinto de `void`, use una conversión de tipo en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La función `realloc` cambia el tamaño de un bloque de memoria asignado. El argumento `memblock` apunta al principio del bloque de memoria. Si `memblock` es `NULL`, `realloc` se comporta del mismo modo que `malloc` y asigna un nuevo bloque de `size` bytes. Si `memblock` no es `NULL`, debe ser un puntero devuelto por una llamada anterior a `calloc`, `malloc` o `realloc`.  
  
 El argumento `size` proporciona el tamaño nuevo del bloque (en bytes). El contenido del bloque es igual hasta el más pequeño de los tamaños nuevo y antiguo, aunque el bloque nuevo puede estar en otra ubicación. Dado que el bloque nuevo puede estar en una nueva ubicación de memoria, no se garantiza que el puntero devuelto por `realloc` sea el puntero que se pasa a través del argumento `memblock`. `realloc` no establece un cero en la memoria recién asignada en el caso de un crecimiento del búfer.  
  
 `realloc` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`. Para obtener información sobre este y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `realloc` llama a `malloc` para usar la función [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) de C++ y establecer el nuevo modo de controlador. El nuevo modo de controlador indica si, en caso de error, `malloc` va a llamar a la rutina del nuevo controlador, según lo establecido por [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). De forma predeterminada, `malloc` no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando `realloc` no pueda asignar memoria, `malloc` llame a la rutina del nuevo controlador de la misma forma que hace el operador `new` cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a  
  
```  
_set_new_mode(1)  
```  
  
 temprano en un programa o vincúlelo con NEWMODE.OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `realloc` se resuelve como [_realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `realloc` está marcado como `__declspec(noalias)` y `__declspec(restrict)`, lo que significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`realloc`|\<stdlib.h> y \<malloc.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after malloc of 1000 longs: 4000  
Size of block after realloc of 1000 more longs: 8000  
```  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)
