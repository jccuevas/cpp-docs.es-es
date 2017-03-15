---
title: "_onexit, _onexit_m | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_onexit"
  - "_onexit_m"
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
apitype: "DLLExport"
f1_keywords: 
  - "_onexit"
  - "onexit_m"
  - "onexit"
  - "_onexit_m"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "onexit (función)"
  - "registro, registrar rutinas de salida"
  - "_onexit_m (función)"
  - "onexit_m (función)"
  - "_onexit (función)"
  - "registrar rutinas de salida"
  - "registrar para llamar al salir"
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _onexit, _onexit_m
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Registra una rutina que se llama en el tiempo de salida.  
  
## Sintaxis  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### Parámetros  
 `function`  
 Puntero a una función que se llama en la salida.  
  
## Valor devuelto  
 `_onexit` devuelve un puntero a la función si correctamente o a `NULL` si no hay espacio para almacenar el puntero a función.  
  
## Comentarios  
 La función de `_onexit` se pasa la dirección de una función \(`function`\) que se llamará cuando el programa termina normalmente.  Las llamadas sucesivas a `_onexit` crean un registro de las funciones que se ejecutan en tipo LIFO \(último en entrar, primero en salir\) orden.  Las funciones pasadas a `_onexit` no pueden tomar parámetros.  
  
 En caso `_onexit` se denomina dentro de un archivo DLL, rutinas registradas con el rendimiento de `_onexit` en un archivo DLL que descarga después de que `DllMain` se denomina con DLL\_PROCESS\_DETACH.  
  
 `_onexit` es una extensión de Microsoft.  Para la portabilidad de ANSI, utilice [atexit](../../c-runtime-library/reference/atexit.md).  La versión de `_onexit_m` de la función se usa en modo mixto.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_onexit`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_onexit.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
/* Prototypes */  
int fn1(void), fn2(void), fn3(void), fn4 (void);  
  
int main( void )  
{  
   _onexit( fn1 );  
   _onexit( fn2 );  
   _onexit( fn3 );  
   _onexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
int fn1()  
{  
   printf( "next.\n" );  
   return 0;  
}  
  
int fn2()  
{  
   printf( "executed " );  
   return 0;  
}  
  
int fn3()  
{  
   printf( "is " );  
   return 0;  
}  
  
int fn4()  
{  
   printf( "This " );  
   return 0;  
}  
```  
  
## Resultados  
  
```  
This is executed first.  
This is executed next.  
```  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_\_dllonexit](../../c-runtime-library/dllonexit.md)