---
title: "rand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rand"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "rand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generación de números pseudoaleatorios"
  - "números, generación de pseudoaleatorios"
  - "números, pseudoaleatorios"
  - "números pseudoaleatorios"
  - "rand (función)"
  - "números aleatorios, generar"
ms.assetid: 75d9df25-7aaf-4a88-b940-2775559634e8
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# rand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera un número pseudoaleatorio.  Una versión más segura de esta función está disponible, vea [rand\_s](../../c-runtime-library/reference/rand-s.md).  
  
## Sintaxis  
  
```  
int rand( void );  
```  
  
## Valor devuelto  
 `rand` devuelve un número pseudoaleatorio, como se ha descrito anteriormente.  No se devuelve ningún error.  
  
## Comentarios  
 La función de `rand` devuelve un entero pseudoaleatorio en el intervalo de 0 a `RAND_MAX` \(32767\).  Utilice la función de [srand](../../c-runtime-library/reference/srand.md) como origen para el generador de pseudoaleatorio\- número antes de llamar a `rand`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`rand`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_rand.c  
// This program seeds the random-number generator  
// with the time, then exercises the rand function.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <time.h>  
  
void SimpleRandDemo( int n )  
{  
   // Print n random numbers.  
   int i;  
   for( i = 0; i < n; i++ )  
      printf( "  %6d\n", rand() );  
}  
  
void RangedRandDemo( int range_min, int range_max, int n )  
{  
   // Generate random numbers in the half-closed interval  
   // [range_min, range_max). In other words,  
   // range_min <= random number < range_max  
   int i;  
   for ( i = 0; i < n; i++ )  
   {  
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)  
            + range_min;  
      printf( "  %6d\n", u);  
   }  
}  
  
int main( void )  
{  
   // Seed the random-number generator with the current time so that  
   // the numbers will be different every time we run.  
   srand( (unsigned)time( NULL ) );  
  
   SimpleRandDemo( 10 );  
   printf("\n");  
   RangedRandDemo( -100, 100, 10 );  
}  
```  
  
  **22036**  
 **18330**  
 **11651**  
 **27464**  
 **18093**  
 **3284**  
 **11785**  
 **14686**  
 **11447**  
 **11285**  
 **74**  
 **48**  
 **27**  
 **65**  
 **96**  
 **64**  
 **\-5**  
 **\-42**  
 **\-55**  
 **66**   
## Equivalente en .NET Framework  
 [System::Random Class](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [srand](../../c-runtime-library/reference/srand.md)   
 [rand\_s](../../c-runtime-library/reference/rand-s.md)