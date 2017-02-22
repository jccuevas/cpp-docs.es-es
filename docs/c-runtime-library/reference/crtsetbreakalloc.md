---
title: "_CrtSetBreakAlloc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetBreakAlloc"
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
  - "CrtSetBreakAlloc"
  - "_CrtSetBreakAlloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetBreakAlloc (función)"
  - "CrtSetBreakAlloc (función)"
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtSetBreakAlloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece un punto de interrupción en un número de orden de asignación de objetos especificado \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
  
long _CrtSetBreakAlloc(     long lBreakAlloc  );  
```  
  
#### Parámetros  
 *lBreakAlloc*  
 Número de orden de asignación para el que se va a establecer el punto de interrupción.  
  
## Valor devuelto  
 Devuelve el número de orden de asignación de objetos anterior que tenía establecido un punto de interrupción.  
  
## Comentarios  
 `_CrtSetBreakAlloc` permite que una aplicación lleve a cabo la detección de pérdidas de memoria, mediante la interrupción en un punto concreto de la asignación de memoria y la trazabilidad del origen de la solicitud.  La función usa el número de orden de la asignación de objetos secuencial asignado al bloque de memoria cuando se asignó en el montón.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetBreakAlloc` se quitan durante el preprocesamiento.  
  
 El número de orden de la asignación de objetos se almacena en el campo *lRequest* de la estructura de **\_CrtMemBlockHeader**, definido en Crtdbg.h.  Cuando alguna de las funciones de volcado de depuración proporciona información sobre un bloque de memoria, este número aparece encerrado entre llaves, por ejemplo {36}.  
  
 Para más información sobre el uso de `_CrtSetBreakAlloc` con otras funciones de administración de memoria, vea [Seguir las solicitudes de asignación en el montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Track_Heap_Allocation_Requests).  Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtSetBreakAlloc`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_setbrkal.c  
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug  
  
/*  
 * In this program, a call is made to the _CrtSetBreakAlloc routine  
 * to verify that the debugger halts program execution when it reaches  
 * a specified allocation number.  
 */  
  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( )  
{  
        long allocReqNum;  
        char *my_pointer;  
  
        /*   
         * Allocate "my_pointer" for the first  
         * time and ensure that it gets allocated correctly  
         */  
        my_pointer = malloc(10);  
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);  
  
        /*   
         * Set a breakpoint on the allocation request  
         * number for "my_pointer"  
         */  
        _CrtSetBreakAlloc(allocReqNum+2);  
  
        /*   
         * Alternate freeing and reallocating "my_pointer"  
         * to verify that the debugger halts program execution  
         * when it reaches the allocation request  
         */  
        free(my_pointer);  
        my_pointer = malloc(10);  
        free(my_pointer);  
        my_pointer = malloc(10);  
        free(my_pointer);  
}  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)