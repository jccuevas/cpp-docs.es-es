---
title: "_lseek, _lseeki64 | Microsoft Docs"
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
  - "_lseeki64"
  - "_lseek"
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
  - "_lseeki64"
  - "_lseek"
  - "lseeki64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lseek (función)"
  - "_lseeki64 (función)"
  - "punteros a archivos [C++], mover"
  - "lseek (función)"
  - "lseeki64 (función)"
  - "buscar punteros a archivos"
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lseek, _lseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mueve un puntero de archivo en la ubicación especificada.  
  
## Sintaxis  
  
```  
  
      long _lseek(  
   int fd,  
   long offset,  
   int origin   
);  
__int64 _lseeki64(  
   int fd,  
   __int64 offset,  
   int origin   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia a un archivo abierto.  
  
 *offset*  
 Número de bytes *de origen*.  
  
 *origen*  
 Posición inicial.  
  
## Valor devuelto  
 `_lseek` devuelve la diferencia, en bytes, de la nueva posición desde el principio del archivo.  `_lseeki64` devuelve el desplazamiento en un entero de 64 bits.  La función devuelve – 1L para indicar un error.  Si se pasa un parámetro no válido, como un archivo dañado descriptor, o el valor del *origen* es no válidos o la posición especificada por *el desplazamiento* es anterior al principio del archivo, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, este `errno` establecido funciones a `EBADF` y retorno \-1L.  En los dispositivos incapaces de búsqueda \(como terminales y impresoras\), el valor devuelto es indefinido.  
  
 Para obtener más información sobre estos y otros códigos error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_lseek` mueve el puntero de archivo asociado a `fd` a una nueva ubicación que está a bytes *de desplazamiento* *de origen*.  La operación siguiente en el archivo en la nueva ubicación.  El argumento *de origen* debe ser una de las siguientes constantes, que se definen en Stdio.h.  
  
 `SEEK_SET`  
 Principio del archivo.  
  
 `SEEK_CUR`  
 Posición actual del puntero de archivo.  
  
 `SEEK_END`  
 Final de archivo.  
  
 Puede utilizar `_lseek` para colocar el puntero de nuevo en cualquier parte de un archivo o más allá del final del archivo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lseek`|\<io.h\>|  
|`_lseeki64`|\<io.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_lseek.c  
/* This program first opens a file named lseek.txt.  
 * It then uses _lseek to find the beginning of the file,  
 * to find the current position in the file, and to find  
 * the end of the file.  
 */  
  
#include <io.h>  
#include <fcntl.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh;  
   long pos;               /* Position of file pointer */  
   char buffer[10];  
  
   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );  
  
   /* Seek the beginning of the file: */  
   pos = _lseek( fh, 0L, SEEK_SET );  
   if( pos == -1L )  
      perror( "_lseek to beginning failed" );  
   else  
      printf( "Position for beginning of file seek = %ld\n", pos );  
  
   /* Move file pointer a little */  
    _read( fh, buffer, 10 );  
  
   /* Find current position: */  
   pos = _lseek( fh, 0L, SEEK_CUR );  
   if( pos == -1L )  
      perror( "_lseek to current position failed" );  
   else  
      printf( "Position for current position seek = %ld\n", pos );  
  
   /* Set the end of the file: */  
   pos = _lseek( fh, 0L, SEEK_END );  
   if( pos == -1L )  
      perror( "_lseek to end failed" );  
   else  
      printf( "Position for end of file seek = %ld\n", pos );  
  
   _close( fh );  
}  
```  
  
## Entrada: crt\_lseek.c\_input  
  
```  
Line one.  
Line two.  
Line three.  
Line four.  
Line five.  
```  
  
## Resultados  
  
```  
Position for beginning of file seek = 0  
Position for current position seek = 10  
Position for end of file seek = 57  
```  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [fseek, \_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_tell, \_telli64](../../c-runtime-library/reference/tell-telli64.md)