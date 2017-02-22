---
title: "cwait | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cwait"
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
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "cwait"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cwait (función)"
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _cwait
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Espera hasta que finaliza otro proceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
intptr_t _cwait(     int *termstat,    intptr_t procHandle,    int action  );  
```  
  
#### Parámetros  
 `termstat`  
 Puntero a un búfer en el que se almacenará el código de resultado del proceso especificado, o NULL.  
  
 `procHandle`  
 Identificador del proceso al que se va a esperar \(es decir, el proceso que tiene que finalizar antes de que `_cwait` pueda devolver un valor\).  
  
 `action`  
 NULL: las aplicaciones el sistema operativo Windows lo omiten; en el caso de otras aplicaciones: código de acción que se va a realizar en `procHandle`.  
  
## Valor devuelto  
 Cuando el proceso especificado finaliza correctamente, devuelve el identificador del proceso especificado y establece `termstat` en el código de resultado devuelto por el proceso especificado.  De lo contrario, devuelve –1 y establece `errno` como se indica a continuación.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`ECHILD`|No existe ningún proceso especificado, `procHandle` no es válido o la llamada a la API [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) o [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) ha producido un error.|  
|`EINVAL`|`action` no es válido.|  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_cwait` espera a que finalice el proceso de identificación de proceso proporcionado por `procHandle` para el proceso especificado.  El valor de `procHandle` que se pasa a `_cwait` debe ser el valor devuelto por la llamada a la función [\_spawn](../../c-runtime-library/spawn-wspawn-functions.md) que creó el proceso especificado.  Si el identificador de proceso finaliza antes de que se llame a `_cwait`, `_cwait` devuelve un valor inmediatamente.  `_cwait` se puede usar en cualquier proceso para esperar a cualquier otro proceso conocido para el que existe un identificador válido \(`procHandle`\).  
  
 `termstat` señala a un búfer en el que se almacenará el código devuelto del proceso especificado.  El valor de `termstat` indica si el proceso especificado terminó con normalidad mediante una llamada a la API de Windows [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx).  Se llama internamente a `ExitProcess` si el proceso especificado llama a `exit` o `_exit`, vuelve desde `main` o llega al final de `main`.  Para más información sobre el valor que se devuelve a través de `termstat`, vea [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx).  Si se llama a `_cwait` con un valor NULL para `termstat`, el código de retorno del proceso especificado no se almacena.  
  
 El sistema operativo Windows omite el parámetro `action`, porque en estos entornos no están implementadas las relaciones elemento primario\-elemento secundario.  
  
 A menos que `procHandle` sea \-1 o \-2 \(identificadores del proceso o subproceso actual\), el identificador se cierra.  Por consiguiente, en esta situación, no se debe usar el identificador devuelto.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_cwait`|\<process.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_cwait.c  
// compile with: /c  
// This program launches several processes and waits  
// for a specified process to finish.  
//  
#define _CRT_RAND_S  
  
#include <windows.h>  
#include <process.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <time.h>  
  
// Macro to get a random integer within a specified range  
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))  
  
struct PROCESS  
{  
   int     nPid;  
   char    name[40];  
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };  
  
int main( int argc, char *argv[] )  
{  
   int termstat, c;  
   unsigned int number;  
  
   srand( (unsigned)time( NULL ) );    // Seed randomizer  
  
   // If no arguments, this is the calling process  
   if( argc == 1 )  
   {  
      // Spawn processes in numeric order  
      for( c = 0; c < 4; c++ ){  
         _flushall();  
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],   
                             process[c].name, NULL );  
      }  
  
      // Wait for randomly specified process, and respond when done   
      c = getrandom( 0, 3 );  
      printf( "Come here, %s.\n", process[c].name );  
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );  
      printf( "Thank you, %s.\n", process[c].name );  
  
   }  
   // If there are arguments, this must be a spawned process   
   else  
   {  
      // Delay for a period that's determined by process number  
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );  
      printf( "Hi, Dad. It's %s.\n", argv[1] );  
   }  
}  
```  
  
  **Hi, Dad.  It's Ann.  Come here, Ann.  Thank you, Ann.  Hi, Dad.  It's Beth.  Hi, Dad.  It's Carl.  Hi, Dad.  It's Dave.**    
## Equivalente en .NET Framework  
 [System::Diagnostics::Process::WaitForExit](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.waitforexit.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)