---
title: _dup, _dup2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _dup
- _dup2
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 687c8e0d2f9f8f860e78a1c8e44cab6886e3cf04
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="dup-dup2"></a>_dup, _dup2
Crea un segundo descriptor de archivo para un archivo abierto (`_dup`), o reasigna un descriptor de archivo (`_dup2`).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _dup(   
   int fd   
);  
int _dup2(   
   int fd1,  
   int fd2   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`, `fd1`  
 Descriptores de archivo que hacen referencia al archivo abierto.  
  
 `fd2`  
 Cualquier descriptor de archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 `_dup` devuelve un descriptor de archivo nuevo. `_dup2` devuelve 0 para indicar que la operación ha sido correcta. Si se produce un error, cada función devuelve -1 y establece `errno` a `EBADF` si el descriptor de archivo no es válido o a `EMFILE` si no hay más descriptores de archivo disponibles. En el caso de un descriptor de archivo no válido, la función invoca también al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_dup` y `_dup2` asocian un segundo descriptor de archivo a un archivo abierto actualmente. Estas funciones se pueden usar para asociar un descriptor de archivo predefinido, como el de `stdout`, a otro archivo. Las operaciones en el archivo se pueden realizar con cualquiera de los dos descriptores de archivo. El tipo de acceso permitido al archivo no se ve afectado por la creación de un nuevo descriptor. `_dup` devuelve el siguiente descriptor de archivo disponible para el archivo especificado. `_dup2` obliga a `fd2` a hacer referencia al mismo archivo que `fd1`. Si `fd2` se asocia a un archivo abierto en el momento de la llamada, dicho archivo se cierra.  
  
 `_dup` y `_dup2` aceptan descriptores de archivo como parámetros. Para pasar una secuencia `(FILE *)` a cualquiera de estas funciones, use [_fileno](../../c-runtime-library/reference/fileno.md). La rutina de `fileno` devuelve el descriptor de archivo asociado actualmente al flujo especificado. En el ejemplo siguiente se muestra cómo asociar `stderr` (definido como `FILE` `*` en Stdio.h) con un descriptor de archivo:  
  
```  
int cstderr = _dup( _fileno( stderr ));  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_dup`|\<io.h>|  
|`_dup2`|\<io.h>|  
  
 La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola:`stdin`, `stdout`, y `stderr`, se deben redirigir antes de que las funciones de tiempo de ejecución de C puedan usarlos en [! Aplicaciones INCLUDEUWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_dup.c  
// This program uses the variable old to save  
// the original stdout. It then opens a new file named  
// DataFile and forces stdout to refer to it. Finally, it  
// restores stdout to its original state.  
//  
  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int old;  
   FILE *DataFile;  
  
   old = _dup( 1 );   // "old" now refers to "stdout"   
                      // Note:  file descriptor 1 == "stdout"   
   if( old == -1 )  
   {  
      perror( "_dup( 1 ) failure" );  
      exit( 1 );  
   }  
   _write( old, "This goes to stdout first\n", 26 );  
   if( fopen_s( &DataFile, "data", "w" ) != 0 )  
   {  
      puts( "Can't open file 'data'\n" );  
      exit( 1 );  
   }  
  
   // stdout now refers to file "data"   
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )  
   {  
      perror( "Can't _dup2 stdout" );  
      exit( 1 );  
   }  
   puts( "This goes to file 'data'\n" );  
  
   // Flush stdout stream buffer so it goes to correct file   
   fflush( stdout );  
   fclose( DataFile );  
  
   // Restore original stdout   
   _dup2( old, 1 );  
   puts( "This goes to stdout\n" );  
   puts( "The file 'data' contains:" );  
   _flushall();  
   system( "type data" );  
}  
```  
  
```Output  
This goes to stdout first  
This goes to stdout  
  
The file 'data' contains:  
This goes to file 'data'  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)