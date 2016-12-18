---
title: "fread_s | Microsoft Docs"
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
  - "fread_s"
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
  - "fread_s"
  - "stdio/fread_s"
dev_langs: 
  - "C++"
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fread_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee los datos de una secuencia.  Esta versión de [fread](../../c-runtime-library/reference/fread.md) tiene mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
size_t fread_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `bufferSize`  
 Tamaño del búfer de destino en bytes.  
  
 `elementSize`  
 Tamaño del elemento para leer en bytes.  
  
 `count`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fread_s` devuelve el número de elementos \(integer\) que se han leído en el búfer, que puede ser menor que `count` si un error de lectura o el final del archivo se encuentra antes de alcanzar `count` .  Utilice la función de `feof` o de `ferror` para distinguir un error de una condición de fin de archivo.  Si `size` o `count` es 0, `fread_s` devuelve 0 y el contenido del búfer no se modifican.  Si `stream` o `buffer` es un puntero NULL, `fread_s` invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, conjuntos `errno` de esta función a `EINVAL` y devuelven 0.  
  
 Para obtener más información sobre los códigos de error, vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `fread_s` lee hasta `count` elementos de bytes de `elementSize` de entrada `stream` y los almacena en `buffer`.  El puntero de archivo asociada a `stream` \(si hay alguno\) es aumentado por el número de bytes leídos realmente.  Si la secuencia especificada se abre en modo de texto, los pares de retorno\- avance de línea de carro se reemplazan por los únicos caracteres de avance de línea.  El reemplazo no tiene ningún efecto en el puntero de archivo o el valor devuelto.  La posición del archivo \(el archivo puntero es indeterminado si se produce un error.  El valor de un elemento de lectura no se puede determinar parcialmente.  
  
 Esta función bloquea out otros subprocesos.  Si necesita una versión de modificación limitada de interpretación, utilice `_fread_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fread_s`|\<stdio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```cpp  
  
// crt_fread_s.c  
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c  
//  
// This program opens a file that's named FREAD.OUT and  
// writes characters to the file. It then tries to open  
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
#define BUFFERSIZE 30  
#define DATASIZE 22  
#define ELEMENTCOUNT 2  
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)  
#define FILENAME "FREAD.OUT"  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   for ( i = 0; i < DATASIZE; i++ )  
      list[i] = (char)('z' - i);  
   list[DATASIZE] = '\0'; // terminal null so we can print it  
  
   // Open file in text mode:  
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )  
   {  
      // Write DATASIZE characters to stream   
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );  
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );  
      printf( "Wrote %d items\n\n", numwritten );  
      fclose( stream );  
   } else {  
      printf( "Problem opening the file\n" );  
      return -1;  
   }  
  
   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {  
      // Attempt to read in characters in 2 blocks of 11  
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );  
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );  
      printf( "Contents of buffer after write/read:\n\t%s\n", list );  
      fclose( stream );  
   } else {  
      printf( "File could not be opened\n" );  
      return -1;  
   }  
}  
```  
  
  **Contenido del búfer antes de escritura o lectura:**   
 **zyxwvutsrqponmlkjihgfe**  
 **Escribió 22 elementos**   
 **El número de 11 elementos de bytes lee \= 2**   
 **Contenido del búfer cuando la escritura o lectura:**   
 **zyxwvutsrqponmlkjihgfe**    
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)