---
title: "rewind | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rewind"
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
  - "rewind"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "punteros a archivos [C++]"
  - "punteros a archivos [C++], cambiar de posición"
  - "cambiar de posición punteros a archivos"
  - "rewind (función)"
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rewind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Coloca el puntero de archivo en el principio de un archivo.  
  
## Sintaxis  
  
```  
  
      void rewind(  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura **FILE**.  
  
## Comentarios  
 La función de **rewind** coloca el puntero de archivo de nuevo asociado a `stream` al principio del archivo.  Una llamada a **rewind** es similar a  
  
 **\(void\) fseek\(** `stream`**,0L,** `SEEK_SET`\);  
  
 Sin embargo, a diferencia de `fseek`, **rewind** borra los indicadores de error para la secuencia junto con la marca de fin de archivo.  Además, a diferencia de `fseek`, **rewind** no devuelve un valor para indicar si el puntero se ha movido correctamente.  
  
 Para borrar el búfer de teclado, utilice **rewind** con la secuencia `stdin`, que se asocia el teclado de forma predeterminada.  
  
 Si la secuencia es un puntero de `NULL` , se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función devuelve y `errno` se establece en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**rebobinado**|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_rewind.c  
/* This program first opens a file named  
 * crt_rewind.out for input and output and writes two  
 * integers to the file. Next, it uses rewind to  
 * reposition the file pointer to the beginning of  
 * the file and reads the data back in.  
 */  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int data1, data2;  
  
   data1 = 1;  
   data2 = -37;  
  
   fopen_s( &stream, "crt_rewind.out", "w+" );  
   if( stream != NULL )  
   {  
      fprintf( stream, "%d %d", data1, data2 );  
      printf( "The values written are: %d and %d\n", data1, data2 );  
      rewind( stream );  
      fscanf_s( stream, "%d %d", &data1, &data2 );  
      printf( "The values read are: %d and %d\n", data1, data2 );  
      fclose( stream );  
   }  
}  
```  
  
## Resultados  
  
```  
The values written are: 1 and -37  
The values read are: 1 and -37  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)