---
title: "_popen, _wpopen | Microsoft Docs"
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
  - "_popen"
  - "_wpopen"
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
  - "tpopen"
  - "popen"
  - "wpopen"
  - "_popen"
  - "_wpopen"
  - "_tpopen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_popen (función)"
  - "_tpopen (función)"
  - "_wpopen (función)"
  - "canalizaciones, crear"
  - "popen (función)"
  - "tpopen (función)"
  - "wpopen (función)"
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _popen, _wpopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea una canalización y ejecuta un comando.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
      FILE *_popen(  
const char *command,  
const char *mode   
);  
FILE *_wpopen(  
const wchar_t *command,  
const wchar_t *mode   
);  
```  
  
#### Parámetros  
 *command*  
 Comando que se va a ejecutar.  
  
 *mode*  
 Modo del flujo devuelto.  
  
## Valor devuelto  
 Devuelve un flujo asociado a un extremo de la canalización creada.  El otro extremo de la canalización se asocia a la entrada o salida estándar del comando generado.  Las funciones devuelven **NULL** si se produce un error.  Si el error es un parámetro no válido, por ejemplo si *command* o *mode* es un puntero nulo, o si *mode* no es un modo válido, `errno` se establece en `EINVAL`.  Vea los modos válidos en la sección de comentarios.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_popen` crea una canalización y ejecuta de forma asincrónica una copia generada del procesador de comandos con el *command* de cadena especificado.  La cadena de caracteres *mode* especifica el tipo de acceso solicitado, como se indica a continuación.  
  
 **"r"**  
 El proceso de llamada puede leer la salida estándar del comando generado mediante el flujo devuelto.  
  
 **"w"**  
 El proceso de llamada puede escribir en la entrada estándar del comando generado mediante el flujo devuelto.  
  
 **"b"**  
 Abrir en modo binario.  
  
 **"t"**  
 Abrir en modo de texto.  
  
> [!NOTE]
>  Si se usa en un programa de Windows, la función `_popen` devuelve un puntero de archivo no válido que hace que el programa deje de responder indefinidamente.  `_popen` funciona correctamente en una aplicación de consola.  Para crear una aplicación de Windows que redirija la entrada y la salida, vea [Crear un proceso secundario con redirección de entrada y salida](http://msdn.microsoft.com/library/windows/desktop/ms682499) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
 `_wpopen` es una versión con caracteres anchos de `_popen`; el argumento *path* para `_wpopen` es una cadena de caracteres anchos.  Por lo demás, `_wpopen` y `_popen` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tpopen`|`_popen`|`_popen`|`_wpopen`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_popen`|\<stdio.h\>|  
|`_wpopen`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_popen.c  
/* This program uses _popen and _pclose to receive a   
 * stream of text from a system process.  
 */  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
  
   char   psBuffer[128];  
   FILE   *pPipe;  
  
        /* Run DIR so that it writes its output to a pipe. Open this  
         * pipe with read text attribute so that we can read it   
         * like a text file.   
         */  
  
   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )  
      exit( 1 );  
  
   /* Read pipe until end of file, or an error occurs. */  
  
   while(fgets(psBuffer, 128, pPipe))  
   {  
      printf(psBuffer);  
   }  
  
   /* Close pipe and print return value of pPipe. */  
   if (feof( pPipe))  
   {  
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );  
   }  
   else  
   {  
     printf( "Error: Failed to read the pipe to the end.\n");  
   }  
}  
```  
  
## Resultados del ejemplo  
 En este resultado se supone que solo hay un archivo en el directorio actual con la extensión de nombre de archivo .c.  
  
```  
 Volume in drive C is CDRIVE  
 Volume Serial Number is 0E17-1702  
  
 Directory of D:\proj\console\test1  
  
07/17/98  07:26p                   780 popen.c  
               1 File(s)            780 bytes  
                             86,597,632 bytes free  
  
Process returned 0  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_pclose](../../c-runtime-library/reference/pclose.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)