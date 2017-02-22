---
title: "tmpfile_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tmpfile_s"
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
  - "tmpfile_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos temporales"
  - "tmpfile_s (función)"
  - "archivos temporales, crear"
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# tmpfile_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un archivo temporal.  Es una versión de [tmpfile](../../c-runtime-library/reference/tmpfile.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### Parámetros  
 \[out\] `pFilePtr`  
 La dirección de un puntero para almacenar la dirección del puntero generado en una secuencia.  
  
## Valor devuelto  
 Devuelve 0 si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### Condiciones de error  
  
|`pFilePtr`|**Valor devuelto**|**Contents of**  `pFilePtr`|  
|----------------|------------------------|---------------------------------|  
|`NULL`|`EINVAL`|no cambia|  
  
 Si el error de validación anterior de parámetro aparece, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y el valor devuelto es `EINVAL`.  
  
## Comentarios  
 La función de `tmpfile_s` crea un archivo temporal y coloca un puntero a esa secuencia en el argumento de `pFilePtr` .  El archivo temporal se crea en el directorio raíz.  Para crear un archivo temporal en un directorio distinto de la raíz, utilice [tmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) o [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) junto con [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Si no se puede abrir el archivo, `tmpfile_s` escribe `NULL` al parámetro de `pFilePtr` .  Este archivo temporal se elimina automáticamente cuando se cierra el archivo, cuando el programa termina normalmente, o cuando `_rmtmp` se denomina, suponiendo que el directorio de trabajo actual no cambia.  El archivo temporal se abre en el modo de `w+b` \(escritura binaria\).  
  
 El error puede producirse si intenta más que `TMP_MAX_S` \(vea STDIO.H\) las llamadas con `tmpfile_s.`  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`tmpfile_s`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
> [!NOTE]
>  Este ejemplo requiere que se ejecuten privilegios administrativos en Windows Vista.  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
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