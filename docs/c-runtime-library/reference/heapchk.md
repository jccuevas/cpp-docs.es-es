---
title: "_heapchk | Microsoft Docs"
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
  - "_heapchk"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_heapchk"
  - "heapchk"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_heapchk (función)"
  - "comprobación de coherencia de montones"
  - "depurar [CRT], problemas relacionados con los montones"
  - "heapchk (función)"
  - "montones, comprobación de coherencia"
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _heapchk
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ejecutar comprobaciones de coherencia en la pila.  
  
## Sintaxis  
  
```  
int _heapchk( void );  
```  
  
## Valor devuelto  
 `_heapchk` devuelve una de las siguientes constantes de manifiesto enteras, definidas en Malloc.h.  
  
 `_HEAPBADBEGIN`  
 La información de encabezado inicial es incorrecta o no se encuentra.  
  
 `_HEAPBADNODE`  
 Se ha encontrado el nodo incorrecta o está dañado la pila.  
  
 `_HEAPBADPTR`  
 El puntero de la pila no es válido.  
  
 `_HEAPEMPTY`  
 Pila no se ha inicializado.  
  
 `_HEAPOK`  
 La pila parece ser coherente.  
  
 Además, si se produce un error, `_heapchk` establece `errno` en `ENOSYS`.  
  
## Comentarios  
 Los problemas pila\- relacionados de depuración de la función de `_heapchk` comprobar si hay coherencia mínima de la pila.  Si el sistema operativo no admite `_heapchk`\(por ejemplo Windows 98\), la función devuelve `_HEAPOK` y establece `errno` en `ENOSYS`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_heapchk`|\<malloc.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_heapchk.c  
// This program checks the heap for  
// consistency and prints an appropriate message.  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  heapstatus;  
   char *buffer;  
  
   // Allocate and deallocate some memory  
   if( (buffer = (char *)malloc( 100 )) != NULL )  
      free( buffer );  
  
   // Check heap status  
   heapstatus = _heapchk();  
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf(" OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf(" OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
}  
```  
  
  **OK \(la pila está bien**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../../c-runtime-library/heapadd.md)   
 [\_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../../c-runtime-library/heapset.md)   
 [\_heapwalk](../../c-runtime-library/reference/heapwalk.md)