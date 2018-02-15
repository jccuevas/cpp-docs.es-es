---
title: _expand | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6b2bf8ba3e30165f11e3392e04519a3d49cfd4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="expand"></a>_expand
Cambia el tamaño de un bloque de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_expand(   
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
 `_expand` devuelve un puntero void al bloque de memoria reasignado. `_expand`, a diferencia de `realloc`, no puede mover un bloque para cambiarle el tamaño. Por consiguiente, si hay suficiente memoria disponible para expandir el bloque sin moverlo, el parámetro `memblock` para `_expand` es igual al valor devuelto.  
  
 `_expand` devuelve `NULL` cuando se detecta un error durante la operación. Por ejemplo, si `_expand` se usa para reducir un bloque de memoria, podría detectar daños en el montón en bloque pequeño o un puntero de bloque no válido y devolver `NULL`.  
  
 Si no hay memoria suficiente disponible para expandir el bloque hasta el tamaño especificado sin moverlo, la función devuelve `NULL`. `_expand` nunca devuelve un bloque expandido a un tamaño inferior al solicitado. Si se produce un error, `errno` indica la naturaleza del error. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para comprobar el nuevo tamaño del elemento, use `_msize`. Para obtener un puntero a un tipo distinto de `void`, use una conversión de tipo en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 La función `_expand` cambia el tamaño de un bloque de memoria asignado previamente intentando expandir o contraer el bloque sin mover su ubicación en el montón. El parámetro `memblock` apunta al principio del bloque. El parámetro `size` proporciona el nuevo tamaño del bloque (en bytes). El contenido del bloque queda sin modificar hasta el menor de los tamaños nuevos y antiguos. `memblock` no debe ser un bloque que se ha liberado.  
  
> [!NOTE]
>  En plataformas de 64 bits, puede que `_expand` no contraiga el bloque si el nuevo tamaño es menor que el tamaño actual; en concreto, si el bloque tenía un tamaño inferior a 16 KB y, por lo tanto, se había asignado al montón de baja fragmentación, `_expand` deja el bloque sin modificar y devuelve `memblock`.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `_expand` se resuelve como [_expand_dbg](../../c-runtime-library/reference/expand-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Esta función valida sus parámetros. Si `memblock` es un puntero nulo, esta función invoca a un controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`. Si `size` es mayor que `_HEAP_MAXREQ`, `errno` se establece en `ENOMEM` y la función devuelve `NULL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_expand`|\<malloc.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
```Output  
Allocate a 512 element buffer  
Allocated 512 bytes at 002C12BC  
Expanded block to 1024 bytes at 002C12BC  
```  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_msize](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)