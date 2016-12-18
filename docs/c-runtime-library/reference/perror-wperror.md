---
title: "perror, _wperror | Microsoft Docs"
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
  - "_wperror"
  - "perror"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wperror"
  - "_tperror"
  - "perror"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tperror (función)"
  - "_wperror (función)"
  - "mensajes de error, imprimir"
  - "perror (función)"
  - "imprimir mensajes de error"
  - "tperror (función)"
  - "wperror (función)"
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# perror, _wperror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Imprime un mensaje de error.  
  
## Sintaxis  
  
```  
  
      void perror(  
   const char *string   
);  
void _wperror(  
   const wchar_t *string   
);  
```  
  
#### Parámetros  
 `string`  
 Mensaje de cadena para imprimir.  
  
## Comentarios  
 La función de `perror` imprime un mensaje de error a `stderr`.  `_wperror` es una versión con caracteres anchos de **\_perror**; el argumento de `string` a `_wperror` es una cadena de caracteres.  `_wperror` y **\_perror** se comportan exactamente igual de otra manera.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tperror`|`perror`|`perror`|`_wperror`|  
  
 `string` es impreso primero, seguido de dos puntos, después por el mensaje de error del sistema para la última llamada de biblioteca que generó el error y, finalmente por un carácter de nueva línea.  Si `string` es un puntero NULL o un puntero a una cadena nula, `perror` imprime únicamente el mensaje de error del sistema.  
  
 El número de error se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) \(definido en ERRNO.H\).  Se obtiene acceso a los mensajes de error del sistema a través de la variable [\_sys\_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error.  `perror` imprime el mensaje de error adecuado mediante el valor de `errno` como índice a `_sys_errlist`.  El valor de la variable [\_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz `_sys_errlist`.  
  
 Para los resultados precisos, la llamada `perror` inmediatamente después de una rutina de biblioteca vuelve con un error.  Si no, las llamadas subsiguientes pueden sobrescribir el valor de `errno` .  
  
 En el sistema operativo Windows, algunos valores de `errno` enumerados en ERRNO.H son no usados.  Estos valores se reservan para uso del sistema operativo UNIX.  Vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para una lista de valores de `errno` utilizados por el sistema operativo Windows.  `perror` imprime una cadena vacía para cualquier valor de `errno` no utilizado por estas plataformas.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`perror`|\<stdio.h o\> stdlib.h \<\>|  
|`_wperror`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_perror.c  
// compile with: /W3  
/* This program attempts to open a file named  
 * NOSUCHF.ILE. Because this file probably doesn't exist,  
 * an error message is displayed. The same message is  
 * created using perror, strerror, and _strerror.  
 */  
  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh;  
  
   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )  
   {  
      /* Three ways to create error message: */  
      perror( "perror says open failed" );  
      printf( "strerror says open failed: %s\n",  
         strerror( errno ) ); // C4996  
      printf( _strerror( "_strerror says open failed" ) ); // C4996  
      // Note: strerror and _strerror are deprecated; consider  
      // using strerror_s and _strerror_s instead.  
   }  
   else  
   {  
      printf( "open succeeded on input file\n" );  
      _close( fh );  
   }  
}  
```  
  
## Resultados  
  
```  
perror says open failed: No such file or directory  
strerror says open failed: No such file or directory  
_strerror says open failed: No such file or directory  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [strerror, \_strerror, \_wcserror, \_\_wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)