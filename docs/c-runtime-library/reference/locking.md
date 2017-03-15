---
title: "_locking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_locking"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_locking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_locking (función)"
  - "bytes [C++], bloquear archivo"
  - "archivos [C++], bloquear"
  - "archivos [C++], bloquear bytes"
  - "locking (función)"
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _locking
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Bloqueos ni desbloquea bytes de un archivo.  
  
## Sintaxis  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo.  
  
 *mode*  
 Acción de bloqueo para realizar.  
  
 *nbytes*  
 Número de bytes a bloquear.  
  
## Valor devuelto  
 `_locking` devuelve 0 si correctamente.  Un valor devuelto de – 1 indica el error, en este caso [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en uno de los valores siguientes.  
  
 `EACCES`  
 Infracción de bloqueo \(el archivo bloqueado ya o desbloqueó\).  
  
 `EBADF`  
 Descriptor de archivo no válido.  
  
 `EDEADLOCK`  
 Infracción de bloqueo.  Cambia cuando se especifica el indicador de `_LK_LOCK` o de `_LK_RLCK` y el archivo no se puede bloquear después de 10 intentos.  
  
 `EINVAL`  
 Un argumento no válido se asigna a `_locking`.  
  
 Si el error se debe a un parámetro incorrecto, como descriptor de archivo no válido, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Comentarios  
 La función de `_locking` bloqueos ni desbloquea los bytes *de los nbytes* del archivo especificado por `fd`.  Bloquear bytes en un archivo impide el acceso a esos bytes por otros procesos.  Todo el bloqueo o el desbloquear comienza en la posición actual del puntero de archivo y continúa para bytes siguientes *de los nbytes* .  Es posible bloquear bytes más allá del final del archivo.  
  
 *el modo* debe ser una de las constantes de manifiesto siguientes, que se definen en Locking.h.  
  
 `_LK_LOCK`  
 Bloquea los bytes especificados.  Si los bytes no puede bloquear, el programa inmediatamente intentarlo después de 1 segundo.  Si, después de 10 intentos, los bytes no puede bloquear, la constante devuelve un error.  
  
 `_LK_NBLCK`  
 Bloquea los bytes especificados.  Si los bytes no puede bloquear, la constante devuelve un error.  
  
 `_LK_NBRLCK`  
 Igual que `_LK_NBLCK`.  
  
 `_LK_RLCK`  
 Igual que `_LK_LOCK`.  
  
 `_LK_UNLCK`  
 Desbloquea los bytes especificados, que deberían haberse bloqueados previamente.  
  
 Varias regiones de un archivo que no se superponen pueden ser bloqueadas.  Una región que es desbloqueada debe haberse bloqueado previamente.  `_locking` no combina regiones adyacentes; si dos regiones bloqueadas adyacentes, cada región se debe desbloquear por separado.  Las regiones se deben bloquear sólo brevemente y deben estar desbloqueado antes de cerrar un archivo o de salir del programa.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_locking`|\<io.h y\> sistema \<\/locking.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_locking.c  
/* This program opens a file with sharing. It locks  
 * some bytes before reading them, then unlocks them. Note that the  
 * program works correctly only if the file exists.  
 */  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/locking.h>  
#include <share.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
  
int main( void )  
{  
   int  fh, numread;  
   char buffer[40];  
  
   /* Quit if can't open file or system doesn't   
    * support sharing.   
    */  
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,   
                          _S_IREAD | _S_IWRITE );  
   printf( "%d %d\n", err, fh );  
   if( err != 0 )  
      exit( 1 );  
  
   /* Lock some bytes and read them. Then unlock. */  
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )  
   {  
      long lseek_ret;  
      printf( "No one can change these bytes while I'm reading them\n" );  
      numread = _read( fh, buffer, 30 );  
      buffer[30] = '\0';  
      printf( "%d bytes read: %.30s\n", numread, buffer );  
      lseek_ret = _lseek( fh, 0L, SEEK_SET );  
      _locking( fh, LK_UNLCK, 30L );  
      printf( "Now I'm done. Do what you will with them\n" );  
   }  
   else  
      perror( "Locking failed\n" );  
  
   _close( fh );  
}  
```  
  
## Entrada: crt\_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## Resultados del ejemplo  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)