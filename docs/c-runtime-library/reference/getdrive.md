---
title: "_getdrive | Microsoft Docs"
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
  - "_getdrive"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getdrive"
  - "getdrive"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getdrive (función)"
  - "unidad de disco duro actual"
  - "unidades de disco"
  - "getdrive (función)"
ms.assetid: e40631a0-8f1a-4897-90ac-e1037ff30bca
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdrive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la unidad de disco actual.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _getdrive( void );  
```  
  
## Valor devuelto  
 Devuelve la unidad \(predeterminada\) actual \(1\=A, 2\=B, etc.\).  No se devuelve ningún error.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getdrive`|\<direct.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_getdrive.c  
// compile with: /c  
// Illustrates drive functions including:  
//    _getdrive       _chdrive        _getdcwd  
//  
  
#include <stdio.h>  
#include <direct.h>  
#include <stdlib.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch, drive, curdrive;  
   static char path[_MAX_PATH];  
  
   // Save current drive.  
   curdrive = _getdrive();  
  
   printf( "Available drives are:\n" );  
  
   // If we can switch to the drive, it exists.  
   for( drive = 1; drive <= 26; drive++ )  
   {  
      if( !_chdrive( drive ) )  
      {  
         printf( "%c:", drive + 'A' - 1 );  
         if( _getdcwd( drive, path, _MAX_PATH ) != NULL )  
            printf( " (Current directory is %s)", path );  
         putchar( '\n' );  
      }  
   }  
  
   // Restore original drive.  
   _chdrive( curdrive );  
}  
```  
  
  **Las unidades disponibles son:**  
**A: \(el directorio actual es A:\\\)**  
**C: \(el directorio actual es C:\\\)**  
**E: \(el directorio actual es E:\\testdir\\bin\)**  
**F: \(el directorio actual es F:\\\)**  
**G: \(el directorio actual es G:\\\)**   
## Equivalente en .NET Framework  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## Vea también  
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [\_chdrive](../../c-runtime-library/reference/chdrive.md)   
 [\_getcwd, \_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdcwd, \_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)