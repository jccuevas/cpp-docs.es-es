---
title: "_lock_file | Microsoft Docs"
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
  - "_lock_file"
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
  - "_lock_file"
  - "lock_file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lock_file (función)"
  - "bloqueo de archivos [C++]"
  - "lock_file (función)"
ms.assetid: 75c7e0e6-efff-4747-b6ed-9bcf2b0894c3
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lock_file
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Bloquea un objeto de `FILE` para garantizar la coherencia de los subprocesos que tienen acceso a `FILE` simultáneamente.  
  
## Sintaxis  
  
```  
void _lock_file(  
   FILE* file  
);  
```  
  
#### Parámetros  
 `file`  
 Identificador de archivos.  
  
## Comentarios  
 La función de `_lock_file` bloquea el objeto de `FILE` especificado por `file`.  El archivo subyacente no está bloqueado por `_lock_file`.  Utilice [\_unlock\_file](../../c-runtime-library/reference/unlock-file.md) para liberar el bloqueo en el archivo.  Las llamadas a `_lock_file` y `_unlock_file` se deben coincidir en un subproceso.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lock_file`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_lock_file.c  
// This example creates multiple threads that write to standard output  
// concurrently, first with _file_lock, then without.  
  
#include <stdio.h>  
#include <process.h>// _beginthread  
#include <windows.h>// HANDLE  
  
void Task_locked( void* str )  
{  
    for( int i=0; i<1000; ++i )  
    {  
        _lock_file( stdout );  
        for( char* cp = (char*)str; *cp; ++cp )  
        {  
            _fputc_nolock( *cp, stdout );  
        }  
        _unlock_file( stdout );  
    }  
}  
  
void Task_unlocked( void* str )  
{  
    for( int i=0; i<1000; ++i )  
    {  
        for( char* cp = (char*)str; *cp; ++cp )  
        {  
            fputc( *cp, stdout );  
        }  
    }  
}  
  
int main()  
{  
    HANDLE h[3];  
    h[0] = (HANDLE)_beginthread( &Task_locked, 0, "First\n" );  
    h[1] = (HANDLE)_beginthread( &Task_locked, 0, "Second\n" );  
    h[2] = (HANDLE)_beginthread( &Task_locked, 0, "Third\n" );  
  
    WaitForMultipleObjects( 3, h, true, INFINITE );  
  
    h[0] = (HANDLE)_beginthread( &Task_unlocked, 0, "First\n" );  
    h[1] = (HANDLE)_beginthread( &Task_unlocked, 0, "Second\n" );  
    h[2] = (HANDLE)_beginthread( &Task_unlocked, 0, "Third\n" );  
  
    WaitForMultipleObjects( 3, h, true, INFINITE );  
}  
```  
  
  **...**  
**Primero**  
**Segundo**  
**Primero**  
**Segundo**  
**Tercer**  
**Segundo**  
**Tercer**  
**Segundo**  
**...**  
**FSiercsotn**  
**dF**  
**iSrescto**  
**nFdi**  
**rSsetc**  
**oFnidr**  
**sSte**  
**cFoinrds**  
**tS**  
**eFciornsdt**   
## Equivalente en .NET Framework  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_unlock\_file](../../c-runtime-library/reference/unlock-file.md)