---
title: "fputs, fputws | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fputs"
  - "fputws"
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
  - "fputs"
  - "fputws"
  - "_fputts"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fputts (función)"
  - "fputs (función)"
  - "fputts (función)"
  - "fputws (función)"
  - "secuencias, escribir cadenas en"
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# fputs, fputws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe una cadena en un flujo.  
  
## Sintaxis  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `str`  
 Cadena de salida  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un valor no negativo si se ejecuta correctamente.  Si se produce un error, `fputs` y `fputws` devuelven `EOF`.  Si `str` o `stream` es un puntero nulo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL`; a continuación, `fputs` devuelve `EOF` y `fputws` devuelve `WEOF`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 Cada una de estas funciones copia `str` en la `stream` de salida en la posición actual.  `fputws` copia el argumento `str` de caracteres anchos en `stream` como una cadena de caracteres multibyte o una cadena de caracteres en función de que `stream` se haya abierto en modo de texto o modo binario, respectivamente.  Ninguna de las funciones copia el carácter de terminación NULL.  
  
 Las dos funciones se comportan igual si el flujo se abre en modo ANSI.  `fputs` no admite actualmente la salida a un flujo UNICODE.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fputs`|\<stdio.h\>|  
|`fputws`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
  **Hello world from fputs.**   
## Equivalente en .NET Framework  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fgets, fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [gets, \_getws](../../c-runtime-library/gets-getws.md)   
 [puts, \_putws](../../c-runtime-library/reference/puts-putws.md)