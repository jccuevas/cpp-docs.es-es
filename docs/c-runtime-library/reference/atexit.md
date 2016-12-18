---
title: "atexit | Microsoft Docs"
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
  - "atexit"
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
  - "atexit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "atexit (función)"
  - "procesar, al salir"
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atexit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Procesa la función especificada en la salida.  
  
## Sintaxis  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### Parámetros  
 `func`  
 Función que se va a llamar.  
  
## Valor devuelto  
 `atexit` devuelve 0 si es correcto, o un valor distinto de cero si se produce un error.  
  
## Comentarios  
 La función de `atexit` se pasa la dirección de una función \(`func`\) que se llamará cuando el programa termina normalmente.  Las llamadas sucesivas a `atexit` crean un registro de las funciones pasado\- en las que se ejecutan en, primer \- out orden de \(LIFO\).  Las funciones pasadas a `atexit` no pueden tomar parámetros.  `atexit` y `_onexit` utilizan el montón para contener el registro de funciones.  Así, el número de funciones que pueden ser registradas está limitado por la memoria del montón.  
  
 El código de la función de `atexit` no debe contener ninguna dependencia en ningún DLL que han podido descargar ya cuando se llama a la función de `atexit` .  
  
 Para generar una aplicación de ANSI\- bajo, utilice la función de `atexit` del estándar ANSI \(en lugar de la función similar de `_onexit` \).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`atexit`|\<stdlib.h\>|  
  
## Ejemplo  
 Este programa inserta cuatro funciones en la pila de funciones que se ejecutarán cuando se llama a `atexit` .  Cuando se ejecutan a resultados de programa, estos programas del último en entrar, primero en salir base.  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
  **Esto se ejecuta primero.**  
**Esto se ejecuta después.**   
## Equivalente en .NET Framework  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)