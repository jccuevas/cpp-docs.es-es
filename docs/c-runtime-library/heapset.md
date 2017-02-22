---
title: "_heapset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapset"
apilocation: 
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_heapset"
  - "heapset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_heapset (función)"
  - "comprobar montón"
  - "depurar [CRT], problemas relacionados con los montones"
  - "montones, comprobar"
  - "heapset (función)"
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _heapset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba que los montones mantienen una coherencia mínima y establece las entradas libres a un valor especificado.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
int _heapset(   
   unsigned int fill   
);  
```  
  
#### Parámetros  
 `fill`  
 Carácter de relleno.  
  
## Valor devuelto  
 `_heapset` devuelve una de las siguientes constantes de manifiesto enteras, definidas en Malloc.h.  
  
 `_HEAPBADBEGIN`  
 La información de encabezado inicial no es válida o no se encuentra.  
  
 `_HEAPBADNODE`  
 Se ha encontrado un montón dañado o un nodo incorrecto.  
  
 `_HEAPEMPTY`  
 El montón no está inicializado.  
  
 `_HEAPOK`  
 El montón parece ser coherente.  
  
 Además, si se produce un error, `_heapset` establece `errno` en `ENOSYS`.  
  
## Comentarios  
 La función `_heapset` muestra las ubicaciones de memoria libre o los nodos que se han sobrescrito accidentalmente.  
  
 `_heapset` comprueba la coherencia mínima en el montón y, después, establece cada byte de las entradas libres del montón al valor `fill`. Este valor conocido muestra las ubicaciones de memoria del montón que contienen nodos libres y las que contienen datos que se escribieron involuntariamente en la memoria liberada. Si el sistema operativo no admite `_heapset`\(por ejemplo Windows 98\), la función devuelve `_HEAPOK` y establece `errno` en `ENOSYS`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_heapset`|\<malloc.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_heapset.c // This program checks the heap and // fills in free entries with the character 'Z'. #include <malloc.h> #include <stdio.h> #include <stdlib.h> int main( void ) { int heapstatus; char *buffer; if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is exit( 0 );                        //    initialized heapstatus = _heapset( 'Z' );        // Fill in free entries switch( heapstatus ) { case _HEAPOK: printf( "OK - heap is fine\n" ); break; case _HEAPEMPTY: printf( "OK - heap is empty\n" ); break; case _HEAPBADBEGIN: printf( "ERROR - bad start of heap\n" ); break; case _HEAPBADNODE: printf( "ERROR - bad node in heap\n" ); break; } free( buffer ); }  
```  
  
```Output  
OK - heap is fine  
```  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../c-runtime-library/memory-allocation.md)   
 [\_heapadd](../c-runtime-library/heapadd.md)   
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../c-runtime-library/reference/heapmin.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)