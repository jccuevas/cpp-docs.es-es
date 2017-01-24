---
title: "_chsize | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chsize"
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
  - "_chsize"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chsize (función)"
  - "chsize (función)"
  - "archivos [C++], cambiar el tamaño"
  - "tamaño"
  - "tamaño, de archivo (cambiar)"
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chsize
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia el tamaño de un archivo.  Una versión más segura está disponible; vea [\_chsize\_s](../../c-runtime-library/reference/chsize-s.md).  
  
## Sintaxis  
  
```  
int _chsize(   
   int fd,  
   long size   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia a un archivo abierto.  
  
 `size`  
 Nueva longitud en bytes de un archivo.  
  
## Valor devuelto  
 `_chsize` devuelve el valor 0 si el tamaño de archivo cambia correctamente.  Un valor devuelto de – 1 indica un error: `errno` se establece en `EACCES` si el archivo especificado está bloqueado y el acceso, a `EBADF` si el archivo especificado es de solo lectura o descriptor es no válido, a `ENOSPC` si no se permite ningún espacio en el dispositivo, o a `EINVAL` si `size` es menor que cero.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 La función de `_chsize` extiende o trunca el archivo asociado a `fd` con la longitud especificada por `size`.  El archivo debe estar abierto en un modo que permite escribir.  Se agregan caracteres null \(“\\0”\) si se mejora el archivo.  Si se trunca el archivo, todos los datos del final del archivo abreviado a la longitud original del archivo se pierde.  
  
 Esta función valida sus parámetros.  Si `size` es menor que cero o `fd` es un archivo dañado descriptor, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_chsize`|\<io.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_chsize.c  
// This program uses _filelength to report the size  
// of a file before and after modifying it with _chsize.  
  
#include <io.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh, result;  
   unsigned int nbytes = BUFSIZ;  
  
   // Open a file   
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,  
                 _S_IREAD | _S_IWRITE ) == 0 )  
   {  
      printf( "File length before: %ld\n", _filelength( fh ) );  
      if( ( result = _chsize( fh, 329678 ) ) == 0 )  
         printf( "Size successfully changed\n" );  
      else  
         printf( "Problem in changing the size\n" );  
      printf( "File length after:  %ld\n", _filelength( fh ) );  
      _close( fh );  
   }  
}  
```  
  
  **Longitud del archivo antes: 0**  
**Tamaño cambiado correctamente**  
**Longitud del archivo a continuación:  329678**   
## Equivalente en .NET Framework  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_sopen, \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)