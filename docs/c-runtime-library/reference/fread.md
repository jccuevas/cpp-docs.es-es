---
title: "fread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fread"
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
  - "fread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [C++], leer en secuencia de entrada"
  - "fread (función)"
  - "leer datos [C++], en secuencias de entrada"
  - "secuencias [C++], leer datos de"
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# fread
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee los datos de una secuencia.  
  
## Sintaxis  
  
```  
size_t fread(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `size`  
 Tamaño del elemento en bytes.  
  
 `count`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fread` devuelve el número de elementos completos lee realmente, que pueden ser menor que `count` si se produce un error o si el final del archivo se encuentra antes de `count`que consiga*.* Utilice la función de `feof` o de `ferror` para distinguir un error de una condición de fin de archivo.  Si `size` o `count` es 0, `fread` devuelve 0 y el contenido del búfer no se modifican.  Si `stream` o `buffer` es un puntero NULL, `fread` invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, conjuntos `errno` de esta función a `EINVAL` y devuelven 0.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 La función de `fread` lee hasta `count` elementos de bytes de `size` de entrada `stream` y los almacena en *`buffer`.* El puntero de archivo asociado a `stream` \(si hay alguno\) es aumentado por el número de bytes leídos realmente.  Si la secuencia especificada se abre en modo de texto, los pares de retorno\- avance de línea de carro se reemplazan por los únicos caracteres de avance de línea.  El reemplazo no tiene ningún efecto en el puntero de archivo o el valor devuelto.  La posición del archivo \(el archivo puntero es indeterminado si se produce un error.  El valor de un elemento de lectura no se puede determinar parcialmente.  
  
 Esta función bloquea out otros subprocesos.  Si necesita una versión de modificación limitada de interpretación, utilice `_fread_nolock`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fread`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fread.c  
// This program opens a file named FREAD.OUT and  
// writes 25 characters to the file. It then tries to open  
// FREAD.OUT and read in 25 characters. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   // Open file in text mode:  
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )  
   {  
      for ( i = 0; i < 25; i++ )  
         list[i] = (char)('z' - i);  
      // Write 25 characters to stream   
      numwritten = fwrite( list, sizeof( char ), 25, stream );  
      printf( "Wrote %d items\n", numwritten );  
      fclose( stream );  
  
   }  
   else  
      printf( "Problem opening the file\n" );  
  
   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )  
   {  
      // Attempt to read in 25 characters   
      numread = fread( list, sizeof( char ), 25, stream );  
      printf( "Number of items read = %d\n", numread );  
      printf( "Contents of buffer = %.25s\n", list );  
      fclose( stream );  
   }  
   else  
      printf( "File could not be opened\n" );  
}  
```  
  
  **Escribió 25 elementos**  
**Número de elementos leídos \= 25**  
**Contenido del búfer \= de zyxwvutsrqponmlkjihgfedcb**   
## Equivalente en .NET Framework  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)