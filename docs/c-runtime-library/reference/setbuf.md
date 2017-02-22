---
title: "setbuf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setbuf"
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
  - "setbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "setbuf (función)"
  - "Almacenamiento en búfer de secuencia"
ms.assetid: 13beda22-7b56-455d-8a6c-f2eb636885b9
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# setbuf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Almacenamiento en búfer de la secuencia de Controles.  Se deja de utilizar esta función; uso [setvbuf](../../c-runtime-library/reference/setvbuf.md) en su lugar.  
  
## Sintaxis  
  
```  
void setbuf(  
   FILE *stream,  
   char *buffer   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `buffer`  
 Búfer Usuario\- asignado.  
  
## Comentarios  
 La función de `setbuf` controla el almacenamiento en búfer para `stream`.  El argumento de `stream` debe hacer referencia a un archivo abierto que no se ha leído ni se ha escrito.  Si el argumento de `buffer` es `NULL`, la secuencia se inseparada.  Si no, el búfer debe señalar a una matriz de caracteres de longitud `BUFSIZ`, donde el tamaño de búfer `BUFSIZ` definido en STDIO.H.  El búfer definido por el usuario, en lugar del búfer sistema\- asignado predeterminado para la secuencia especificada, se utiliza para el búfer de E\/S.  La secuencia de `stderr` está inseparada de forma predeterminada, pero puede utilizar `setbuf` para asignar búferes a `stderr`.  
  
 `setbuf` se ha reemplazado por [setvbuf](../../c-runtime-library/reference/setvbuf.md), que es la rutina preferida para el nuevo código.  `setbuf` se conserva a efectos de compatibilidad con código existente.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`setbuf`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_setbuf.c  
// compile with: /W3  
// This program first opens files named DATA1 and  
// DATA2. Then it uses setbuf to give DATA1 a user-assigned  
// buffer and to change DATA2 so that it has no buffer.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[BUFSIZ];  
   FILE *stream1, *stream2;  
  
   fopen_s( &stream1, "data1", "a" );  
   fopen_s( &stream2, "data2", "w" );  
  
   if( (stream1 != NULL) && (stream2 != NULL) )  
   {  
      // "stream1" uses user-assigned buffer:  
      setbuf( stream1, buf ); // C4996  
      // Note: setbuf is deprecated; consider using setvbuf instead  
      printf( "stream1 set to user-defined buffer at: %Fp\n", buf );  
  
      // "stream2" is unbuffered  
      setbuf( stream2, NULL ); // C4996  
      printf( "stream2 buffering disabled\n" );  
      _fcloseall();  
   }  
}  
```  
  
  **stream1 establecido en el búfer definido por el usuario en: 0012FCDC**  
**almacenamiento en búfer stream2 deshabilitado**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, \_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)