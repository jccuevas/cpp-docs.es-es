---
title: "_set_new_handler | Microsoft Docs"
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
  - "_set_new_handler"
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
  - "_set_new_handler"
  - "set_new_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_new_handler (función)"
  - "control de errores"
  - "set_new_handler (función)"
  - "transferir control a controlador de errores"
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transfiere el control al mecanismo de control de errores si el operador `new` no puede asignar memoria.  
  
## Sintaxis  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### Parámetros  
 `pNewHandler`  
 Puntero a memoria aplicación\-proporcionada que administra la función.  Un argumento de 0 hace que el nuevo controlador que se va a quitar.  
  
## Valor devuelto  
 Devuelve un puntero a la función anterior del control de excepciones registrada por `_set_new_handler`, para poder restaurar la función anterior más adelante.  Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; este valor puede ser `NULL`.  
  
## Comentarios  
 La función de C\+\+ `_set_new_handler` especifica una función de control de excepciones que control de mejoras si el operador de `new` no puede para asignar memoria.  Si se produce `new` , el sistema en tiempo de ejecución llama automáticamente a la función excepción\- que administra que se pasa como argumento a `_set_new_handler`.  `_PNH`, definido en New.h, es un puntero a una función que devuelve el tipo `int` y toma un argumento de `size_t`escrito.  Utilice `size_t` para especificar la cantidad de espacio que se asignará.  
  
 No hay ningún controlador predeterminado.  
  
 `_set_new_handler` es esencialmente un esquema de recolección de elementos no utilizados.  El sistema de motor en tiempo de ejecución reintenta la asignación cada vez que la función devuelve un valor distinto de cero y no se supera si la función devuelve 0.  
  
 Una aparición de la función de `_set_new_handler` en registros de un programa que la función excepción\- que estaba controlando especificado en la lista de argumentos con el sistema en tiempo de ejecución:  
  
```  
#include <new.h>  
int handle_program_memory_depletion( size_t )  
{  
   // Your code  
}  
int main( void )  
{  
   _set_new_handler( handle_program_memory_depletion );  
   int *pi = new int[BIG_NUMBER];  
}  
```  
  
 Puede guardar la dirección de función que se pasó por última vez a la función de `_set_new_handler` y reinstalarla posterior:  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 La función de C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) establece el nuevo modo de controlador para [malloc](../../c-runtime-library/reference/malloc.md).  El nuevo modo de controlador indica si, en el error, `malloc` es llamar a la nueva rutina de controlador como lo establece `_set_new_handler`.  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando `malloc` no puede asignar memoria, `malloc` llama a la nueva rutina de controlador de la misma manera que hace el operador `new` cuando produce errores por la misma razón.  Para reemplazar el valor predeterminado, llame a:  
  
```  
_set_new_mode(1)  
```  
  
 al principio del programa o el vínculo con Newmode.obj.  
  
 Si se proporciona `operator new`definido por el usuario, las nuevas funciones controladoras no son error automáticamente invitado.  
  
 Para obtener más información, vea [new](../../cpp/new-operator-cpp.md) y [borrar](../../cpp/delete-operator-cpp.md) en *la referencia del lenguaje C\+\+*.  
  
 Hay solo controlador de `_set_new_handler` para todos los archivos DLL o ejecutables dinámicamente vinculados; incluso si llama a `_set_new_handler` el controlador podría reemplazar por otro o que se está reemplazando un controlador establecido por otra DLL o ejecutable.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_new_handler`|\<new.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 En este ejemplo, cuando se produce un error en la asignación, el control se transfiere a MyNewHandler.  El argumento pasado a MyNewHandler es el número de bytes solicitados.  El valor devuelto de MyNewHandler es una marca que indica si la asignación debe reintentar: un valor distinto de cero indica que la asignación debe reintentar, y un valor cero indica que se ha producido un error en la asignación.  
  
```  
// crt_set_new_handler.cpp  
// compile with: /c  
#include <stdio.h>  
#include <new.h>  
#define BIG_NUMBER 0x1fffffff  
  
int coalesced = 0;  
  
int CoalesceHeap()  
{  
   coalesced = 1;  // Flag RecurseAlloc to stop   
   // do some work to free memory  
   return 0;  
}  
// Define a function to be called if new fails to allocate memory.  
int MyNewHandler( size_t size )  
{  
   printf("Allocation failed. Coalescing heap.\n");  
  
   // Call a function to recover some heap space.  
   return CoalesceHeap();  
}  
  
int RecurseAlloc() {  
   int *pi = new int[BIG_NUMBER];  
   if (!coalesced)  
      RecurseAlloc();  
   return 0;  
}  
  
int main()  
{  
   // Set the failure handler for new to be MyNewHandler.  
   _set_new_handler( MyNewHandler );  
   RecurseAlloc();  
}  
```  
  
  **La asignación no.  Pila de incorporación.**  
**Esta aplicación solicitó la finalización del tiempo de ejecución de modo no habitual.**  
**Póngase en contacto con el equipo de asistencia técnica de la aplicación para obtener más información.**    
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)