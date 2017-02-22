---
title: "isatty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isatty"
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
  - "isatty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "isatty (función)"
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _isatty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un descriptor de archivo está asociado a un dispositivo de caracteres.  
  
## Sintaxis  
  
```  
  
      int _isatty(  
int fd   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al dispositivo que se va a probar.  
  
## Valor devuelto  
 `_isatty` devuelve un valor distinto de cero si descriptor está asociado a un dispositivo de caracteres.  De lo contrario, `_isatty` devuelve 0.  
  
## Comentarios  
 La función `_isatty` determina si `fd` está asociado a un dispositivo de caracteres \(un terminal, una consola, una impresora o un puerto serie\).  
  
 Esta función valida el parámetro `fd`.  Si `fd` es un puntero de archivo incorrecto, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve 0 y establece `errno` en `EBADF`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_isatty`|\<io.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_isatty.c  
/* This program checks to see whether  
 * stdout has been redirected to a file.  
 */  
  
#include <stdio.h>  
#include <io.h>  
  
int main( void )  
{  
   if( _isatty( _fileno( stdout ) ) )  
      printf( "stdout has not been redirected to a file\n" );  
   else  
      printf( "stdout has been redirected to a file\n");  
}  
```  
  
## Resultados del ejemplo  
  
```  
stdout has not been redirected to a file  
```  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)