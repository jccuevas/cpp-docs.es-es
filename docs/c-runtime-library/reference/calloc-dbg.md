---
title: _calloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: 18
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
ms.openlocfilehash: f505aa045dcee661bfddec2ed1d01a7b77efcc51
ms.lasthandoff: 02/24/2017

---
# <a name="callocdbg"></a>_calloc_dbg
Asigna varios bloques de memoria del montón con espacio adicional para un encabezado de depuración y búferes sobrescritos (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_calloc_dbg(   
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `num`  
 Número de bloques de memoria solicitado.  
  
 `size`  
 Tamaño de cada bloque de memoria solicitado (bytes).  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o `NULL`.  
  
 Los parámetros `filename` y `linenumber` solo están disponibles cuando se ha llamado a `_calloc_dbg` explícitamente o se ha definido la constante de preprocesador [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Cuando se lleva a cabo correctamente, esta función devuelve un puntero a la parte del usuario del último bloque de memoria asignado, llama a la nueva función de controlador o devuelve `NULL`. Para obtener una descripción completa del comportamiento de retorno, vea la sección de comentarios. Para obtener más información sobre cómo se usa la nueva función de controlador, consulte la función [calloc](../../c-runtime-library/reference/calloc.md).  
  
## <a name="remarks"></a>Comentarios  
 `_calloc_dbg` es una versión de depuración de la función [calloc](../../c-runtime-library/reference/calloc.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_calloc_dbg` se reduce a una llamada a `calloc`. `calloc` y `_calloc_dbg` asignan los bloques de memoria `num` del montón base, pero `_calloc_dbg` proporciona varias características de depuración:  
  
-   Búferes situados a cada lado de la parte del usuario del bloque para comprobar si hay pérdidas.  
  
-   Un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación específicos.  
  
-   Información de `filename`/`linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_calloc_dbg` asigna cada bloque de memoria con un poco más de espacio que el `size` solicitado. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_calloc_dbg` establece `errno` en `ENOMEM` si se produce un error de asignación de memoria. Se devuelve `EINVAL` si la cantidad de memoria necesaria (incluida la sobrecarga ya mencionada) es mayor que `_HEAP_MAXREQ`. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y llamar a su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_calloc_dbg`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_callocd.c  
/*  
 * This program uses _calloc_dbg to allocate space for  
 * 40 long integers. It initializes each element to zero.  
 */  
#include <stdio.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *bufferN, *bufferC;  
  
        /*   
         * Call _calloc_dbg to include the filename and line number  
         * of our allocation request in the header and also so we can  
         * allocate CLIENT type blocks specifically  
         */  
        bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );  
        if( bufferN != NULL && bufferC != NULL )  
              printf( "Allocated memory successfully\n" );  
        else  
              printf( "Problem allocating memory\n" );  
  
        /*   
         * _free_dbg must be called to free CLIENT type blocks  
         */  
        free( bufferN );  
        _free_dbg( bufferC, _CLIENT_BLOCK );  
}  
```  
  
```Output  
Allocated memory successfully  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [_DEBUG](../../c-runtime-library/debug.md)
