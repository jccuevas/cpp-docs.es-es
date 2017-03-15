---
title: "_read | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_read"
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
  - "_read"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_read (función)"
  - "datos [C++], leer"
  - "datos [CRT]"
  - "archivos [C++], leer"
  - "read (función)"
  - "leer datos [C++]"
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _read
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos de un archivo.  
  
## Sintaxis  
  
```  
  
      int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
 *buffer*  
 Ubicación de almacenamiento de los datos.  
  
 *count*  
 Número de bytes máximo.  
  
## Valor devuelto  
 \_**read** devuelve el número de bytes leídos, que puede ser menor que *cuenta* si hay menos que los bytes que quedan en el archivo o si el archivo se abre en modo de texto, en cuyo caso cada par de fuentes de la retorno\- línea de carro \(CR\-LF\) se reemplaza por un único carácter de avance de línea.  Sólo el único carácter de avance de línea se cuenta en el valor devuelto.  El reemplazo no afecta al puntero de archivo.  
  
 Si la función intenta leer al final del archivo, devuelve 0.  Si `fd` no es válido, el archivo no está abierto para lectura, o el archivo está bloqueado, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve – 1 y establece `errno` a `EBADF`.  
  
 Si *el búfer* es **nulo**, se invoca el controlador no válido del parámetro.  Si la ejecución puede continuar, la función devuelve \-1 y `errno` se establece en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_read` lee un número máximo de bytes del *recuento* en *el búfer* de archivo asociado a `fd`.  La operación de lectura comienza en la posición actual del puntero de archivo asociado al archivo especificado.  Después de la operación de lectura, los puntos de ese puntero al carácter no leídos siguiente.  
  
 Si el archivo se abre en modo de texto, lectura finaliza cuando `_read` encuentra un carácter de CTRL\+Z, que se trata como un mensaje de fin de archivo.  Uso [\_lseek](../../c-runtime-library/reference/lseek-lseeki64.md) de borrar la marca de fin de archivo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_read`|\<io.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
## Entrada: crt\_read.txt  
  
```  
Line one.  
Line two.  
```  
  
## Resultados  
  
```  
Read 19 bytes from file  
```  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_write](../../c-runtime-library/reference/write.md)