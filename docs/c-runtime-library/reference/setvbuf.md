---
title: "setvbuf | Microsoft Docs"
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
  - "setvbuf"
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
  - "setvbuf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "controlar almacenamiento en búfer de secuencia"
  - "setvbuf (función)"
  - "Almacenamiento en búfer de secuencia"
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setvbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Almacenamiento en búfer y el tamaño de búfer de la secuencia de Controles.  
  
## Sintaxis  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `buffer`  
 Búfer Usuario\- asignado.  
  
 `mode`  
 Modo de almacenamiento en búfer.  
  
 `size`  
 Tamaño de búfer en bytes.  El intervalo permitido: 2 \<\= `size` \<\= INT\_MAX \(2147483647\).  Internamente, el valor proporcionado para `size` se redondea hacia abajo al múltiplo más cercano de 2.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0.  
  
 Si `stream` es `NULL`, o si `mode` o `size` no está dentro de un cambio válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función devuelve \-1 y establece `errno` a `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `setvbuf` permite que el programa controle el búfer y el tamaño de búfer para `stream`.  `stream` debe hacer referencia a un archivo abierto que no ha superado una operación de E\/S desde que se abrió.  La matriz indicada por `buffer` se utiliza como el búfer, a menos que sea `NULL`, en este caso `setvbuf` utiliza un búfer automáticamente asignado de longitud `size`\/2 \* 2 bytes.  
  
 El modo debe ser `_IOFBF`, `_IOLBF`, o `_IONBF`.  Si `mode` es `_IOFBF` o `_IOLBF`, después `size` se utiliza como el tamaño del búfer.  Si `mode` es `_IONBF`, la secuencia se inseparada y se omiten `size` y `buffer` .  Los valores para `mode` y sus significados son:  
  
 `_IOFBF`  
 Almacenamiento en búfer completo; es decir, `buffer` se utiliza como el búfer y `size` se utiliza como el tamaño del búfer.  Si `buffer` es `NULL`, bytes automáticamente asignados de `size` de un búfer se utilizan de longitud.  
  
 `_IOLBF`  
 Para algunos sistemas, proporciona el búfer de la línea.  Sin embargo, para Win32, el comportamiento es igual que `_IOFBF` \- búfer completo.  
  
 `_IONBF`  
 No se utiliza ningún búfer, independientemente `buffer` o `size`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`setvbuf`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **“stream1” tiene ahora un búfer de 1024 bytes**  
**“stream2” ahora no tiene ningún búfer**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, \_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)