---
title: "ftell, _ftelli64 | Microsoft Docs"
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
  - "_ftelli64"
  - "ftell"
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
  - "_ftelli64"
  - "ftell"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftelli64 (función)"
  - "punteros a archivos [C++]"
  - "punteros a archivos [C++], obtener posición actual"
  - "ftell (función)"
  - "ftelli64 (función)"
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ftell, _ftelli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la posición actual de un puntero de archivo.  
  
## Sintaxis  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Estructura de `FILE` de destino.  
  
## Valor devuelto  
 `ftell` y `_ftelli64` devuelven la posición del archivo actual.  El valor devuelto por `ftell` y `_ftelli64` puede no reflejar el desplazamiento de bytes físico para las secuencias abierto en modo de texto, porque el modo de texto produce la traducción de retorno\- avance de línea de carro.  Utilice `ftell` con `fseek`o`_ftelli64`con`_fseeki64` para volver a las ubicaciones del archivo correctamente.  Por error, `ftell`y`_ftelli64` se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven – 1L y `errno` determinado a una de dos constantes, definido en ERRNO.H.  La constante de `EBADF` significa que el argumento de `stream` no es un valor válido del puntero de archivo ni que hace referencia a un archivo abierto.  `EINVAL` significa que un argumento no válido de `stream` pasado a la función.  En los dispositivos incapaces de búsqueda \(como terminales y impresoras\), o cuando `stream` no hace referencia a un archivo abierto, el valor devuelto es indefinido.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 Las funciones de `ftell` yde `_ftelli64`recuperan la posición actual del puntero de archivo \(si existe\) asociado a *`stream`.* La posición se expresa como un desplazamiento en relación con el principio de la secuencia.  
  
 Observe que si se abre para anexar datos, la posición del archivo actual está determinada por la operación de E\/S última, no por donde escribir siguiente aparecería.  Por ejemplo, si un archivo se abre para un anexar y la última operación fuera una lectura, la posición del archivo es el punto donde la operación de lectura siguiente comenzaría, no donde escribir siguiente comenzaría. \(Si se abre para anexar, la posición del archivo se mueve al final de archivo antes de cualquier operación de escritura\). Si ninguna operación de E\/S todavía ha producido en un archivo abierto para anexar, la posición del archivo es el principio del archivo.  
  
 En modo de texto, CTRL\+Z se interpretan como un final de archivo de entrada.  En archivos abierto para lectura\/escritura, `fopen` y toda la comprobación para de rutinas relacionada un CTRL\+Z al final del archivo y quítelo si es posible.  Se hace esto porque utilizar la combinación de `ftell` y `fseek` o `_ftelli64` y `_fseeki64`, para desplazarse en un archivo que finaliza con un CTRL\+Z puede hacer `ftell` o `_ftelli64` para comportarse incorrectamente cerca del final del archivo.  
  
 Esta función bloquea el subproceso de llamada durante la ejecución y por consiguiente seguro para subprocesos.  Para consultar una versión que no realiza el bloqueo, vea `_ftell_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezados opcionales|  
|-------------|--------------------------|----------------------------|  
|`ftell`|\<stdio.h\>|\<errno.h\>|  
|`_ftelli64`|\<stdio.h\>|\<errno.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
  **Colocar después de intentar leer 100 bytes: 100**   
## Equivalente en .NET Framework  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, \_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)