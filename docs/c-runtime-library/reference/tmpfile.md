---
title: "tmpfile | Microsoft Docs"
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
  - "tmpfile"
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
  - "tmpfile"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "archivos temporales"
  - "tmpfile (función)"
  - "archivos temporales, crear"
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpfile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un archivo temporal.  Se deja de utilizar esta función porque una versión más segura está disponible; vea [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md).  
  
## Sintaxis  
  
```  
FILE *tmpfile( void );  
```  
  
## Valor devuelto  
 Si es correcto, `tmpfile` devuelve un puntero de secuencia.  De lo contrario, devuelve un puntero de `NULL` .  
  
## Comentarios  
 La función de `tmpfile` crea un archivo temporal y devuelve un puntero a esa secuencia.  El archivo temporal se crea en el directorio raíz.  Para crear un archivo temporal en un directorio distinto de la raíz, utilice [tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) o [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Si no se puede abrir el archivo, `tmpfile` devuelve un puntero de `NULL` .  Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa termina normalmente, o cuando `_rmtmp` se denomina, suponiendo que el directorio de trabajo actual no cambia.  El archivo temporal se abre en el modo de `w+b` \(escritura binaria\).  
  
 El error puede producirse si intenta más que TMP\_MAX \(vea STDIO.H\) las llamadas con `tmpfile`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`tmpfile`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
> [!NOTE]
>  Este ejemplo requiere que se ejecuten privilegios administrativos en Windows Vista.  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
  **El archivo temporal 1 se creó**  
**El archivo temporal 2 se creó**  
**El archivo temporal 3 se creó**  
**3 archivos temporales eliminados**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)