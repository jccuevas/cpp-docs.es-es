---
title: "fgetc, fgetwc | Microsoft Docs"
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
  - "fgetwc"
  - "fgetc"
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
  - "_fgettc"
  - "fgetwc"
  - "fgetc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgettc (función)"
  - "caracteres, leer"
  - "fgetc (función)"
  - "fgettc (función)"
  - "fgetwc (función)"
  - "leer caracteres de secuencias"
  - "secuencias, leer caracteres de"
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgetc, fgetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee un carácter de una secuencia.  
  
## Sintaxis  
  
```  
int fgetc(   
   FILE *stream   
);  
wint_t fgetwc(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 `fgetc` devuelve el carácter leído como `int` o devuelve `EOF` para indicar un error o un final de archivo.  `fgetwc` devuelve, como [wint\_t](../../c-runtime-library/standard-types.md), el carácter ancho correspondiente al carácter lee o devuelve `WEOF` para indicar un error o un final de archivo.  En el caso de las dos funciones, use `feof` o `ferror` diferenciar un error de una condición de fin de archivo.  Si un error de lectura, aparece el mensaje de error para la secuencia se establece.  Si `stream` es `NULL`, `fgetc` y `fgetwc` se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EOF`.  
  
## Comentarios  
 Cada una de estas funciones lecturas que un carácter individual de la posición actual del archivo asociado a `stream`.  A continuación, la función aumenta el puntero de archivo asociado \(si está definido\) para señalar al carácter siguiente.  Si el flujo está al final del archivo, se establece la marca de fin de archivo para el flujo.  
  
 `fgetc` es equivalente a `getc`, pero se implementa solo como función, en lugar de como una función y macros.  
  
 `fgetwc` constituye la versión con caracteres anchos de `fgetc`; lee `c` como un carácter multibyte o carácter ancho como si `stream` está abierta en modo de texto o modo binario.  
  
 Las versiones con el sufijo `_nolock` son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos.  
  
 Para obtener más información sobre los caracteres anchos de procesamiento y los caracteres multibyte en modos de texto y el binario, vea [E\/S de la secuencia de Unicode en modos de texto y binario](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fgettc`|`fgetc`|`fgetc`|`fgetwc`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fgetc`|\<stdio.h\>|  
|`fgetwc`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fgetc.c  
// This program uses getc to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   char buffer[81];  
   int  i, ch;  
  
   // Open file to read line from:  
   fopen_s( &stream, "crt_fgetc.txt", "r" );  
   if( stream == NULL )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":   
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = fgetc( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## Entrada: crt\_fgetc.txt  
  
```  
Line one.  
Line two.  
```  
  
### Resultados  
  
```  
Line one.  
Line two.  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fputc, fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)